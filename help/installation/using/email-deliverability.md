---
product: campaign
title: 技术电子邮件配置
description: 了解如何配置Campaign以在发送电子邮件时控制实例的输出
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '3023'
ht-degree: 0%

---

# 技术电子邮件配置{#email-deliverability}



## 概述 {#overview}

以下部分概述了在发送电子邮件时控制Adobe Campaign实例输出所需的配置。

>[!NOTE]
>
>某些配置只能通过Adobe由Adobe托管的部署来执行，例如，访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 或 [本页](../../installation/using/capability-matrix.md).

有关与Adobe Campaign的可投放性相关的概念和最佳实践的更多信息，请参阅此 [部分](../../delivery/using/about-deliverability.md).

要更深入地了解什么是投放能力，包括有关Adobe平台有效发送和接收电子邮件的所有技术建议，请参阅 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

## 操作原则 {#operating-principle}

可以控制一个或多个Adobe Campaign实例的输出，以根据域限制发送的电子邮件数量。 例如，您可以将输出限制为每小时20,000个 **yahoo.com** 地址，同时为所有其他域配置每小时10万条消息。

需要针对投放服务器使用的每个IP地址控制消息输出(**mta**)。 几个 **mta** 划分到多台计算机并属于各种Adobe Campaign实例时，可以共享相同的IP地址进行电子邮件投放：需要设置一个流程来协调这些IP地址的使用。

这就是 **stat** 模块会执行以下操作：它会将所有连接请求和消息转发到邮件服务器，以获取一组IP地址。 统计信息服务器会跟踪投放，并可根据设置的配额启用或禁用发送。

![](assets/s_ncs_install_mta.png)

* 统计服务器(**stat**)链接到Adobe Campaign库以加载其配置。
* 投放服务器(**mta**)使用UDP联系并非始终属于其自己实例的统计服务器。

### 投放服务器 {#delivery-servers}

的 **mta** 模块将消息分发到其 **母乳** 子模块。 每个 **母乳** 在从统计服务器请求授权并发送消息之前准备消息。

步骤如下：

1. 的 **mta** 选择符合条件的消息并为其分配可用消息 **母乳**.
1. 的 **母乳** 加载构建消息（内容、个性化元素、附件、图像等）所需的所有信息 并将消息转发到 **电子邮件流量整形器**.
1. 电子邮件流量整形器收到统计服务器的授权后(**smtp stat**)，则会将消息发送给收件人。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 电子邮件服务器统计信息和限制 {#email-server-statistics-and-limitations}

统计信息服务器维护接收消息的每个电子邮件服务器的以下统计信息：

* 打开的时间点连接数，
* 最近一小时内发送的消息数，
* 成功/拒绝连接的速率，
* 与不可访问服务器的连接率。

同时，模块会加载特定电子邮件服务器的限制列表：

* 最大同时连接数，
* 每小时最大消息数，
* 每个连接的消息数上限。

### 管理IP地址 {#managing-ip-addresses}

统计信息服务器可以合并具有相同公共IP地址的多个实例或多台计算机。 因此，它未链接到特定实例，但是它必须联系实例才能恢复每个域的限制。

将保留每个目标MX和每个源IP的投放统计信息。 例如，如果目标域有5个MX，而平台可以使用3个不同的IP地址，则服务器可以管理此域最多15个系列指示器。

源IP地址与公共IP地址匹配，即远程电子邮件服务器看到的地址。 此IP地址可能与托管的计算机的地址不同 **mta**，如果提供NAT路由器。 这就是为什么统计服务器使用与公共IP匹配的标识符(**publicId**)。 本地地址与此标识符之间的关联在 **serverConf.xml** 配置文件。 中所有可用的参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).

## 投放输出控制 {#delivery-output-controlling}

要向电子邮件服务器发送消息，请 **电子邮件流量整形器** 组件从统计信息服务器请求连接。 请求被接受后，连接即会打开。

在发送消息之前，模块会从服务器请求“令牌”。 这些令牌通常至少包含10个令牌，可减少对服务器的查询数。

服务器会保存与连接和投放相关的所有统计信息。 如果重新启动，信息会暂时丢失：每个客户端都保留其发送统计信息的本地副本，并定期（每2分钟）将其返回到服务器。 然后，服务器可以重新聚合数据。

以下各节介绍了 **电子邮件流量整形器** 组件。

### 消息投放 {#message-delivery}

发送消息后，可能会得到3个结果：

