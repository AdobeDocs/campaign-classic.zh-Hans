---
solution: Campaign Classic
product: campaign
title: SMS 疑难解答
description: 了解有关如何对SMS渠道进行故障诊断的更多信息
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---


# SMS疑难解答{#troubleshooting-sms}

## 不同外部帐户之间的冲突{#external-account-conflict}

如果实例有多个SMS外部帐户，则必须检查问题不是由外部帐户之间的冲突引起的。

Adobe Campaign将外部帐户视为无关实体。

如果您有多个帐户，请按照以下过程隔离导致问题的外部帐户:

1. 禁用所有外部帐户。
1. 启用一个外部帐户。
1. 尝试重现问题。
1. 如果初始问题不总是出现，请在结束前进行合理的尝试。
1. 如果该单个帐户未出现问题，请禁用该帐户，然后在下一个帐户上重新启动到步骤2。

单独检查每个帐户后，可能会出现两种情况：

* **问题出现在一个或多个帐户上**

   在这种情况下，您可以单独对每个帐户应用其他故障排除过程。 最好在诊断帐户时禁用其他帐户，以减少网络流量和日志数。

* **在任何时候只有一个帐户处于活动状态时，问题未出现**

   帐户之间有冲突。 如前所述，Adobe Campaign会单独对待帐户，但提供商会将其视为单个帐户。

   * 您在所有帐户之间使用不同的登录名/密码组合。
您必须联系提供商，以诊断他们身边的潜在冲突。

   * 某些外部帐户共享相同的登录名/口令组合。
