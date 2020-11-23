---
solution: Campaign Classic
product: campaign
title: 电子邮件发送能力
description: 电子邮件发送能力
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2973'
ht-degree: 0%

---


# 技术电子邮件配置{#email-deliverability}

## 概述 {#overview}

以下部分概述了在传送电子邮件时控制Adobe Campaign实例输出所需的配置。

>[!NOTE]
>
>某些配置只能通过Adobe来执行由Adobe托管的部署，例如，访问服务器和实例配置文件。 要进一步了解不同的部署，请参 [阅托管模型](../../installation/using/hosting-models.md) 部分或 [本页](../../installation/using/capability-matrix.md)。

有关可交付性相关概念和最佳实践的更多信息，请参阅本 [节](../../delivery/using/about-deliverability.md)。

本节提供有关Adobe Campaign平台有效发送和接收电子邮件的所有技术 [建议](../../delivery/using/technical-recommendations.md)。

## 工作原理 {#operating-principle}

可以控制一个或多个Adobe Campaign实例的输出，以限制根据域发送的电子邮件数。 例如，您可以将yahoo.com地址的输出限制为 **每小时20** ，同时为所有其他域配置每小时100,000条消息。

需要针对投放服务器(mta)使用的每个IP地址控制消&#x200B;**息输**&#x200B;出。 在多 **台计算机** 上划分并属于不同Adobe Campaign实例的多个mta可以共享相同的IP地址用于电子邮件投放:需要设置一个进程来协调这些IP地址的使用。

这是stat模块 **的功** 能：它将所有要发送到邮件服务器的连接请求和消息转发到一组IP地址。 统计服务器会跟踪投放，并可以根据设置的配额启用或禁用发送。

![](assets/s_ncs_install_mta.png)

* 统计服务器(**stat**)链接到Adobe Campaign库以加载其配置。
* 投放服务&#x200B;**器**(mta)使用UDP联系统计服务器，该服务器并不总是属于其自己的实例。

### 投放服务器 {#delivery-servers}

mta **模块** 将消息分发到 **其mtachild子模** 块。 每个 **计算** 域在从统计服务器请求授权并发送之前准备消息。

步骤如下：

