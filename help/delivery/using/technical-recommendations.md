---
solution: Campaign Classic
product: campaign
title: 改进Adobe Campaign Classic交付能力的技术建议
description: 探索可用于提高Adobe Campaign Classic的交付率的技术、配置和工具。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '2427'
ht-degree: 0%

---


# 技术建议{#technical-recommendations}

下面列出了几种可用于提高交付率的技术、配置和工具。

## 配置{#configuration}

### 反向DNS {#reverse-dns}

Adobe Campaign检查是否为IP地址提供反向DNS，并且这正确地指向IP。

网络配置中的一个重要点是确保为每个传出消息的IP地址定义正确的反向DNS。 这意味着对于给定的IP地址，存在一个反向DNS记录（PTR记录），该记录具有匹配的DNS（A记录），该记录循环回初始IP地址。

反向DNS的域选择在与某些ISP打交道时会产生影响。 特别是AOL，它只接受与反向DNS位于同一域中的地址的反馈循环（请参见[反馈循环](#feedback-loop)）。

工具可用于验证域的配置：[https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx)。

### MX规则{#mx-rules}

MX规则（邮件eXchanger）是管理发送服务器与接收服务器之间通信的规则。

更准确地说，它们用于控制活动MTA（邮件传输代理）向每个电子邮件域或ISP（如hotmail.com、comcast.net）发送电子邮件的速度。 这些规则通常基于ISP发布的限制（例如，每个SMTP连接不包含20条以上的邮件）。

有关MX管理的详细信息，请参阅[本节](../../installation/using/email-deliverability.md#mx-configuration)。

### TLS {#tls}

TLS（传输层安全性）是一种加密协议，可用于保护两个电子邮件服务器之间的连接并保护电子邮件内容不被任何收件人读取。

## 身份验证{#authentication}

### SPF {#spf}

SPF（发送者策略框架）是电子邮件身份验证标准，允许域的所有者指定允许哪些电子邮件服务器代表该域发送电子邮件。 此标准使用电子邮件的“返回路径”标题（也称为“信封发件人”地址）中的域。

工具可用于验证SPF记录：[https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

SPF是一种技术，在某种程度上，它使您能够确保电子邮件中使用的域名不伪造。 当从域接收消息时，将查询域的DNS服务器。 响应是一个简短记录（SPF记录），它详细列出了哪些服务器有权从此域发送电子邮件。 如果我们假定只有域的所有者有权更改此记录，我们可以考虑此技术不允许伪造发送者地址，至少不允许伪造“@”右侧的部分。

在最后的[RFC 4408规范](https://www.rfc-editor.org/info/rfc4408)中，消息的两个元素用于确定被视为发送方的域：由SMTP &quot;HELO&quot;（或&quot;EHLO&quot;）命令指定的域和由&quot;Return-Path&quot;（或&quot;MAIL FROM&quot;）头的地址指定的域，也是弹回地址。 不同的考虑使得只考虑其中一个值成为可能；我们建议确保两个源都指定同一个域。

检查SPF可评估发送方域的有效性：

* **无**:无法进行评估，
* **中性**:查询的域不启用评估，
* **通过**:域被认为是正版，
* **失败**:域是伪造的，信息应该被拒绝，
* **SoftFail**:域可能是伪造的，但消息不应仅基于此结果而拒绝，
* **TempError**:临时错误停止了评估。消息可以被拒绝，
* **PermError**:域的SPF记录无效。

值得注意的是，在DNS服务器级别所做记录可能需要48小时才能考虑。 此延迟取决于接收服务器的DNS缓存刷新频率。

### DKIM {#dkim}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则DKIM电子邮件身份验证签名由增强的MTA对所有域的所有消息执行。

DKIM（域密钥标识邮件）身份验证是SPF的后继服务器，它使用公钥密码术，允许接收电子邮件服务器验证消息实际上是由其声称其发送的个人或实体发送的，以及消息内容在最初发送（和DKIM“已签名”）和接收之间是否发生了更改。 此标准通常使用“发件人”或“发件人”标题中的域。 为确保DKIM的安全级别，建议使用最佳实践加密大小1024b。 大多数访问提供者不认为低DKIM密钥有效。

DKIM来自DomainKeys, Yahoo! 和Cisco Internet Mail身份验证原则，用于检查发送方域的真实性并保证消息的完整性。

DKIM已替换&#x200B;**DomainKeys**&#x200B;身份验证。

使用DKIM需要一些先决条件：

* **安全性**:加密是DKIM的一个关键元素，确保自2013年春1024b以来DKIM的安全级别是建议加密大小的最佳实践。大多数访问提供者不认为低DKIM密钥有效。
* **声誉**:信誉基于IP和／或域，但不透明的DKIM选择器也是需要考虑的关键元素。选择选择器很重要：避免保留“违约”，因为“违约”可以被任何人使用，因此声誉非常低。 您必须为&#x200B;**保留与客户获取通信**&#x200B;以及身份验证实施不同的选择器。
* **Adobe Campaign选项声明**:在Adobe活动中，DKIM私钥基于DKIM选择器和域。当前无法为具有不同选择器的同一域／子域创建多个私钥。 无法定义平台或电子邮件中的身份验证必须使用哪个选择器域／子域。 该平台可选地选择其中一个私钥，这意味着该身份验证有很高的失败概率。

>[!NOTE]
>
>* 如果您为Adobe Campaign实例配置了DomainKeys，您只需在[域管理规则](../../delivery/using/understanding-delivery-failures.md#domain-management)中选择&#x200B;**dkim**。 否则，请按照与DomainKeys相同的配置步骤（私有／公钥）操作。
>* 对于DKIM是DomainKeys的改进版本，因此不必为同一域同时启用DomainKeys和DKIM。
>* 以下域当前验证DKIM:AOL,Gmail。


### DMARC {#dmarc}

DMARC(基于域的邮件身份验证、报告和符合性)是最新的电子邮件身份验证形式，它依赖SPF和DKIM身份验证来确定电子邮件是否通过或失败。 DMARC在两个非常重要的方面具有独特性和强大性：

* 符合性——它允许发送方指示ISP如何处理未通过身份验证的消息（例如，不接受它）。
* 报告-它向发送方提供详细报告，显示DMARC身份验证失败的所有消息，以及每个用户使用的“发件人”域和IP地址。 这允许公司识别身份验证失败且需要某种类型的“修复”（例如，将IP地址添加到其SPF记录）的合法电子邮件，以及其电子邮件域上的网络钓鱼尝试的来源和流行情况。

DMARC可以利用由[250ok](https://250ok.com/)生成的报告。

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## 反馈循环{#feedback-loop}

反馈循环在ISP级别为用于发送消息的IP地址范围声明给定的电子邮件地址。 ISP将以与弹回消息类似的方式发送到此邮箱，收件人将这些消息作为垃圾邮件报告。 该平台应配置为阻止向已投诉的用户发送未来投放。 即使他们没有使用正确的退出链接，也必须不再与他们联系。 ISP将根据这些投诉在其中添加IP地阻止列表址。 如果投诉率在1%左右，则会阻止IP地址。

目前正在制定一个标准来定义反馈循环消息的格式：[滥用反馈报告格式(ARF)](https://tools.ietf.org/html/rfc6650)。

为实例实现反馈循环需要：

* 专用于实例的邮箱，该邮箱可能是弹回邮箱
* 专用于实例的IP发送地址

在Adobe Campaign中实现简单的反馈循环使用弹回消息功能。 反馈循环邮箱用作弹回邮箱，并定义规则来检测这些邮件。 将邮件报告为垃圾信息的收件人的电子邮件地址添加到隔离列表。

* 在&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;中创建或修改弹回邮件规则&#x200B;**Feedback_loop**，原因为&#x200B;**Recombed**&#x200B;和类型&#x200B;**Hard**。
* 如果邮箱是专门为反馈循环定义的，请定义参数以通过在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中新建一个外部弹回邮件帐户访问该邮箱。

该机制立即开始运作，处理投诉通知。 为确保此规则正常工作，您可以暂时取消激活帐户，以便它们不收集这些邮件，然后手动检查反馈循环邮箱的内容。 在服务器上，执行以下命令：

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

如果强制您对多个实例使用一个反馈循环地址，则必须：

* 复制在任意数量的邮箱上收到的消息，
* 让每个邮箱由一个实例选取，
* 配置实例，以便它们只处理与它们相关的消息：实例信息包含在由Adobe Campaign发送的消息的消息ID头中，因此也位于反馈循环消息中。 只需在实例配置文件中指定&#x200B;**checkInstanceName**&#x200B;参数即可（默认情况下，该实例不进行验证，这可能导致某些地址被错误隔离）:

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Adobe Campaign的可交付性服务管理您对以下ISP的反馈环路服务的订阅:AOL、BlueTie、Comcast、Cox、EarthLink、FastMail、Gmail、Hotmail、HostedEmail、Libero、Mail.ru、MailTrust、OpenSRS、QQ、RoadRunner、Synacor、Telenor、Terra、UniteOnline、USA、XS4所有，雅虎，扬德克斯，佐霍。

## 列表-取消订阅{#list-unsubscribe}

### 关于列表-取消订阅{#about-list-unsubscribe}

必须添加名为&#x200B;**列表-取消订阅**&#x200B;的SMTP头，才能确保最佳的可交付性管理。

此标题可用作“报告为垃圾邮件”图标的替代内容。 它将在电子邮件界面中显示为退订链接。

使用此功能有助于保护您的声誉，反馈将作为退订执行。

>[!NOTE]
>
>此功能可从Build 6831获得。

要使用“列表取消订阅”，您必须输入类似于以下命令行：

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>以上示例基于收件人表。 如果从另一个表执行数据库实现，请确保用正确的信息重述命令行。

以下命令行可用于创建动态&#x200B;**列表-取消订阅**:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail、Outlook.com和Microsoft Outlook支持此方法，并且其界面中直接提供取消订阅按钮。 这种技术降低了投诉率。

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

可以通过以下方式实现&#x200B;**列表-取消订阅**:

* 直接在投放模板中添加命令行——请参见[此部分](#adding-a-command-line-in-a-delivery-template),
* 或者，创建类型规则-请参阅[此部分](#creating-a-typology-rule)。

### 在投放模板{#adding-a-command-line-in-a-delivery-template}中添加命令行

必须在电子邮件SMTP头的其他部分添加命令行。

此添加操作可在每封电子邮件中或在现有投放模板中完成。 您还可以创建包含此功能的新投放模板。

### 创建分类规则{#creating-a-typology-rule}

规则必须包含生成命令行的脚本，并且必须包含在电子邮件标题中。

>[!NOTE]
>
>我们建议创建类型规则:列表取消订阅功能将自动添加到每封电子邮件中。

1. 列表取消订阅：&lt;mailto:unsubscribe@domain.com>

   单击&#x200B;**取消订阅**&#x200B;链接可打开用户的默认电子邮件客户端。 此类型规则必须添加到用于创建电子邮件的类型学中。

1. 列表取消订阅：`<https://domain.com/unsubscribe.jsp>`

   单击&#x200B;**取消订阅**&#x200B;链接会将用户重定向到您的退订表单。

   示例:

   ![](assets/s_tn_del_unsubscribe_param.png)

## 电子邮件优化{#email-optimization}

### SMTP {#smtp}

SMTP（简单邮件传输协议）是电子邮件传输的Internet标准。

未通过规则检查的SMTP错误列在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]**&#x200B;文件夹中。 这些错误消息默认解释为不可到达软错误。 如果要正确限定来自SMTP服务器的反馈，则必须识别最常见的错误，并在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]**&#x200B;中添加相应的规则。 否则，平台将执行不必要的重试(未知用户的情况)，或在给定数量的测试后错误地将某些收件人置于隔离中。

### 专用IP {#dedicated-ips}

Adobe为每位客户提供专用的IP战略，增加IP，以建立信誉并优化投放性能。

## IP 认证 {#ip-certification}

IP认证是一种发送最佳实践项目，有助于确保接收电子邮件时不会被防垃圾邮件过滤器或其他电子邮件拦截系统阻止。

目前有两个提供商优惠IP认证：Return Path和Certified Senders Alliance。

认证发件人会添加到全球邮允许列表箱提供商和电子邮件安全公司使用的电子邮件。 这些商业允许列表过滤器基于一种系统，该系统使发送方能够完全绕过防垃圾邮件，或在他们进入系统时分配增量点。

[Return Path Certification](https://www.validity.com/products/returnpath/certification/)项目优惠了许多优点，包括：

* 在Microsoft、AOL、Yahoo、Gmail、Comcast、Orange、Mail.ru等顶级邮箱提供商的收件箱放置量显着增加
* 在诸如Cloudmark、SpamAssassin和Cisco Ironport等关键过滤器享有良好的声誉和待遇
* 专门负责全天候监控的合规团队，提供安全警报并与您通力合作，解决任何折中
* 邮箱提供商数据提供有关KPI、位置和认证性能的详细信息
* 简化和更快的IP加热，包括在迁移或获取新IP地址时更强的声誉和识别能力

[认证发件人联盟](https://certified-senders.org/certification-process/)认证优惠还有其他好处：

* 符合高质量标准的商业电子邮件发件人的认证
* 改进商业电子邮件的投放和发送能力，以提高收件箱放置率并减少垃圾邮件过滤
* 充分遵守法律标准，防范法律和财务风险
* 通过CSA投诉办公室的早期警告和每日垃圾邮件陷阱报告保护声誉

ISP可免费使用这些服务，ISP的数量可能因而允许列表异。

但是，由于越来越多的ISP根据每个收件箱所有者的行为而不是分析邮件内容本身来构建其防垃圾邮件过滤器，使用IP认证无法保证收件箱的放置甚至投放。