提供程序无法判断`BIND PDU`来自哪个外部帐户，因此它们将多个帐户的所有连接视为单个连接。 他们可能在这两个帐户上随机发送了MO和SR，导致问题。
如果提供者支持同一登录名/密码组合的多个短代码，则您必须询问他们将该短代码放在`BIND PDU`中的位置。 请注意，此信息必须放在`BIND PDU`中，而不是放在`SUBMIT_SM`中，因为`BIND PDU`是允许正确路由MO的唯一位置。
请参见上面每种PDU](../../delivery/using/sms-protocol.md#information-pdu)中的[信息部分，了解`BIND PDU`中有哪个字段可用，通常在`address_range`中添加短代码，但这需要提供商的特殊支持。 与他们联系，了解他们期望如何独立路由多个短代码。
Adobe Campaign支持在同一外部帐户上处理多个短代码。

## 一般{#external-account-issues}与外部帐户有关的问题

* 调查连接器最近是否更改过以及更改者(将外部帐户作为组检查)。

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 调查（在/postupgrade目录中）系统是否已升级以及何时
* 调查最近是否升级了影响SMS的任何包(/var/log/dpkg.log)。

## 中间源（托管）{#issue-mid-sourcing}问题

* 如果问题发生在中间源环境上，请确保在中间源服务器上正确创建和更新投放和广泛日志。 如果不是这样，这就不是SMS问题。

* 如果中端服务器上的所有功能都正常工作，且SMS已正确发送，但营销实例未正确更新，则可能会出现中间同步问题。

## 连接到提供程序{#issue-provider}时出现问题

* 如果`BIND PDU`返回非零`command_status`代码，请向提供程序咨询详细信息。

* 检查网络是否已正确配置，以便能够与提供程序建立TCP连接。

* 请求提供者检查他们是否将IP正确添加允许列表到Adobe Campaign实例的。

* 检查&#x200B;**外部帐户**&#x200B;设置。 向提供者询问字段的值。

* 如果连接成功但不稳定，请检查[连接不稳定问题](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection)部分。

* 如果连接问题难以诊断，则网络捕获可以提供信息。 确保网络捕获在出现问题时同时运行，以便对其进行有效分析。 您还应注意出现问题的确切时间。

## 连接{#issues-unstable-connection}不稳定的问题

如果发生以下任一情况，则会认为连接不稳定：

* 连接持续不到1小时。 Adobe Campaign Classic发射器连接因Adobe Campaign Classic MTA的工作方式而异。

* 提供程序发送`UNBIND PDU`s。

* `enquire_link` 超时(在Adobe Campaign端或提供方端)。在这种情况下，您可能会看到`ENQUIRE_LINK_RESP`有非零错误代码。

* 有很多`BIND PDU`s。根据连接的数量，一天内不应超过几个。 每小时超过1个BIND PDU应为警报。

如何修复连接稳定性问题：

* 不稳定的连接很少是根本原因，它通常是另一个导致断开连接的问题的结果。 找到根本原因是当务之急。

* 启用详细的SMPP跟踪。 您需要他们查看连接重新启动时发生的情况。

* 如果提供程序发送`BIND PDU`s，则可能出错。 询问您的提供商发送`UNBING`的原因。

* 有时，捕获网络是查看连接关闭情况的唯一方法。

* 如果提供程序通过发送`TCP FIN`或`TCP RST packet`关闭连接，请向提供程序询问详细信息。

* 如果提供程序在发送带有错误代码的清理错误（如`DELIVER_SM_RESP`）后关闭连接，则它们必须修复其连接器，否则将阻止其他类型的消息传输，并触发MTA限制。 在收发信机模式中，关闭连接会影响MT和SR，这一点尤其重要。

## 发送MT（发送给最终用户的常规SMS）时的问题{#issue-MT}

* 检查连接是否稳定。 除Adobe Campaign Classic上的发射器外，SMPP连接应保持至少1小时不间断。 请参阅[不稳定连接问题](../../delivery/using/sms-protocol.md#issues-unstable-connection)一节。

* 如果重新启动MTA使发送MT在一小段时间内再次工作，则可能由于连接不稳定而出现限制。 请参阅[不稳定连接问题](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection)一节。

* 检查广泛日志是否存在，并且状态正确且日期正确。 否则，可能是投放或投放准备问题。

* 检查MTA是否实际处理消息。 如果不是这样，这可能不是SMS问题。

* 检查SMS连接器是否实际与提供商的设备绑定。 请求提供者提供反馈，以确保所有系统通信正常。 有关绑定过程的信息，请参见`BIND_TRANSMITTER`和`BIND_TRANSCEIVER PDU`。 您可能需要启用SMPP跟踪以进行正确的故障排除。

* 启用SMPP跟踪后，检查`SUBMIT_SM PDU`是否包含正确的信息。

* 检查提供程序是否使用`SUBMIT_SM_RESP PDU`以“OK”值（代码0）做出响应。 确保PDU具有合理的延迟：任何超过1秒的内容必须与提供商讨论，它通常在100毫秒内到达。

* 如果所有这些步骤都有效，您可以确信问题出在提供方。 他们必须在自己的平台上进行故障排除。

* 如果它有效，但吞吐量不一致，请尝试调整发送窗口并降低MT吞吐量。 您需要与提供商合作来调整它。 Adobe Campaign可以非常快地发送消息，因此在提供商的设备上可能会出现性能问题。

## 复制MT（同一SMS在一行中多次发送）{#duplicated-MT}

重复通常由重试引起。 重试消息时有重复是正常的，您应该尝试删除重试的根本原因。

* 如果您看到重复分别发送了60秒，那么在提供方方面可能出现问题，他们无法足够快地发送`SUBMIT_SM_RESP`。

* 如果看到许多`BIND/UNBIND`，则连接不稳定。 在尝试解决重复消息问题之前，请参见[不稳定连接问题](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection)部分以了解解决方案。

在出现重试时降低重复量：

* 降低发送窗口。 发送窗口应足够大，足以覆盖`SUBMIT_SM_RESP`延迟。 其值表示在窗口已满时发生错误时可以复制的最大消息数。

## 处理SR(投放收据){#issue-process-SR}时的问题

* 您需要启用SMPP跟踪以执行任何类型的SR故障排除。

* 检查`DELIVER_SM PDU`是否来自提供程序，并且其格式是否正确。

* 及时检查Adobe Campaign以成功`DELIVER_SM_RESP PDU`回复。 在Adobe Campaign Classic上，这保证SR已插入`providerMsgId`表中，以便由SMS进程延迟处理。

如果`DELIVER_SM PDU`未成功确认，则应检查以下内容：

* 检查与&#x200B;**外部帐户**&#x200B;中的id提取和错误处理相关的正则表达式。 您可能需要根据`DELIVER_SM PDU`的内容验证它们。

* 检查是否在`broadLogMsg`表中正确设置了错误。

如果`DELIVER_SM PDU`已由Adobe Campaign Classic扩展SMPP连接器确认，但broadLog未正确更新，请检查[匹配MT、SR和broadlog条目](../../delivery/using/sms-protocol.md#matching-mt)部分中描述的ID协调过程。

如果修复了所有内容，但某些无效SR仍在提供程序的缓冲区中，则可以使用“无效ID确认计数”选项跳过它们。 在缓冲区清理后，应尽快谨慎地使用并重置为0。

## 处理MO（和黑名单/自动回复）{#issue-process-MO}时的问题

* 在测试期间启用SMPP跟踪。 如果不启用TLS，则应在对MO进行故障诊断时执行网络捕获，以检查PDU是否包含正确的信息并且格式正确。

* 在捕获网络流量或分析SMPP跟踪时，如果配置了回复，请确保捕获与MO及其回复MT的整个对话。

* 如果跟踪中未显示MO(`DELIVER_SM PDU`)，则问题出在提供方。 他们必须在自己的平台上进行故障排除。

* 如果出现`DELIVER_SM PDU`，请检查Adobe Campaign是否确认它是否成功`DELIVER_SM_RESP PDU`（代码0）。 此RESP保证所有处理逻辑都已由Adobe Campaign应用(自动回复和允许/阻止列表)。 如果不是，请在SMS进程日志中搜索错误消息。

* 如果启用了自动回复，请检查是否已将`SUBMIT_SM`发送给提供程序。 否则，保证在SMS进程日志中找到错误消息。

* 如果在跟踪中找到包含回复的`SUBMIT_SM MT PDU`，但SMS未到达移动电话，则必须与提供商联系，以获得故障排除的帮助。

## 投放准备过程中的问题不会排除隔离收件人（由自动回复功能隔离）{#issue-delivery-preparation}

* 检查隔离表和投放日志中的电话号码格式是否完全相同。 如果没有，请参阅此[部分](../../delivery/using/sms-protocol.md#automatic-reply)（如果您对国际电话号码格式的加号前缀有问题）。

* 检查短码。 如果收件人的短代码与外部帐户中定义的相同或为空（空=任何短代码），则可能会发生排除。 如果整个Adobe Campaign实例只使用一个短代码，则更容易将所有&#x200B;**短代码**&#x200B;字段留空。

## 编码问题{#encoding-issues}

**第1步：与提供商联系**

联系他们，看看他们有什么问题。 他们应该能够告诉你问题是在他们这边还是在Adobe Campaign那边。 如果问题出在Adobe Campaign中，他们应该能够告诉您确切的字段不正确。

**第2步：了解您的消息**

Unicode允许许多类似字符的变体，而Adobe Campaign无法处理所有变体。

最常见的问题源于从字处理器复制粘贴，它将常见字符更改为排版正确的版本：空格更改为不中断空格，多次引号更改为开号和闭号，减号更改为各种连字符等。

测试时不要复制粘贴消息，请始终在界面中直接键入消息。

使用十六进制，您可以区分相似字符之间的差异。 小写L、大写I、O、0、所有不同类型的引号、非拉丁编码、甚至不同类型的空格看起来都一样，甚至根本不显示。

要将Unicode转换为十六进制，可以使用联机工具，如[Unicode代码转换器](https://r12a.github.io/app-conversion/)网站。 键入文本，确保没有PII（如电话号码），然后单击&#x200B;**转换**。 您将在底部（UTF-32区域）看到十六进制值。

打开有关编码问题的票证时，无论是提供商还是[Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，始终包含您键入的内容和所看到内容的十六进制版本。

**第3步：了解您应发送的内容**

确定要使用的编码，并联机搜索字符表。 检查您要发送的字符是否实际在目标代码页中可用。 检查`data_coding`字段是否正确，是否与您和提供者的预期匹配。

**第4步：了解您实际发送的**

您需要连接器的调试输出才能准确查看您发送给提供程序的字节。 编码问题出现在`SUBMIT_SM PDU`s中，因此请务必捕获它们。 发送在日志中易于查找的非常独特的消息。

测试时发送不同种类的特殊字符。 例如，GSM7编码包含扩展字符，这些字符的十六进制格式非常不同，它们易于识别，因为它们不显示在任何其他编码中。

## 在与SMS问题{#element-include}通信时要包含的元素

无论您在SMS问题上寻求帮助，还是向Adobe Campaign打开支持票证，向SMS提供商寻求帮助，或者就此问题进行任何通信，您都需要包含以下信息，以确保其正确合格。 正确确定的问题是更快地解决问题的关键。

* **出现问题时** 启用详细SMPP消息。没有这些，大多数短信问题都是无法解决的。

* 如果问题与SMS通信相关，请首先与提供商联系。 他们的平台最适合实时有效地诊断短信流量问题。

* 对问题进行简短但事实的描述。

* 包括预期结果的描述。

* 包括来自提供商的反馈。

* 包括相关日志和/或网络捕获。 执行捕获时，请确保在捕获期间重现问题。

* 如果包含日志、跟踪或捕获，则当出现问题时，请准确定位文件中的确切位置。

* 如果您引用消息、PDU或日志，请清楚地声明其时间戳，以便更容易查找。

* 尝试在测试环境中重现问题。 如果不确定设置，请在测试环境试用它，然后使用SMPP跟踪检查结果。 通常，报告在测试环境上复制的问题比直接报告生产环境上的问题要好。

* 包括平台上所做的任何更改或调整。 此外，请包括提供者可能已在自己这边所做的任何更改。

### 网络捕获{#network-capture}

网络捕获并不总是需要的，通常冗余的SMPP消息已足够。 以下是帮助您确定是否需要网络捕获的一些准则：

* 连接问题，但详细消息不显示任何`BIND_RESP PDU`。

* 无错误消息的未解释断开连接，即连接器在检测到低级协议错误时的常见行为。

* 提供程序抱怨解除绑定/断开连接进程。

* 可选TLV字段中的编码问题。

* 流量可能混合在不同的连接之间。

在所有其他情况下，请尝试先分析详细的SMPP消息，并仅在详细日志中缺少信息时请求网络捕获。

在某些情况下，不需要捕获网络通信。 以下是最常见的情况：

* 已启用TLS:根据定义，TLS通信已加密，因此无法捕获。

* 性能问题：日志包含跟踪性能问题所需的所有信息。

* 计时问题（`retry timing`、`enquire_link`期间、吞吐量限制等）

* SR分析和处理：详细日志提供了更多上下文和更好的演示文稿。

* MO处理(自动回复、隔离)。

* 不涉及实际SMPP流量的错误：投放准备、消息中心API问题、工作流问题等。

## 启用SMPP跟踪{#enabling-smpp-traces}

新连接器支持通过跟踪进行扩展日志记录：SMPP。 跟踪是在MTA日志中输出的，而不是在标准输出中输出的。

**每外部帐户启用（首选方法）**

1. 在&#x200B;**外部帐户**&#x200B;中，选中&#x200B;**在日志文件**&#x200B;中启用详细的SMPP跟踪。
1. 等待10分钟，让服务器重新加载外部帐户。

现在应该是活动的。

**在配置中启用**

在`config-instance.xml`文件中，设置以下参数：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 检查容器{#open-connections}上打开的连接数

要检查容器上打开的连接数，可以使用以下命令：

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

这将列表为给定端口打开的连接数。 这里我们使用3600端口。

结果应如下：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4个已打开的sms进程连接，每mta儿童2个，5个子级。
