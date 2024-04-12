---
product: campaign
title: 技术电子邮件配置
description: 了解如何配置Campaign以在投放电子邮件时控制实例的输出
feature: Installation, Deliverability
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '3094'
ht-degree: 0%

---

# 技术电子邮件配置{#email-deliverability}



## 概述 {#overview}

以下部分概述了在投放电子邮件时控制Adobe Campaign实例输出所需的配置。

>[!NOTE]
>
>某些配置只能由Adobe托管的部署的Adobe执行，例如访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 区域或至 [此页面](../../installation/using/capability-matrix.md).

有关与Adobe Campaign可投放性相关的概念和最佳实践的更多信息，请参阅此 [部分](../../delivery/using/about-deliverability.md).

要更深入地了解什么是可投放性，包括有关Adobe平台有效发送和接收电子邮件的所有技术建议，请参阅 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

## 操作原则 {#operating-principle}

可以控制一个或多个Adobe Campaign实例的输出，以根据域限制发送的电子邮件数量。 例如，您可以将输出限制为每小时20,000，对于 **yahoo.com** 地址，而为所有其他域每小时配置100,000条消息。

对于投放服务器使用的每个IP地址，需要控制消息输出(**mta**)。 多个 **mta** 如果细分到多台计算机，并且属于不同的Adobe Campaign实例，则可能会共享相同的IP地址来发送电子邮件：需要设置一个流程来协调这些IP地址的使用。

这就是 **stat** 模块确实如此：它会转发要发送给一组IP地址邮件服务器的所有连接请求和消息。 统计服务器跟踪投放情况，可根据设置的配额启用或禁用发送。

![](assets/s_ncs_install_mta.png)

* 统计信息服务器(**stat**)已链接到Adobe Campaign库以加载其配置。
* 投放服务器(**mta**)使用UDP联系并不总是属于其自身实例的统计服务器。

### 投放服务器 {#delivery-servers}

此 **mta** 模块将消息分发到其 **matachild** 子模块。 每个 **matachild** 在请求统计服务器的授权并发送之前准备消息。

步骤如下：

1. 此 **mta** 选择符合条件的消息并为其分配可用消息 **matachild**.
1. 此 **matachild** 加载构建消息所需的所有信息（内容、个性化元素、附件、图像等） 并将消息转发到 **电子邮件流量整形器**.
1. 一旦电子邮件流量生成器收到统计服务器的授权(**smtp状态**)，则消息将发送给收件人。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 电子邮件服务器统计和限制 {#email-server-statistics-and-limitations}

统计信息服务器维护接收消息的每个电子邮件服务器的以下统计信息：

* 打开的时间点连接数，
* 过去一小时内发送的消息数，
* 成功/拒绝连接的速率，
* 与无法访问服务器的连接速率。

同时，模块会加载特定电子邮件服务器的限制列表：

* 最大同时连接数，
* 每小时最大消息数，
* 每个连接的最大消息数。

### 管理IP地址 {#managing-ip-addresses}

统计服务器可以组合多个实例或具有相同公共IP地址的多台计算机。 因此，它不会链接到特定的实例，但必须联系实例才能恢复每个域的限制。

保留每个目标MX和每个源IP的投放统计信息。 例如，如果目标域具有5个MX，并且平台可以使用3个不同的IP地址，则服务器可以管理此域的最多15系列指标。

源IP地址与公共IP地址匹配，即远程电子邮件服务器看到的地址。 此IP地址可能不同于承载此IP地址的计算机的地址 **mta**，如果提供了NAT路由器。 这就是为什么统计服务器使用与公共IP (**publicId**)。 本地地址与此标识符之间的关联在 **serverConf.xml** 配置文件。 中所有可用的参数，请参见 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).

## 投放输出控制 {#delivery-output-controlling}

要将消息传送到电子邮件服务器，请 **电子邮件流量整形器** 组件向统计服务器请求连接。 请求被接受后，连接即会打开。

在发送消息之前，模块会从服务器请求“令牌”。 这些令牌通常至少包含10个令牌集，可减少向服务器查询的次数。

服务器将保存与连接和投放相关的所有统计信息。 在重新启动时，信息会暂时丢失：每个客户端都会保留其发送统计信息的本地副本，并定期（每2分钟）将其返回服务器。 然后，服务器可以重新聚合数据。

以下各节介绍用户如何处理消息： **电子邮件流量整形器** 组件。

### 消息投放 {#message-delivery}

发送消息时，可能有3个结果：