1. mta选 **择符** 合条件的消息，并为它们分配一个可 **用的字段**。
1. 该模 **板** 可加载构建邮件所需的所有信息（内容、个性化元素、附件、图像等） 并将消息转发 **到Email Traffic Shaper**。
1. 一旦电子邮件流量整形器接收到统计服务器的授权(**smtpstat**)，消息就会发送到收件人。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 电子邮件服务器统计和限制 {#email-server-statistics-and-limitations}

统计服务器为接收消息的每个电子邮件服务器维护以下统计信息：

* 打开的时间点连接数，
* 最后一小时发送的消息数，
* 成功／拒绝连接的速率，
* 与不可到达服务器的连接速率。

同时，该模块加载了对某些电子邮件服务器的一列表限制：

* 同时连接的最大数量，
* 每小时最大消息数，
* 每个连接的最大消息数。

### 管理IP地址 {#managing-ip-addresses}

统计服务器可以组合多个实例或多台具有相同公共IP地址的计算机。 因此，它不链接到特定实例，但它必须联系实例才能恢复每个域的限制。

投放统计信息会保留每个目标MX和每个源IP的数据。 例如，如果目标域有5个MX，并且该平台可以使用3个不同的IP地址，则服务器可以管理此域的多达15个系列指示符。

源IP地址与公共IP地址匹配，即远程电子邮件服务器所看到的地址。 如果提供了NAT路由器，则此IP地址可以与承载mta **的计算机**&#x200B;的地址不同。 这就是为什么统计服务器使用与公共IP(publicId)匹配的标&#x200B;**识符**。 本地地址与此标识符之间的关联在serverConf.xml **配置文件中** 声明。 serverConf.xml中的所 **有可用参数** 都列在本 [节中](../../installation/using/the-server-configuration-file.md)。

## 投放输出控制 {#delivery-output-controlling}

要向电子邮件服务器发送消息， **Email Traffic** Shaper组件会请求统计服务器的连接。 接受请求后，将打开连接。

在发送消息之前，模块从服务器请求“令牌”。 这些令牌通常至少包含10个令牌，可减少服务器的查询数。

服务器保存所有与连接和投放相关的统计信息。 如果重新启动，信息将暂时丢失：每个客户端都保留发送统计数据的本地副本，并定期（每2分钟）将其返回给服务器。 然后，服务器可以重新聚合数据。

以下各节介绍了电子邮件流量整形器组 **件对消息的处** 理。

### 消息投放 {#message-delivery}

发送消息时，可能有3个结果：

1. **成功**:消息发送成功。 消息将更新。
1. **消息失败**:联系的服务器拒绝了所选收件人的消息。 此结果与返回代码550至599匹配，但可以定义例外。
1. **会话失败** （向上5.11）:如果 **mta** 收到此消息的答案，则消息将被放弃(请参阅消 [息放弃](#message-abandonment))。 消息将发送到其他路径，如果没有其他路径可用，则设置为“挂起”(请参阅“ [消息挂起](#message-pending)”)。

   >[!NOTE]
   >
   >路 **径** 是Adobe Campaignmta和 **目标mta之间的** 连接 ****。 Adobe Campaign **** mta可以从多个开始IP和多个目标域IP中进行选择。

### 消息放弃 {#message-abandonment}

放弃的消息将返回 **到mta** ，并且不再由mtachild管 **理**。

mta **决定** 此消息的程序(恢复、放弃、隔离等) 取决于响应代码和规则。

### 消息挂起 {#message-pending}

当消息到达活动队列且没有可用路径时，消息将暂停。

在连接错误后，路径通常被标记为不可用于可变时间量。 不可用期取决于错误的频率和年龄。

## 统计服务器配置 {#statistics-server-configuration}

统计服务器可以由多个实例使用：它必须独立于将使用它的实例进行配置。

开始，方法是定义将托管配置的Adobe Campaign数据库。

### 开始配置 {#start-configuration}

默认情况下，每 **个实例** 都会启动stat模块。 当实例在同一台计算机上共享时，或当实例共享相同的IP地址时，将使用单个统计信息服务器：其他人必须被禁用。

### 服务器端口的定义 {#definition-of-the-server-port}

默认情况下，统计服务器监听端口7777。 可以在serverConf.xml文件 **中修改此端口** 。 serverConf.xml中的所 **有可用参数** 都列在本 [节中](../../installation/using/the-server-configuration-file.md)。

```
<stat port="1234"/>
```

## MX配置 {#mx-configuration}

### 关于MX规则 {#about-mx-rules}

MX规则（邮件eXchanger）是管理发送服务器与接收服务器之间通信的规则。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则不 **[!UICONTROL MX management]** 再使用投放吞吐量规则。 增强的MTA使用其自己的MX规则，该规则允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。
>
>有关Adobe Campaign增强MTA的详细信息，请参阅此 [文档](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)。

这些规则每天早上6点（服务器时间）自动重新加载，以便定期提供客户端实例。

ISP将接受每小时预定数量的连接和消息，具体取决于材料容量和内部策略。 ISP系统可以根据IP和发送域的信誉自动修改这些变量。 Adobe Campaign通过其可交付性平台管理ISP提供的150多个特定规则，此外还管理其他域的一个通用规则。

连接的最大数量并不完全取决于MTA使用的公共IP地址数。

例如，如果您在MX规则中允许5个连接，并且您配置了2个公共IP，您可能认为不能同时打开10个以上的连接到此域。 这不是真的，事实上，最大连接数是指一个路径和一条路径，它是我们的MTA公共IP和客户端MTA的公共IP的组合。

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

对于此记录，用户可以联系8个对等IP地址。 由于他有2个公共IP地址，因此他有8 * 2 = 16个组合可连接到yahoo.com邮件服务器。 这些组合中的每一种都称为路径。

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

mta5（98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203）中已使用这8个IP地址中的4个。 此记录允许用户使用4个新IP地址。 第三个MX记录也会这样做。

总共有16个远程IP地址。 与我们的2个本地公共IP相结合，我们有32条路径可连接到yahoo.com邮件服务器。

>[!NOTE]
>
>如果2个MX记录引用的IP地址相同，则此MX记录将计为一个路径，而不计为两个。

以下是使用MX规则的一些示例：

![](assets/s_ncs_examples_mx_rules.png)

在以下示例中，用户对特定域的每小时限制为10,000条消息，但MTA吞吐量容量高于此限制。

在这种情况下，流量被分为12个时段，每小时5分钟，而实际限制是每个时段833条消息。

这些消息将尽快传递。

![](assets/s_ncs_traffic_shaping.png)

### 配置MX管理 {#configuring-mx-management}

MX要遵循的规则在树的节 **[!UICONTROL MX management]** 点文档 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 中定义。

如果 **[!UICONTROL MX management]** 文档在节点中不存在，则可以手动创建它。 操作步骤：

1. 创建新邮件规则集。
1. Choose the **[!UICONTROL MX management]** mode.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 在 **字段中输入** default **[!UICONTROL Internal name]** MXRules。

为了考虑更改，您需要重新启动统计服务器。

要在不重新启动统计信息服务器的情况下重新加载配置，请在承载服务器的计算机上使用以下命令： `nlserver stat -reload`

>[!NOTE]
>
>此命令行优先于nlserver **重新启动**。 它可防止在重新启动丢失之前收集的统计信息，并避免使用高峰时会与MX规则中定义的配额相冲突。

### 配置MX规则 {#configuring-mx-rules}

文档 **[!UICONTROL MX management]** 列表所有链接到MX规则的域。

这些规则按顺序应用：应用其MX掩码与目标MX兼容的第一个规则。

每个规则的以下可用参数为：

* **[!UICONTROL MX mask]**:应用规则的域。 每个规则定义MX的地址掩码。 因此，其名称与此掩码匹配的任何MX都符合条件。 遮罩可包含“*”和“?” 通用字符。

   例如，以下地址：

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   与以下蒙版兼容：

   * *.yahoo.com
   * ?.mx.yahoo.com

   例如，对于电子邮件地址foobar@gmail.com，域为gmail.com,MX记录为：

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   在这种情况下，将 `*.google.com` 使用MX规则。 如您所见，MX规则掩码不一定与邮件中的域匹配。 适用于gmail.com电子邮件地址的MX规则将是带有遮罩的规则 `*.google.com`。

* **[!UICONTROL Range of identifiers]**:此选项允许您指示应用规则的标识符(publicID)范围。 您可以指定：

   * 数字：规则将仅适用于此publicId,
   * 数字范围(**number1-number2**):该规则将适用于这两个数字之间的所有publicId。

   >[!NOTE]
   >
   >如果字段为空，则规则将应用于所有标识符。

   公共ID是一个或多个MTA使用的公共IP的内部标识符。 这些ID在MTA服务器中的config-instance. **xml文件中进行定义** 。

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**:定义此MX规则的属性范围。 选中后，所有参数都将共享到实例上所有可用的IP上。 如果不选中，将为每个IP定义MX规则。 最大消息数乘以可用IP数。
* **[!UICONTROL Maximum number of connections]**:到发送方域的同时连接的最大数目。
* **[!UICONTROL Maximum number of messages]**:在连接上可以发送的最大消息数。 当消息超过此数时，将关闭连接并打开新连接。
* **[!UICONTROL Messages per hour]**:发送方域可在一小时内发送的最大消息数。
* **[!UICONTROL Connection time out]**:连接到域的时间阈值。

   >[!NOTE]
   >
   >Windows可以在此阈 **值之** 前发出超时，这取决于您的Windows版本。

* **[!UICONTROL Timeout Data]**:发送邮件内容（SMTP协议的“数据”部分）后的最长等待时间。
* **[!UICONTROL Timeout]**:与SMTP服务器进行其他交换的最长等待时间。
* **[!UICONTROL TLS]**:TLS协议允许您对电子邮件投放进行加密，可以有选择地启用。 对于每个MX蒙版，都提供以下选项：

   * **[!UICONTROL Default configuration]**:这是在所应用的serverConf.xml配置文件中指定的常规配置。

      >[!IMPORTANT]
      >
      >不建议修改默认配置。

   * **[!UICONTROL Disabled]** :系统发送消息时不加密。
   * **[!UICONTROL Opportunistic]** :如果接收服务器(SMTP)可以生成TLS协议，则消息投放将被加密。

配置示例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### 管理电子邮件格式 {#managing-email-formats}

您可以定义已发送消息的格式，以便显示的内容会根据每个收件人地址的域自动调整。

为此，请转到 **[!UICONTROL Management of email formats]** 文档，该位于 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**。

此文档包含所有预定义域的列表，这些域与Adobe Campaign管理的日文格式相对应。 For more information, refer to [this document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

MIME结 **构** （多用途Internet邮件扩展）参数允许您定义将发送给不同邮件客户端的邮件结构。 提供了三个选项：

* **多部分**:消息以文本或HTML格式发送。 如果HTML格式不被接受，消息仍能以文本格式显示。

   默认情况下，多部件结构是多 **部件／替代结构**，但当将图像添加到 **消息时，它会自动变** 为多部件／相关结构。 某些提供者预 **期默认采用** multipart/related格式 **[!UICONTROL Force multipart/related]** ，即使未附加图像，此选项也强制采用此格式。

* **HTML**:将发送仅HTML消息。 如果HTML格式不被接受，则不显示消息。
* **文本**:将发送仅文本格式的消息。 文本格式消息的优点是其大小很小。

如果启 **[!UICONTROL Image inclusion]** 用了此选项，则这些选项会直接显示在电子邮件正文中。 随后将上传图像，URL链接将替换为其内容。

日本市场特别使用此选 **项处理Deco邮件**、 **Decore邮件** 或 **装饰邮件**。 有关详细信息，请参 [阅此文档](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

>[!IMPORTANT]
>
>在电子邮件中插入图像会显着增加其大小。

## 投放服务器配置 {#delivery-server-configuration}

### 时钟同步 {#clock-synchronization}

组成Adobe Campaign平台（包括数据库）的所有服务器的时钟必须同步，并且其系统设置为同一时区。

### 统计服务器的坐标 {#coordinates-of-the-statistics-server}

统计服务器的地址必须在mta中提 **供**。

通过 **配置** mta元素 **的statServerAddress属性** ，可以指定要使用的端口的地址和编号。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

要在同一台计算机上使用统计信息服务器，必须至少输入具有localhost值的计算机 **名** :

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>如果未填充此字段，则mta **将不** 会开始。

### 要使用的IP地址列表 {#list-of-ip-addresses-to-use}

有关流量管理的配置位于 **配置文件的mta/child** /smtp元素中。

对于 **每个IPAfinity** 元素，您需要声明可用于计算机的IP地址。

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
* **helo主机**:此标识符表示SMTP服务器将看到的IP地址。

* **publicId**:当NAT路由器后的多个Adobe Campaignmtas共享IP地 **址** 时，此信息很有用。 统计服务器使用此标识符来存储该起始点与目标服务器之间的连接和发送统计信息。
* **权重**:允许您定义地址的相对使用频率。 默认情况下，所有地址的权重均等于1。

>[!NOTE]
>
>在serverConf.xml文件中，您需要验证一个IP是否对应具有唯一标识符(public_id)的单个主机。 无法将其映射到多个主机，这可能会导致投放限制问题。

在上一个示例中，在正常情况下，地址将按如下方式分配：

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

例如，如果第一个地址不能用于给定的MX，则消息将按如下方式发送：

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**:允许您为属于特定域的电子邮件保留此IP地址。 这是一列表蒙版，可包含一个或多个通配符(“*”)。 如果未指定属性，则所有域都可以使用此IP地址。

   示例： **includeDomains=&quot;wanadoo.com,orange.com,yahoo.*&quot;**

* **excludeDomains**:不包括此IP地址的列表域。 在includeDomains过滤器后应 **用此过滤** 器。

   ![](assets/s_ncs_install_mta_ips.png)

## 电子邮件发送优化 {#email-sending-optimization}

Adobe Campaignmta的内部架构 **对** 、优化电子邮件投放的配置有影响。 以下是有关改进投放的一些提示。

### 调整maxWaitingMessages参数 {#adjust-the-maxwaitingmessages-parameter}

maxWaitingMessages **参数指示mtachild预先准备的最大消息** 数 ****。 仅当消息被发送或放弃后，才会从此列表中删除这些消息。

如果消息未按域排序，则此参数很重要，尤其重要。

达到 **maxWorkingSetMb** (256)阈值后，投放服务器将停止发送消息。 性能将显着下降，直到 **开始** 再次上升。 要避免此问题，您可以增加maxWorkingSetMb参 **数的阈值** ，也可以减小maxWaitingMessages参 **数的阈值** 。

maxWorkingSetMb **参数是通过经验计算的，方法是将消息的最大数乘以平均消息大小，再乘以结果2.5。例如，如果消息的平均大小为50 kB,** 且maxWaitingMessages **** 参数等于1,000，则使用的内存将平均为125 MB。

### 调整匹配字段的数量 {#adjust-the-number-of-mtachild}

子代数不应超过计算机中的处理器数(约 1000个会话)。 我们建议您不要超过8 **英镑**。 然后，您可以增加每个子代 **的消息** (**maxMsgPerChild**)数量，以实现足够的寿命。
