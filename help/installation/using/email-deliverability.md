---
title: 电子邮件发送能力
seo-title: 电子邮件发送能力
description: 电子邮件发送能力
seo-description: null
page-status-flag: never-activated
uuid: 983aec6b-60f6-4c9b-a75a-1693958626c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 86c18986-1f65-40ff-80dc-1fbff37f406d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e8de8441303cb9d5102db2a95742ec7d38b16fc2

---


# 技术电子邮件配置{#email-deliverability}

## 概述 {#overview}

以下部分概述了在传送电子邮件时控制Adobe Campaign实例输出所需的配置。

>[!NOTE]
>
>某些配置只能由Adobe为Adobe托管的部署执行，例如，访问服务器和实例配置文件。 要进一步了解不同的部署，请参阅托 [管模型部分](../../installation/using/hosting-models.md) ，或 [本文](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

有关与可交付性相关的概念和最佳实践的详细信息，请参阅本 [节](../../delivery/using/about-deliverability.md)。

本节提供有关Adobe Campaign平台有效发送和接收电子邮件的所有技术建 [议](../../delivery/using/technical-recommendations.md)。

## 工作原理 {#operating-principle}

可以控制一个或多个Adobe Campaign实例的输出，以限制根据域发送的电子邮件数。 例如，您可以将 **** yahoo.com地址的输出限制为每小时20,000条，同时为所有其他域配置每小时100,000条消息。

需要针对传送服务器(mta **)使用的每个IP地址控制消息输**&#x200B;出。 在多 **台计算机上划分** 、属于各种Adobe Campaign实例的多个mta可以共享相同的IP地址进行电子邮件发送：需要设置一个进程来协调这些IP地址的使用。

这是stat模块 **的功** 能：它将所有连接请求和消息转发到邮件服务器以获得一组IP地址。 统计服务器会跟踪发送情况，并可以根据设置的配额启用或禁用发送。

![](assets/s_ncs_install_mta.png)

* 统计服务器(**stat**)链接到Adobe Campaign基础，以加载其配置。
* 传送服务器(**mta**)使用UDP与统计服务器联系，该服务器并不总是属于它们自己的实例。

### 交付服务器 {#delivery-servers}

mta **模块** ，将消息分发到 **其子模块** 。 每个 **计算机** 在从统计服务器请求授权并发送消息之前准备消息。

步骤如下：

1. mta选 **择符合条件** 的消息，并为其分配一个可 **用字段**。
1. 该模 **板加载构建消息** （内容、个性化元素、附件、图像等）所需的所有信息并将消息转发到电子邮 **件流量整形器**。
1. 一旦电子邮件流量整形器接收到统计服务器的授权(**smtpstat**)，消息就发送给收件人。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 电子邮件服务器统计数据和限制 {#email-server-statistics-and-limitations}

统计服务器为接收消息的每个电子邮件服务器维护以下统计信息：

* 打开的时间点连接数，
* 最后一小时发送的消息数，
* 连接成功／拒绝率，
* 到不可访问服务器的连接率。

同时，该模块加载了某些电子邮件服务器的限制列表：

* 同时连接的最大数量，
* 每小时最大消息数，
* 每个连接的最大消息数。

### 管理IP地址 {#managing-ip-addresses}

统计服务器可以将多个实例或多台计算机合并为具有相同公共IP地址。 因此，它不链接到特定实例，但它必须联系实例才能恢复每个域的限制。

每个目标MX和每个源IP都会保留交付统计信息。 例如，如果目标域有5个MX，并且平台可以使用3个不同的IP地址，则服务器可以为该域管理多达15个系列指示符。

源IP地址与公共IP地址匹配，即远程电子邮件服务器所看到的地址。 如果提供了NAT路由器，则此IP地址可以与承载 **mta的计算机的地址**&#x200B;不同。 这就是为什么统计服务器使用与公共IP(**publicId**)匹配的标识符。 本地地址与此标识符之间的关联在serverConf.xml配 **置文件中声明** 。 serverConf.xml中可用的所 **有参数都列在本节** 中 [](../../installation/using/the-server-configuration-file.md)。

## 传送输出控制 {#delivery-output-controlling}

要向电子邮件服务器发送消息， **** Email Traffic Shaper组件会请求统计服务器连接。 接受请求后，将打开连接。

在发送消息之前，模块从服务器请求“令牌”。 这些令牌通常至少包含10个令牌，从而减少了向服务器查询的次数。

服务器会保存与连接和交付相关的所有统计信息。 如果重新启动，信息会暂时丢失：每个客户端都保留发送统计信息的本地副本，并定期（每2分钟）将其返回给服务器。 然后，服务器可以重新聚合数据。

以下各节介绍了电子邮件流量Shaper组件对 **消息的处理** 。

### 消息传送 {#message-delivery}

发送消息时，可能会有3个结果：

1. **成功**:消息发送成功。 消息将更新。
1. **消息失败**:联系的服务器拒绝了所选收件人的消息。 此结果与返回代码550至599匹配，但可以定义例外。
1. **会话失败** （向上5.11）:如果 **mta** 收到此消息的答案，则消息将被放弃(请参阅消 [息放弃](#message-abandonment))。 消息将发送到其他路径，如果没有其他路径可用，则设置为“待定”(请参阅“消 [息待定](#message-pending)”)。

   >[!NOTE]
   >
   >路 **径** ，是Adobe Campaign **mta和目标mta** 之间的 **连接**。 Adobe Campaign **mta** 可以从多个起始IP和多个目标域IP中进行选择。

### 消息放弃 {#message-abandonment}

放弃的消息将返回 **到mta** ，并且不再由mtachild **管理**。

Mta **决定** ，此邮件的程序（恢复、放弃、隔离等）根据响应代码和规则。

### 消息待定 {#message-pending}

当消息到达活动队列且没有可用路径时，消息将暂停。

在发生连接错误后，路径通常被标记为不可用于可变的时间量。 不可用期取决于错误的频率和年龄。

## 统计服务器配置 {#statistics-server-configuration}

统计服务器可由多个实例使用：它必须独立于要使用它的实例进行配置。

首先，定义将托管配置的Adobe Campaign数据库。

### 启动配置 {#start-configuration}

默认情况下，每 **个实例** ，都会启动stat模块。 当实例在同一台计算机上共同化时，或当实例共享同一IP地址时，将使用单个统计信息服务器：其他人必须禁用。

### 服务器端口的定义 {#definition-of-the-server-port}

默认情况下，统计服务器监听端口7777。 可以在serverConf.xml文件 **中修改此端口** 。 serverConf.xml中可用的所 **有参数都列在本节** 中 [](../../installation/using/the-server-configuration-file.md)。

```
<stat port="1234"/>
```

## MX配置 {#mx-configuration}

### 关于MX规则 {#about-mx-rules}

MX规则（邮件eXchanger）是管理发送服务器和接收服务器之间的通信的规则。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则不再使 **[!UICONTROL MX management]** 用交付吞吐量规则。 增强的MTA使用其自己的MX规则，该规则允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。
>
>有关Adobe Campaign增强型MTA的详细信息，请参阅本 [文档](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。

这些规则会在每天早晨6点（服务器时间）自动重新加载，以便定期提供客户端实例。

根据材料容量和内部策略，ISP将接受预定数量的每小时连接和消息。 ISP系统可以根据IP和发送域的信誉自动修改这些变量。 Adobe Campaign通过其可交付性平台管理ISP提供的150多个特定规则，此外还管理其他域的一个通用规则。

连接的最大数量并不完全取决于MTA使用的公共IP地址的数量。

例如，如果您在MX规则中允许5个连接，并且您配置了2个公共IP，您可能认为不能同时打开10个以上的该域连接。 这不是事实，事实上，最大连接数是指一个路径和一条路径，它是我们的MTA公共IP和客户端MTA的公共IP的组合。

在以下示例中，用户配置了两个公共IP地址，域为yahoo.com。

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

yahoo.com的MX记录告诉我们yahoo.com有3个Mail Exchanger。 要连接对等邮件交换机，MTA将从DNS请求其IP地址。

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

对于此记录，用户可以联系8个对等IP地址。 由于他有2个公共IP地址，因此这为他提供了8 * 2 = 16个组合以连接到yahoo.com邮件服务器。 这些组合中的每一个都称为路径。

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

其中4个IP地址已用于mta5（98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203）。 此记录允许用户使用4个新IP地址。 第三条MX记录也会这样做。

总共有16个远程IP地址。 与我们的2个本地公共IP相结合，我们有32个路径可以到达yahoo.com邮件服务器。

>[!NOTE]
>
>如果2个MX记录引用的IP地址相同，则这个记录将计为一个路径，而不计为两个。

以下是使用MX规则的一些示例：

![](assets/s_ncs_examples_mx_rules.png)

在以下示例中，用户对特定域的每小时限制为10,000条消息，但MTA吞吐量容量高于此限制。

在这种情况下，流量分为12个时段（每小时5分钟），每个时段的实际限制为833条消息。

这些消息将尽快传递。

![](assets/s_ncs_traffic_shaping.png)

### 配置MX管理 {#configuring-mx-management}

MX要遵循的规则在树节点的文 **[!UICONTROL MX management]** 档中定 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 义了。

如果 **[!UICONTROL MX management]** 节点中不存在文档，您可以手动创建它。 操作步骤：

1. 创建一组新的邮件规则。
1. 选择模 **[!UICONTROL MX management]** 式。

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 在字 **段中输入defaultMXRules****[!UICONTROL Internal name]** 。

为了考虑更改，您需要重新启动统计服务器。

要在不重新启动统计信息服务器的情况下重新加载配置，请在承载服务器的计算机上使用以下命令： `nlserver stat -reload`

>[!NOTE]
>
>此命令行优先于nlserver **重新启动**。 它可防止在重启丢失之前收集的统计信息，并避免使用高峰时可能与MX规则中定义的配额相冲突。

### 配置MX规则 {#configuring-mx-rules}

文 **[!UICONTROL MX management]** 档列出所有链接到MX规则的域。

这些规则按顺序应用：应用其MX掩码与目标MX兼容的第一条规则。

每个规则可用的参数如下：

* **[!UICONTROL MX mask]**:应用规则的域。 每个规则都为MX定义了地址掩码。 因此，其名称与此掩码匹配的任何MX都符合条件。 遮罩可以包含“*”和“?” 常规字符。

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

   在这种情况下，将使 `*.google.com` 用MX规则。 正如您所看到的，MX规则掩码不一定与邮件中的域相匹配。 适用于gmail.com电子邮件地址的MX规则将是带有遮罩的规则 `*.google.com`。

* **[!UICONTROL Range of identifiers]**:通过此选项，可以指示应用规则的标识符(publicID)范围。 您可以指定：

   * 数字：该规则将仅适用于此publicId,
   * 数字范围(**number1-number2**):该规则将适用于这两个数字之间的所有publicId。
   >[!NOTE]
   >
   >如果字段为空，则该规则适用于所有标识符。

   公共ID是一个或多个MTA使用的公共IP的内部标识符。 这些ID在MTA服务器中的 **config-instance.xml文件中定义** 。

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**:定义此MX规则的属性范围。 选中此项后，将在实例上所有可用的IP上共享所有参数。 取消选中后，将为每个IP定义MX规则。 最大消息数乘以可用IP数。
* **[!UICONTROL Maximum number of connections]**:到发送方域的并发连接的最大数量。
* **[!UICONTROL Maximum number of messages]**:在连接上可发送的最大消息数。 当消息超过此数时，将关闭连接并打开新连接。
* **[!UICONTROL Messages per hour]**:发送方域在一小时内可发送的消息的最大数量。
* **[!UICONTROL Connection time out]**:用于连接到域的时间阈值。

   >[!NOTE]
   >
   >Windows可以在此阈 **值之前发出超时** ，这取决于您的Windows版本。

* **[!UICONTROL Timeout Data]**:发送消息内容（SMTP协议的DATA部分）后的最长等待时间。
* **[!UICONTROL Timeout]**:与SMTP服务器进行其他交换的最长等待时间。
* **[!UICONTROL TLS]**:TLS协议允许您加密电子邮件发送，可以选择性地启用。 对于每个MX蒙版，都有以下选项可用：

   * **[!UICONTROL Default configuration]**:这是在应用的serverConf.xml配置文件中指定的常规配置。

      >[!CAUTION]
      >
      >不建议修改默认配置。

   * **[!UICONTROL Disabled]** :系统发送消息时不加密。
   * **[!UICONTROL Opportunistic]** :如果接收服务器(SMTP)可以生成TLS协议，则消息传送将被加密。

配置示例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### 管理电子邮件格式 {#managing-email-formats}

您可以定义已发送消息的格式，以便显示的内容会根据每个收件人地址的域自动调整。

为此，请转到文档 **[!UICONTROL Management of email formats]** ，该文档位于 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** >中 **[!UICONTROL Mail rule sets]**。

本文档包含与Adobe Campaign管理的日文格式相对应的所有预定义域的列表。 For more information, refer to [this document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

MIME结 **构** （多用途Internet邮件扩展）参数允许您定义将发送给不同邮件客户端的邮件结构。 有三个可用选项：

* **多部分**:消息以文本或HTML格式发送。 如果不接受HTML格式，消息仍可以以文本格式显示。

   默认情况下，多部分结构是多 **部分／替代结构**，但在将图像添加到消息中时，它会自 **动变为多部分／相关结构** 。 某些提供商预期 **默认采用多部分／相关** ，即使未附加图像， **[!UICONTROL Force multipart/related]** 此选项也会强制采用此格式。

* **HTML**:将发送仅HTML消息。 如果不接受HTML格式，则不显示消息。
* **文本**:将发送仅文本格式的消息。 文本格式消息的优势在于其非常小。

如果启 **[!UICONTROL Image inclusion]** 用此选项，则这些选项会直接显示在电子邮件正文中。 随后将上传图像，URL链接将替换为其内容。

此选项在日本市场中尤其用于 **Deco邮件**、 **Decore邮件** 或装 **饰邮件**。 有关详细信息，请查阅 [本文档](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

>[!CAUTION]
>
>在电子邮件中插入图像会大大增加其大小。

## 交付服务器配置 {#delivery-server-configuration}

### 时钟同步 {#clock-synchronization}

组成Adobe Campaign平台（包括数据库）的所有服务器的时钟必须同步，并且其系统设置为同一时区。

### 统计服务器的坐标 {#coordinates-of-the-statistics-server}

必须在mta中提供统计服务器的地 **址**。

通过 **配置的mta** 元素的statServerAddress属性 **** ，可以指定要使用的端口的地址和编号。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

要在同一台计算机上使用统计信息服务器，必须至少输入具有localhost值的该计算机 **的名称** :

```
 <mta statServerAddress="localhost">
```

>[!CAUTION]
>
>如果未填充此字段，则 **mta** 将不启动。

### 要使用的IP地址列表 {#list-of-ip-addresses-to-use}

有关流量管理的配置位于配 **置文件的mta/child/smtp** 元素中。

对于每 **个IPAfinity元素** ，您需要声明可用于计算机的IP地址。

例如：

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

* **publicId**:当NAT路由器后面的几个Adobe Campaign mta共享IP地址时，此 **信息很** 有用。 统计服务器使用该标识符来存储该起始点和目标服务器之间的连接和发送统计信息。
* **粗细**:允许您定义地址的相对使用频率。 默认情况下，所有地址的粗细均等于1。

>[!NOTE]
>
>在serverConf.xml文件中，您需要验证一个IP是否对应于具有唯一标识符(public_id)的单个主机。 它无法映射到多个主机，这可能导致交付限制问题。

在上一个示例中，在正常情况下，地址将按如下方式分发：

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

例如，如果第一个地址不能用于给定的MX，则消息将按如下方式发送：

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**:允许您为属于特定域的电子邮件保留此IP地址。 这是一个蒙版列表，它可以包含一个或多个通配符(&#39;*&#39;)。 如果未指定属性，则所有域都可以使用此IP地址。

   示例： **includeDomains=&quot;wanadoo.com,orange.com,yahoo.*&quot;**

* **excludeDomains**:不包括此IP地址的域列表。 此过滤器在includeDomains过滤器之 **后应用** 。

   ![](assets/s_ncs_install_mta_ips.png)

## 电子邮件发送优化 {#email-sending-optimization}

Adobe Campaign邮件的内部架构 **对** “优化电子邮件投放”的配置有影响。 以下是有关改进送货的一些提示。

### 调整maxWaitingMessages参数 {#adjust-the-maxwaitingmessages-parameter}

maxWaitingMessages **参数指示由匹配字段预先准备的最大** 消息数 ****。 消息仅在发送或放弃后才会从此列表中删除。

如果消息未按域排序，则此参数非常重要，尤其重要。

达到 **maxWorkingSetMb** (256)阈值后，传送服务器将停止发送消息。 性能将显着下降，直到 **匹配** 再次启动。 要避免此问题，您可以增加 **maxWorkingSetMb** 参数的阈值，或者减少 **maxWaitingMessages参数的阈值** 。

maxWorkingSetMb **(maxWorkingSetMb** )参数是通过经验计算的，方法是将消息的最大数乘以平均消息大小，再乘以结果2.5。例如，如果消息的平均大小为50 kB，且 **maxWaitingMessages** 参数等于1,000，则使用的内存将平均为125 MB。

### 调整字段数 {#adjust-the-number-of-mtachild}

子代的数量不应超过计算机中的处理器数量(约为1000次会议)。 我们建议您不要超过8英 **镑**。 然后，您可以增加每个子代的消 **息数** (**maxMsgPerChild**)，以实现足够的寿命。