1. **成功**：消息已成功发送。 消息已更新。
1. **消息失败**：联系的服务器拒绝了选定收件人的消息。 此结果与550到599的返回代码匹配，但可以定义例外。
1. **会话失败** （对于5.11以上版本）：如果 **mta** 接收此消息的应答，该消息将被放弃(请参阅 [消息放弃](#message-abandonment))。 消息将发送到其他路径，如果没有其他路径可用，则设置为待定(请参阅 [消息待定](#message-pending))。

   >[!NOTE]
   >
   >A **路径** 是Adobe Campaign之间的连接 **mta** 和目标 **mta**. Adobe Campaign **mta** 可以从多个起始IP和多个目标域IP中进行选择。

### 消息放弃 {#message-abandonment}

已放弃的消息将返回到 **mta** 不再受 **matachild**.

此 **mta** 决定此报文的程序（恢复、丢弃、隔离等） 取决于响应代码和规则。

### 消息待定 {#message-pending}

当消息到达活动队列且没有可用路径时，该消息将被挂起。

路径通常会在连接错误后的不同时间段内标记为不可用。 不可用期取决于错误的频率和持续时间。

## 统计服务器配置 {#statistics-server-configuration}

统计信息服务器可供多个实例使用：它必须独立于将使用它的实例进行配置。

首先，定义将托管配置的Adobe Campaign数据库。

### 开始配置 {#start-configuration}

默认情况下， **stat** 为每个实例启动模块。 当实例池位于同一台计算机上或实例共享同一IP地址时，将使用单个统计服务器：必须禁用其他服务器。

### 服务器端口的定义 {#definition-of-the-server-port}

默认情况下，统计服务器侦听端口7777。 可以在以下位置修改此端口 **serverConf.xml** 文件。 中所有可用的参数，请参见 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## MX配置 {#mx-configuration}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到 [增强MTA](../../delivery/using/sending-with-enhanced-mta.md)， **[!UICONTROL MX management]** 不再使用投放吞吐量规则。 Enhanced MTA会使用自己的MX规则，根据您自己的历史电子邮件信誉以及来自您发送电子邮件之域名的实时反馈，按域自定义您的吞吐量。

### 关于MX规则 {#about-mx-rules}

>[!NOTE]
>
>本节及以下部分仅适用于使用旧版Campaign MTA的内部部署和托管/混合安装。

MX规则（邮件交换器）是管理发送服务器和接收服务器之间通信的规则。

这些规则每天早上6点（服务器时间）自动重新加载，以定期提供客户端实例。

根据材料容量和内部政策， ISP将接受每小时预定义数量的连接和消息。 ISP系统可能会根据IP和发送域的信誉自动修改这些变量。 通过其可投放性平台，Adobe Campaign可由ISP管理150多条特定规则，此外，一条适用于其他域的通用规则。

最大连接数并不完全取决于MTA使用的公共IP地址数。

例如，如果您在MX规则中允许了5个连接，并且配置了2个公共IP，您可能会认为不能同时打开超过10个连接到此域。 这不是真的，事实上，最大连接数是指路径和由我们的MTA公共IP之一和客户端MTA的公共IP组成的路径。

在以下示例中，用户配置了两个公共IP地址，域为yahoo.com。

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

yahoo.com的MX记录告诉我们，yahoo.com有3个邮件交换器。 为了连接对等邮件交换器，MTA将向DNS请求其IP地址。

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

对于此记录，用户可以联系8个对等IP地址。 由于用户具有2个公共IP地址，因此这为他们提供了8 * 2 = 16个组合以访问yahoo.com邮件服务器。 这些组合中的每一个都称为路径。

第二条　MX记录显示为：

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

这8个IP地址中有4个已在mta5中使用（98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203）。 此记录允许用户使用4个新的IP地址。 第三条　MX记录也是一样。

我们总共有16个远程IP地址。 结合我们的2个本地公共IP，我们有32条路径可访问yahoo.com邮件服务器。

>[!NOTE]
>
>如果2条MX记录引用了相同的IP地址，则这条记录将计为一条路径，而不是两条路径。

以下是使用MX规则的一些示例：

![](assets/s_ncs_examples_mx_rules.png)

在下面的示例中，对于特定域，用户具有每小时10,000条消息的限制，但MTA吞吐量容量高于此限制。

在这种情况下，流量被划分为每小时5分钟的12个时段，实际限制为每时段833条消息。

将尽快发送这些消息。

![](assets/s_ncs_traffic_shaping.png)

### 配置MX管理 {#configuring-mx-management}

要遵守的MX规则定义于 **[!UICONTROL MX management]** 文档 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 树节点。

如果 **[!UICONTROL MX management]** 文档在节点中不存在，您可以手动创建它。 操作步骤：

1. 创建一组新的邮件规则。
1. 选择 **[!UICONTROL MX management]** 模式。

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 输入 **defaultMXRules** 在 **[!UICONTROL Internal name]** 字段。

为了将更改考虑在内，您需要重新启动统计服务器。

要重新加载配置而不重新启动统计信息服务器，请在承载该服务器的计算机上使用以下命令： `nlserver stat -reload`

>[!NOTE]
>
>此命令行比更适合 **nlserver重新启动**. 它可防止在重新启动丢失之前收集的统计信息，并避免可能违反MX规则中定义的配额的使用峰值。

### 配置MX规则 {#configuring-mx-rules}

此 **[!UICONTROL MX management]** 文档列出了链接到MX规则的所有域。

这些规则将按顺序应用：将应用其MX掩码与目标MX兼容的第一个规则。

以下参数可用于每个规则：

* **[!UICONTROL MX mask]**：应用规则的域。 每个规则都为MX定义一个地址掩码。 因此，任何名称与此掩码匹配的MX都是合格的。 蒙版可以包含&#39;&#39;&#42;”和“？” 通用字符。

  例如，以下地址：

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

  与以下掩码兼容：

   * &#42;.yahoo.com
   * ？.mx.yahoo.com

  例如，电子邮件地址foobar@gmail.com的域为gmail.com ，MX记录为：

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  在这种情况下，MX规则 `*.google.com` 将使用。 如您所见，MX规则掩码并不一定与邮件中的域匹配。 应用于gmail.com电子邮件地址的MX规则将是带有掩码的规则 `*.google.com`.

* **[!UICONTROL Range of identifiers]**：利用此选项可指示规则适用的标识符(publicID)范围。 您可以指定：

   * 数字：该规则将仅适用于此publicId，
   * 数字范围(**数字1 — 数字2**)：规则将应用于这两个数字之间的所有publicId。

  >[!NOTE]
  >
  >如果字段为空，则该规则将应用于所有标识符。

  公共ID是一个或多个MTA使用的公共IP的内部标识符。 这些ID是在的MTA服务器中定义的 **config-instance.xml** 文件。

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**：定义此MX规则的属性的范围。 选中后，所有参数将在实例上可用的所有IP上共享。 取消选中后，将为每个IP定义MX规则。 最大消息数乘以可用IP数。
* **[!UICONTROL Maximum number of connections]**：与发件人域的最大同时连接数。
* **[!UICONTROL Maximum number of messages]**：连接上可发送的最大消息数。 当消息超过此数目时，连接将关闭并打开一个新连接。
* **[!UICONTROL Messages per hour]**：一小时内发送到发件人域的最大消息数。
* **[!UICONTROL Connection time out]**：连接到域的时间阈值。

  >[!NOTE]
  >
  >Windows可以发出 **timeout** 在此阈值之前（具体取决于您的Windows版本）。

* **[!UICONTROL Timeout Data]**：发送消息内容后的最长等待时间（SMTP协议的DATA部分）。
* **[!UICONTROL Timeout]**：与SMTP服务器进行其他交换的最长等待时间。
* **[!UICONTROL TLS]**：允许您加密电子邮件投放的TLS协议可以选择性地启用。 对于每个MX掩码，可使用以下选项：

   * **[!UICONTROL Default configuration]**：这是所应用的serverConf.xml配置文件中指定的常规配置。

     >[!IMPORTANT]
     >
     >建议不要修改默认配置。

   * **[!UICONTROL Disabled]** ：消息会在不加密的情况下系统地发送。
   * **[!UICONTROL Opportunistic]** ：如果接收服务器(SMTP)可以生成TLS协议，则对消息投放进行加密。

配置示例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>有关将MX服务器与Adobe Campaign结合使用的详细信息，请参阅 [本节](../../installation/using/using-mx-servers.md).

### 管理电子邮件格式 {#managing-email-formats}

您可以定义已发送消息的格式，以便显示的内容可以根据每个收件人地址的域自动进行调整。

为此，请转到 **[!UICONTROL Management of email formats]** 文档，位于 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

本文档包含所有预定义域的列表，这些域对应于Adobe Campaign管理的日语格式。 有关更多信息，请参阅 [本文档](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

此 **MIME结构** （多用途Internet邮件扩展）参数允许您定义将发送到不同邮件客户端的消息结构。 提供了三个选项：

* **多部分**：消息以文本或HTML格式发送。 如果不接受HTML格式，则消息仍能够以文本格式显示。

  默认情况下，多部分结构为 **复合/可选**，但它会自动变为 **复合/相关** 在将图像添加到消息时。 某些提供商希望 **复合/相关** 格式默认情况下， **[!UICONTROL Force multipart/related]** 选项会强制使用此格式，即使未附加图像也是如此。

* **HTML**：仅发送HTML消息。 如果不接受HTML格式，则不会显示消息。
* **文本**：以纯文本格式发送消息。 文本格式消息的优点在于其非常小。

如果 **[!UICONTROL Image inclusion]** 选项，这些选项会直接显示在电子邮件的正文中。 然后，将上传图像，并将URL链接替换为其内容。

日本市场特别将此选项用于 **装饰邮件**， **装饰邮件** 或 **修饰邮件**. 欲知更多信息，请查阅 [本文档](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>在电子邮件中插入图像会显着增加其大小。

## 投放服务器配置 {#delivery-server-configuration}

### 时钟同步 {#clock-synchronization}

组成Adobe Campaign平台的所有服务器（包括数据库）的时钟必须同步，并且其系统设置为相同的时区。

### 统计服务器的坐标 {#coordinates-of-the-statistics-server}

统计服务器的地址必须在 **mta**.

此 **statServerAddress** 的属性 **mta** 元素配置允许您指定要使用的端口的地址和编号。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

要在同一台计算机上使用统计服务器，必须至少输入带有 **localhost** 值：

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>如果未填充此字段，则 **mta** 不会开始。

### 要使用的IP地址列表 {#list-of-ip-addresses-to-use}

有关流量管理的配置位于 **mta/child/smtp** 配置文件的元素。

对于每个 **IPAffinity** 元素，您需要声明可用于计算机的IP地址。

例如：

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

参数如下：

* **地址**：这是要使用的MTA主机的IP地址。
* **heloHost**：此标识符表示SMTP服务器将看到的IP地址。

* **publicId**：当IP地址由多个Adobe Campaign共享时，此信息很有用 **mta** 在NAT路由器后面。 统计信息服务器使用此标识符来记忆此起始点和目标服务器之间的连接和发送统计信息。
* **粗细**：用于定义地址的相对使用频率。 默认情况下，所有地址的权重均等于1。

>[!NOTE]
>
>在serverConf.xml文件中，您需要验证该IP是否与具有唯一标识符(public_id)的单个主机相对应。 它无法映射到多个主机，这可能会导致投放限制问题。

在上一个示例中，在正常条件下，地址将按如下方式进行分配：

    * “1”：5 / (5+5+1) = 45%
    * “2”：5 / (5+5+1) = 45%
    * “3”：1 / (5+5+1) = 10%

例如，如果第一个地址不能用于特定MX，则将按如下方式发送消息：

    * “2”：5 / (5+1) = 83%
    * “3”：1 / (5+1) = 17%

* **includeDomains**：用于为属于特定域的电子邮件保留此IP地址。 这是一个掩码列表，其中可以包含一个或多个通配符(&#39;&#42;&#39;)。 如果未指定属性，则所有域都可以使用此IP地址。

  示例： **includeDomains=&quot;wanadoo.com，orange.com，yahoo.&#42;&quot;**

* **excludedomains**：不包括此IP地址的域列表。 此筛选器应用在 **includeDomains** 筛选。

  ![](assets/s_ncs_install_mta_ips.png)

## 电子邮件发送优化 {#email-sending-optimization}

Adobe Campaign的内部架构 **mta** 对优化电子邮件投放的配置产生影响。 以下是有关改进投放的一些提示。

### 调整maxWaitingMessages参数 {#adjust-the-maxwaitingmessages-parameter}

此 **maxWaitingMessages** parameter指示由用户提前准备的消息的最大数目。 **matachild**. 只有在发送或放弃消息后，才会从此列表中删除这些消息。

此参数非常重要，并且在消息未按域排序时尤为关键。

一旦 **maxWorkingSetMb** (256)达到阈值，投放服务器停止发送消息。 性能将显着降低，直到 **matachild** 又开始了。 要规避此问题，您可以提高 **maxWorkingSetMb** 参数，或降低 **maxWaitingMessages** 参数。

此 **maxWorkingSetMb** 根据经验计算参数，将最大消息数乘以平均消息大小，并将结果乘以2.5。例如，如果消息的平均大小为50 kB，并且 **maxWaitingMessages** 参数等于1,000，则使用的平均内存为125 MB。

### 调整匹配项数 {#adjust-the-number-of-mtachild}

子级数量不应超过计算机中处理器的数量(约 1000个会话)。 我们建议您不要超过8个 **matachild**. 然后，您可以增加每个报表的邮件数 **子项** (**maxMsgPerChild**)以获得足够的寿命。