1. **成功**:消息发送成功。 消息已更新。
1. **消息失败**:联系的服务器拒绝了所选收件人的消息。 此结果与返回代码550到599匹配，但可以定义例外。
1. **会话失败** （向上5.11）：如果 **mta** 收到此消息的答案后，消息将被放弃(请参阅 [消息放弃](#message-abandonment))。 消息将发送到其他路径，或者如果没有其他路径可用，则设置为“待处理”(请参阅 [消息挂起](#message-pending))。

   >[!NOTE]
   >
   >A **路径** 是Adobe Campaign **mta** 和目标 **mta**. Adobe Campaign **mta** 可以从多个起始IP和多个目标域IP中进行选择。

### 消息放弃 {#message-abandonment}

放弃的消息会返回到 **mta** 不再由 **母乳**.

的 **mta** 决定此邮件的程序（恢复、放弃、隔离等） 取决于响应代码和规则。

### 消息挂起 {#message-pending}

当消息到达活动队列且没有可用路径时，消息将被挂起。

在发生连接错误后，路径通常被标记为不可用于变量时间量。 不可用期限取决于错误的频率和年龄。

## 统计服务器配置 {#statistics-server-configuration}

统计信息服务器可供多个实例使用：它必须独立于将使用它的实例进行配置。

首先，定义将托管配置的Adobe Campaign数据库。

### 开始配置 {#start-configuration}

默认情况下， **stat** 每个实例将启动模块。 当实例在同一台计算机上池化，或当实例共享同一IP地址时，会使用单个统计服务器：其他人必须残疾。

### 服务器端口的定义 {#definition-of-the-server-port}

默认情况下，统计服务器监听端口7777。 此端口可在 **serverConf.xml** 文件。 中所有可用的参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## MX配置 {#mx-configuration}

>[!IMPORTANT]
>
>对于托管安装或混合安装(如果已升级到 [增强的MTA](../../delivery/using/sending-with-enhanced-mta.md), **[!UICONTROL MX management]** 不再使用投放吞吐量规则。 Enhanced MTA使用其自己的MX规则，根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，根据域自定义您的吞吐量。

### 关于MX规则 {#about-mx-rules}

>[!NOTE]
>
>本节和以下各节仅适用于使用旧版Campaign MTA的内部部署安装和托管/混合安装。

MX规则（邮件eXchanger）是管理发送服务器与接收服务器之间通信的规则。

这些规则会在每天早上6点（服务器时间）自动重新加载，以便定期提供客户端实例。

ISP将根据材料容量和内部策略，接受预定义的每小时连接和消息数量。 ISP系统可根据IP和发送域的信誉自动修改这些变量。 Adobe Campaign通过其可投放性平台，由ISP管理150多个特定规则，此外，还管理其他域的一个通用规则。

最大连接数不完全取决于MTA使用的公共IP地址数。

例如，如果您在MX规则中允许5个连接，并且配置了2个公共IP，则您可能认为您无法同时打开到此域的连接超过10个。 这不是事实，事实上，最大连接数是指一条路径和一条路径，该路径是我们的MTA公共IP和客户端MTA的公共IP之一的组合。

在以下示例中，用户配置了两个公共IP地址，域为yahoo.com。

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

yahoo.com的MX记录告诉我们yahoo.com有3个邮件交换器。 要连接对等邮件交换器，MTA将从DNS请求其IP地址。

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

对于此记录，用户可以联系8个对等IP地址。 由于用户有2个公共IP地址，因此这会为他们提供8 * 2 = 16的组合，以访问yahoo.com邮件服务器。 这些组合中的每个组合都称为路径。

第二个MX记录显示为：

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

这8个IP地址中的4个已在mta5（98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203）中使用。 此记录允许用户使用4个新IP地址。 第三个MX记录也会这样做。

我们总共有16个远程IP地址。 与我们的2个本地公共IP结合，我们有32个路径可访问yahoo.com邮件服务器。

>[!NOTE]
>
>如果2条MX记录引用的是相同的IP地址，则这条记录将计为一条路径，而不是两条。

以下是使用MX规则的一些示例：

![](assets/s_ncs_examples_mx_rules.png)

在以下示例中，用户对特定域每小时有10,000条消息的限制，但MTA吞吐量容量高于此限制。

在这种情况下，流量会被划分为12个时段，每小时5分钟，而实际限制是每个时段833条消息。

这些消息将尽快发送。

![](assets/s_ncs_traffic_shaping.png)

### 配置MX管理 {#configuring-mx-management}

MX所遵守的规则在 **[!UICONTROL MX management]** 文档 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 树的节点。

如果 **[!UICONTROL MX management]** 文档在节点中不存在，您可以手动创建它。 操作步骤：

1. 创建一组新的邮件规则。
1. 选择 **[!UICONTROL MX management]** 模式。

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 输入 **defaultMXRules** 在 **[!UICONTROL Internal name]** 字段。

为了考虑更改，您需要重新启动统计信息服务器。

要在不重新启动统计信息服务器的情况下重新加载配置，请在承载该服务器的计算机上使用以下命令： `nlserver stat -reload`

>[!NOTE]
>
>与 **nlserver重新启动**. 它可防止在重新启动丢失之前收集的统计信息，并避免使用高峰时可能与MX规则中定义的配额相冲突。

### 配置MX规则 {#configuring-mx-rules}

的 **[!UICONTROL MX management]** 文档列出了链接到MX规则的所有域。

这些规则将依次应用：应用MX掩码与目标MX兼容的第一个规则。

每个规则可用的以下参数包括：

* **[!UICONTROL MX mask]**:应用规则的域。 每个规则都为MX定义一个地址掩码。 因此，名称与此掩码匹配的任何MX均符合条件。 掩码可以包含“&#42;&quot;和&quot;?&quot; 一般字符。

   例如，以下地址：

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   与以下掩码兼容：

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

   例如，对于电子邮件地址foobar@gmail.com，域名为gmail.com，MX记录为：

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   在这种情况下，MX规则 `*.google.com` 中，将使用。 如您所见，MX规则掩码不一定匹配邮件中的域。 对gmail.com电子邮件地址应用的MX规则将是带有掩码的规则 `*.google.com`.

* **[!UICONTROL Range of identifiers]**:利用此选项，可指示应用规则的标识符(publicID)范围。 您可以指定：

   * 数字：该规则将仅适用于此publicId，
   * 数字范围(**number1-number2**):该规则将应用于这两个数字之间的所有publicId。

   >[!NOTE]
   >
   >如果字段为空，则规则将应用于所有标识符。

   公共ID是一个或多个MTA使用的公共IP的内部标识符。 这些ID在MTA服务器(位于 **config-instance.xml** 文件。

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**:定义此MX规则的属性范围。 选中此选项后，所有参数都将共享到实例上所有可用的IP上。 如果未选中，则会为每个IP定义MX规则。 最大消息数乘以可用IP数。
* **[!UICONTROL Maximum number of connections]**:与发件人域的同时连接的最大数量。
* **[!UICONTROL Maximum number of messages]**:可在连接上发送的消息数上限。 当消息数超过此数时，将关闭连接并打开新连接。
* **[!UICONTROL Messages per hour]**:在一小时内可向发件人域发送的消息数上限。
* **[!UICONTROL Connection time out]**:用于连接到域的时间阈值。

   >[!NOTE]
   >
   >Windows可以发出 **超时** 在此阈值之前，具体取决于您的Windows版本。

* **[!UICONTROL Timeout Data]**:发送消息内容后的最长等待时间（SMTP协议的“数据”部分）。
* **[!UICONTROL Timeout]**:与SMTP服务器进行其他交换的最长等待时间。
* **[!UICONTROL TLS]**:可以选择性地启用允许您加密电子邮件投放的TLS协议。 对于每个MX掩码，可使用以下选项：

   * **[!UICONTROL Default configuration]**:这是在应用的serverConf.xml配置文件中指定的常规配置。

      >[!IMPORTANT]
      >
      >不建议修改默认配置。

   * **[!UICONTROL Disabled]** :系统地发送消息，而不加密。
   * **[!UICONTROL Opportunistic]** :如果接收服务器(SMTP)可以生成TLS协议，则会加密消息投放。

配置示例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>有关将MX服务器与Adobe Campaign结合使用的更多信息，请参阅 [此部分](../../installation/using/using-mx-servers.md).

### 管理电子邮件格式 {#managing-email-formats}

您可以定义已发送消息的格式，以便显示的内容会根据每个收件人地址的域自动进行调整。

要执行此操作，请转到 **[!UICONTROL Management of email formats]** 文档，位于 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

本文档包含与Adobe Campaign管理的日语格式对应的所有预定义域的列表。 有关更多信息，请参阅 [本文档](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

的 **MIME结构** （多用途Internet邮件扩展）参数允许您定义要发送到不同邮件客户端的邮件结构。 提供了三个选项：

* **多部分**:消息以文本或HTML格式发送。 如果HTML格式不被接受，消息仍将能够以文本格式显示。

   默认情况下，多部分结构为 **复合/可选**，但会自动变为 **复合/相关** 将图像添加到消息时。 某些提供商期望 **复合/相关** 格式（默认） **[!UICONTROL Force multipart/related]** 选项会强加此格式，即使未附加图像也是如此。

* **HTML**:仅发送HTML消息。 如果HTML格式未被接受，则不会显示消息。
* **文本**:将发送仅文本格式的消息。 文本格式消息的优势在于其大小非常小。

如果 **[!UICONTROL Image inclusion]** 选项时，这些值会直接显示在电子邮件正文中。 然后，将上传图像，URL链接将被其内容替换。

此选项在日本市场中特别用于 **Deco-mail**, **Decore Mail** 或 **装饰邮件**. 有关详细信息，请查阅 [本文档](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>在电子邮件中插入图像会显着增加图像大小。

## 投放服务器配置 {#delivery-server-configuration}

### 时钟同步 {#clock-synchronization}

构成Adobe Campaign平台（包括数据库）的所有服务器的时钟必须同步，并且其系统设置为同一时区。

### 统计服务器的坐标 {#coordinates-of-the-statistics-server}

必须在 **mta**.

的 **statServerAddress** 属性 **mta** 通过配置的元素，您可以指定要使用的端口的地址和编号。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

要在同一台计算机上使用统计服务器，必须至少使用 **localhost** 值：

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>如果未填充此字段，则 **mta** 不会启动。

### 要使用的IP地址列表 {#list-of-ip-addresses-to-use}

有关流量管理的配置位于 **mta/child/smtp** 配置文件的元素。

对于 **IPAffinity** 元素中，您需要声明可用于计算机的IP地址。

示例:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

参数如下：

* **地址**:这是要使用的MTA主机的IP地址。
* **heloHost**:此标识符表示SMTP服务器将看到的IP地址。

* **publicId**:当多个Adobe Campaign共享IP地址时，此信息非常有用 **mtas** 在NAT路由器后面。 统计信息服务器使用该标识符来存储该起始点和目标服务器之间的连接并发送统计信息。
* **权重**:用于定义地址的相对使用频率。 默认情况下，所有地址的权重等于1。

>[!NOTE]
>
>在serverConf.xml文件中，您需要验证一个IP是否与具有唯一标识符(public_id)的单个主机相对应。 无法将其映射到多个主机，这可能会导致投放限制问题。

在上一个示例中，在正常情况下，地址将按如下方式分发：

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

例如，如果第一个地址不能用于给定的MX，则消息将按如下方式发送：

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**:允许您为属于特定域的电子邮件保留此IP地址。 这是可包含一个或多个通配符的掩码列表(“&#42;&#39;)。 如果未指定属性，则所有域都可以使用此IP地址。

   示例： **includeDomains=&quot;wanadoo.com，orange.com，yahoo。&#42;&quot;**

* **excludeDomains**:不包括此IP地址的域列表。 此过滤器在 **includeDomains** 过滤器。

   ![](assets/s_ncs_install_mta_ips.png)

## 电子邮件发送优化 {#email-sending-optimization}

Adobe Campaign的内部架构 **mta** 对优化电子邮件投放的配置有影响。 以下是有关改进投放的一些提示。

### 调整maxWaitingMessages参数 {#adjust-the-maxwaitingmessages-parameter}

的 **maxWaitingMessages** 参数指示事先准备的消息数量上限 **母乳**. 只有在消息被发送或放弃后，才会从此列表中删除它们。

如果消息未按域排序，此参数非常重要，特别重要。

一旦 **maxWorkingSetMb** (256)达到阈值，投放服务器停止发送消息。 性能将显着下降，直至 **母乳** 重新开始。 要避免此问题，您可以提高 **maxWorkingSetMb** 参数，或降低 **maxWaitingMessages** 参数。

的 **maxWorkingSetMb** 参数是通过将消息的最大数量乘以平均消息大小并乘以2.5来按经验计算的。例如，如果消息的平均大小为50 kB，并且 **maxWaitingMessages** 参数等于1,000，所用内存平均为125 MB。

### 调整匹配字段的数量 {#adjust-the-number-of-mtachild}

子代数不应超过计算机中的处理器数(约 1000场会议)。 我们建议您不要超过8 **母乳**. 然后，您可以增加每个 **孩子** (**maxMsgPerChild**)以实现足够的寿命。
