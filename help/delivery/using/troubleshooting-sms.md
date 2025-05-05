---
product: campaign
title: 短信故障排除
description: 详细了解如何对短信渠道进行故障排除
feature: SMS, Troubleshooting
role: User
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: f660dcbb111e73f12737d96ebf9be2aeccbca8ee
workflow-type: tm+mt
source-wordcount: '3044'
ht-degree: 0%

---

# 短信疑难解答 {#troubleshooting-sms}

## 不同外部帐户之间的冲突 {#external-account-conflict}

如果实例具有多个SMS外部帐户，则必须检查问题是否不是由外部帐户之间的冲突引起的。

Adobe Campaign将外部帐户视为不相关的实体。

如果您有多个帐户，请按照以下步骤隔离导致问题的外部帐户：

1. 禁用所有外部帐户。
1. 启用一个外部帐户。
1. 尝试重现问题。
1. 如果初始问题并非总是出现，请在结束之前进行合理数量的尝试。
1. 如果该单个帐户未出现问题，请禁用该帐户，然后在下一个帐户上重新启动到步骤2。

分别检查每个帐户后，可能会出现以下两种情况：

* **问题出现在一个或多个帐户上**

  在这种情况下，您可以对每个帐户单独应用其他故障排除过程。 最好在诊断帐户时禁用其他帐户，以减少网络通信量和日志数量。

* **在任何时候只有一个帐户处于活动状态时，问题未出现**

  帐户之间存在冲突。 如前所述，Adobe Campaign单独处理帐户，但提供商可能会将其视为单个帐户。

   * 您在所有帐户之间使用不同的登录/密码组合。
您必须联系提供程序以诊断其一方的潜在冲突。

   * 某些外部帐户共享相同的登录名/密码组合。提供商无法判断来自哪个外部帐户 `BIND PDU` ，因此他们将来自多个帐户的所有连接视为单个帐户。 他们可能通过这两个帐户随机路由 MO 和 SR，从而导致问题。如果提供商支持同一登录名/密码组合的多个短代码，则必须询问他们将该短代码 `BIND PDU`放在 中的什么位置。 请注意，这条信息必须放在 中 `BIND PDU`，而不是 `SUBMIT_SM`放在 中，因为 是唯一 `BIND PDU` 允许正确路由 MO 的地方。请参阅上面各种PDU[&#128279;](sms-protocol.md#information-pdu)部分中的信息以了解`BIND PDU`中可用的字段，通常是在`address_range`中添加短代码，但这需要提供程序的特别支持。 联系他们，了解他们希望如何独立路由多个短代码。
Adobe Campaign支持在同一外部帐户上处理多个短代码。

## 外部帐户一般问题 {#external-account-issues}

* 调查连接器最近是否已更改以及由谁更改（将外部帐户作为一个组检查）。

  ```
  select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
  
  (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
  
  (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
  
  N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
  
  from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
  ```

* 调查（在 /postupgrade 目录中）系统是否已升级以及何时升级
* 调查最近是否有任何影响 SMS 的程序包可能已升级 （/var/log/dpkg.log）。

## 中源问题（托管）{#issue-mid-sourcing}

* 如果问题发生在中间源环境中，请确保在中间源服务器上正确创建和更新传递日志和广泛日志。 如果不是这种情况，这不是短信问题。

* 如果所有功能在中间服务器上都有效，并且短信已正确发送，但营销实例未正确更新，则您可能会遇到中间同步问题。

## 连接到提供商时出现问题 {#issue-provider}

* 如果`BIND PDU`返回非零`command_status`代码，请向提供程序询问详细信息。

* 检查网络是否已正确配置，以便能够与提供商建立TCP连接。

* 要求提供商检查他们是否正确将IP添加到Adobe Campaign实例的允许列表。

* 检查&#x200B;**外部帐户**&#x200B;设置。 询问提供商字段的值。

* 如果连接成功但不稳定，请检查连接不稳定的[问题](troubleshooting-sms.md#issues-unstable-connection)部分。

* 如果连接问题难以诊断，则网络捕获可以提供信息。 确保网络捕获在问题出现时同时运行，以便对其进行有效分析。 您还应记下问题出现的确切时间。

## 连接不稳定问题 {#issues-unstable-connection}

如果出现以下任一情况，则认为连接不稳定：

* 连接持续不到1小时。 由于Adobe Campaign Classic MTA的工作方式，Adobe Campaign Classic发射器连接是一个例外。

* 提供程序发送`UNBIND PDU`。

* `enquire_link`在Adobe Campaign端或提供商端超时。 在这种情况下，您可能会看到带有非零错误代码的`ENQUIRE_LINK_RESP`。

* 有许多`BIND PDU`。根据连接数量，一天中的连接不应超过几个。 每小时超过1个BIND PDU应发出警报。

如何修复连接稳定性问题：

* 不稳定的连接很少是根本原因，它通常是另一个问题触发断开的结果。 首先要找出根本原因。

* 启用详细的SMPP跟踪。 您需要他们查看连接重新启动时发生的操作。

* 如果提供程序发送`BIND PDU`，则可能有错误。 询问您的提供商发送`UNBING`的原因。

* 进行网络捕获有时是查看连接如何关闭的唯一方法。

* 如果提供程序通过发送`TCP FIN`或`TCP RST packet`来关闭连接，请向你的提供程序询问详细信息。

* 如果提供程序在发送带有错误代码的`DELIVER_SM_RESP`等干净错误后关闭连接，则提供程序必须修复其连接器，否则将阻止传输其他类型的消息并触发MTA限制。 在收发器模式下，这一点尤其重要，因为关闭连接会同时影响MT和SR。

## 发送MT（发送给最终用户的常规短信）时出现问题{#issue-MT}

* 检查连接是否稳定。 除Adobe Campaign Classic上的发射器外，SMPP连接应持续保持至少1小时。 查看部分[连接不稳定的问题](sms-protocol.md#issues-unstable-connection)。

* 如果重新启动MTA后一小段时间内仍可再次发送MT，则连接不稳定可能会造成限制。 查看部分[连接不稳定的问题](troubleshooting-sms.md#issues-unstable-connection)。

* 检查广泛日志是否存在并且状态正确，日期正确。 如果不是，则可能是投放或投放准备问题。

* 检查MTA是否实际处理消息。 如果不是这种情况，则可能不是短信问题。

* 检查SMS连接器是否实际与提供商的设备绑定。 请向提供商征求反馈，以确保所有系统都可正常通信。 有关绑定过程的信息，请参见`BIND_TRANSMITTER`和`BIND_TRANSCEIVER PDU`。 您可能需要启用SMPP跟踪才能正确进行故障排除。

* 启用SMPP跟踪后，检查`SUBMIT_SM PDU`是否包含正确的信息。

* 检查提供程序是否使用“OK”值（代码0）通过`SUBMIT_SM_RESP PDU`做出响应。 确保PDU以合理的延迟到达：任何大于1秒的延迟都必须与提供商讨论，通常在100毫秒内到达。

* 如果所有这些步骤都有效，您可以确信问题出在提供商方面。 他们必须在平台上执行故障排除。

* 如果它可以工作，但吞吐量不一致，请尝试调整发送窗口并降低MT吞吐量。 您需要与提供商合作才能调整此设置。 Adobe Campaign可以非常快速地发送消息，因此提供商的设备可能会出现性能问题。

## MT重复（同一短信连续多次发送）{#duplicated-MT}

重复项通常由重试引起。 重试消息时通常会出现重复项，您应该尝试删除重试的根本原因。

* 如果您看到重复项发送的时间刚好相隔60秒，则可能是提供商方的问题，他们发送`SUBMIT_SM_RESP`的速度不够快。

* 如果您看到许多`BIND/UNBIND`，则表示您的连接不稳定。 在尝试解决重复消息问题之前，请查看不稳定的连接的[问题](troubleshooting-sms.md#issues-unstable-connection)部分以获取解决方案。

在重试时减少重复项数量：

* 降低发送窗口。 发送窗口应足够大，以涵盖`SUBMIT_SM_RESP`延迟。 其值表示在窗口已满时发生错误时可以复制的最大消息数。

## 处理 SR（交货收据）时出现问题 {#issue-process-SR}

* 您需要启用 SMPP 跟踪才能执行任何类型的 SR 故障排除。

* 检查`DELIVER_SM PDU`是否来自提供程序并且格式正确。

* 检查Adobe Campaign是否及时回复并成功回复了`DELIVER_SM_RESP PDU`。 在Adobe Campaign Classic上，这可保证SR已插入`providerMsgId`表，以供SMS进程延迟处理。

`DELIVER_SM PDU`如果未成功确认，则应检查以下内容：

* 检查与外部帐户&#x200B;**中的** id 提取和错误处理相关的正则表达式。您可能需要根据 的内容 `DELIVER_SM PDU`验证它们。

* 检查表中是否正确预配 `broadLogMsg` 了错误。

如果 已通过 Adobe Campaign Classic 扩展 SMPP 连接器确认，`DELIVER_SM PDU`但 broadLog 未正确更新，请检查匹配 MT、SR 和 broadlog 条目[&#128279;](sms-protocol.md#matching-mt)部分中描述的 ID 协调过程。

如果您修复了所有内容，但一些无效的 SR 仍在提供程序的缓冲区中，则可以使用“无效的 ID 确认计数”选项跳过它们。 应谨慎使用，并在缓冲区清理后尽快重置为 0。

## 处理MO（和黑名单/自动回复）时的问题{#issue-process-MO}

* 在测试期间启用SMPP跟踪。 如果不启用TLS，则在对移动问题进行故障排除时应该进行网络捕获，以检查PDU是否包含正确的信息以及格式是否正确。

* 在捕获网络流量或分析SMPP跟踪时，请确保捕获与MO的整个会话及其回复MT（如果配置了回复）。

* 如果MO (`DELIVER_SM PDU`)未出现在跟踪中，则问题出现在提供程序端。 他们必须在平台上执行故障排除。

* 如果出现`DELIVER_SM PDU`，请检查Adobe Campaign是否确认它并成功`DELIVER_SM_RESP PDU`（代码0）。 此RESP可确保Adobe Campaign列入阻止列表已应用所有处理逻辑（自动回复和允许/）。 如果不是这种情况，请在短信进程日志中搜索错误消息。

* 如果启用了自动回复，请检查`SUBMIT_SM`是否已发送给提供程序。 如果没有，则保证在短信进程日志中找到错误消息。

* 如果在跟踪中找到包含回复的`SUBMIT_SM MT PDU`，但手机未收到短信，则您必须联系提供商以获得故障排除方面的帮助。

## 投放准备期间出现的问题未排除被隔离的收件人（被自动回复功能隔离） {#issue-delivery-preparation}

* 检查隔离表和投放日志中的电话号码格式是否完全相同。 如果不是，请参阅此[部分](sms-protocol.md#automatic-reply)（如果您遇到国际电话号码格式的加号前缀问题）。

* 检查短代码。 如果收件人的短代码与外部帐户中定义的短代码相同，或者为空（空=任何短代码），则可能会发生排除。 如果整个Adobe Campaign实例只使用一个短代码，则更容易将所有&#x200B;**短代码**&#x200B;字段留空。

## 编码问题 {#encoding-issues}

**步骤1：联系提供程序**

联系他们，看看他们有什么问题。 他们应该能够告诉你问题是在他们这边还是Adobe Campaign那边。 如果问题出在Adobe Campaign中，他们应该能够确切地告诉您哪个字段不正确。

**步骤2：了解消息内容**

Unicode允许使用多种变体来显示相似字符，而Adobe Campaign无法处理所有这些字符。

最常见的问题源于文字处理器中的复制粘贴，它将常用字符更改为正确排版版本：空格更改为不换行空格，双引号更改为开引号和闭引号，减号更改为各种连字符等。

测试时不复制粘贴消息，始终在界面中直接键入消息。

使用十六进制，您可以区分相似字符之间的差异。 小写L、大写I、O、0，所有不同类型的引号、非拉丁语编码甚至不同类型的空格可能看起来都相同，甚至根本不会显示。

若要将unicode转换为十六进制，可以使用联机工具，如[Unicode代码转换器](https://r12a.github.io/app-conversion/)网站。 键入您的文本，确保没有电话号码等PII，然后单击&#x200B;**转换**。 您将在底部（UTF-32区域）看到十六进制值。

在打开有关编码问题的票证时，无论是否向提供商或[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)发送票证，都始终包含您所键入内容和所看到内容的十六进制版本。

**步骤3：了解应发送哪些内容**

确定要使用的编码，并联机搜索其字符表。 检查您打算发送的字符是否确实在目标代码页中可用。 请检查`data_coding`字段是否正确，它是否与您和提供商期望的内容匹配。

**步骤4：了解您实际发送的内容**

您需要连接器的调试输出，才能准确地查看您发送到提供程序的字节。 编码问题出现在`SUBMIT_SM PDU`中，因此请务必捕获它们。 发送非常不同的消息，这些消息在日志中很容易找到。

测试时发送各种特殊字符。 例如，GSM7编码具有以十六进制形式非常不同的扩展字符，它们很容易被发现，因为它们未出现在任何其他编码中。

## 通信短信问题时要包含的元素 {#element-include}

无论您是在短信问题上寻求帮助，还是向Adobe Campaign、短信提供商打开支持票证，或者就问题寻求任何类型的通信，都需要包含以下信息以确保您能够正确获取所需信息。 适当确定问题对于更快地解决问题至关重要。

* 出现问题时&#x200B;**启用详细的SMPP消息**。 如果没有它，大多数SMS问题都无法解决。

* 如果问题与短信流量相关，请首先与提供商联系。 他们的平台最适合实时高效诊断短信流量问题。

* 包括对问题的简短但实事求是的描述。

* 包括预期结果的描述。

* 包含来自提供商的反馈。

* 包括相关日志和/或网络捕获。 执行捕获时，请确保在捕获期间重现问题。

* 如果包含日志、跟踪或捕获，则当问题出现时，可以精确定位文件中确切的位置。

* 如果您引用消息、PDU或日志，请清楚地声明其时间戳以使其更易于查找。

* 尝试在测试环境中重现问题。 如果不确定设置，请在测试环境中尝试此设置，并使用SMPP跟踪检查结果。 报告在测试环境中复制的问题通常比直接报告生产环境中的问题要好。

* 包括在平台上所做的任何更改或调整。 此外，还包括提供商可能对他们所做的任何更改。

### 网络捕获 {#network-capture}

并不总是需要网络捕获，通常冗长的 SMPP 消息就足够了。 下面是一些准则，可帮助您确定是否需要网络捕获：

* 连接有问题，但详细消息未显示任何`BIND_RESP PDU`。

* 无法解释的断开连接没有错误信息，这是连接器检测到低级协议错误时的常规行为。

* 提供程序抱怨解除bind/断开连接的过程。

* 可选 TLV 字段中的编码问题。

* 怀疑不同连接之间混合了流量。

在所有其他情况下，请尝试先分析详细的SMPP消息，仅当详细日志中缺少信息时请求网络捕获。

在某些情况下，不需要捕获网络流量。 以下是最常见的情况：

* TLS已启用：根据定义，TLS流量会被加密，因此无法捕获该流量。

* 性能问题：日志包含跟踪性能问题所需的所有信息。

* 计时问题（`retry timing`、`enquire_link`周期、吞吐量上限等）

* SR解析和处理：详细日志可提供更多的上下文和更好的呈现。

* MO处理（自动回复、隔离）。

* 不涉及实际SMPP流量的错误：投放准备、消息中心API问题、工作流问题等。

## 启用SMPP跟踪 {#enabling-smpp-traces}

新连接器支持通过跟踪的扩展日志记录： SMPP。 跟踪在MTA日志中输出，而不是在标准输出中输出。

**为每个外部帐户启用（首选方法）**

1. 在&#x200B;**外部帐户**&#x200B;中，选中&#x200B;**在日志文件**&#x200B;中启用详细的SMPP跟踪。
1. 等待10分钟，让服务器重新加载外部帐户。

它现在应该处于活动状态。

**正在配置中启用**

在`config-instance.xml`文件中，设置以下参数：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 检查容器上打开的连接的数量 {#open-connections}

要检查容器上打开的连接的数量，可以使用此命令：

```
(for pid in $(ss -neopts  | sed -n 's/^.*:3600[ \t].*users:(([0-9A-Za-z"]*,pid=\([0-9]*\),.*$/\1/p' | sort ); do  cat /proc/$pid/cmdline; echo  " $pid" ;done;) | uniq --count
```

这将列出为给定端口打开的连接数。 我们用的是端口3600。

结果应如下所示：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

为sms进程打开了4个连接，每个mta子级打开了2个连接，具有5个子级。

## 短信投放状态之间的差异

要阐明&#x200B;**Sent**、**Sent to the Provider**&#x200B;和&#x200B;**Received on Mobile**&#x200B;状态之间的区别，请参阅以下详细定义：

* **已在移动设备上接收**：
消息已成功传递到用户的设备，并且由已终止移动设备(MT)投放和状态报告(SR)提供确认。

* **已发送**：
已成功通过已终止移动设备(MT)步骤处理消息，但尚未收到确认传递到移动设备的状态报表(SR)。

* **已发送给提供程序**：
消息已使用`SUBMIT_SM command`发送到提供程序，但未收到来自提供程序的`SUBMIT_SM_RESP`确认。

消息可能保持为&#x200B;**已发送**&#x200B;状态，因为转换到&#x200B;**已接收**&#x200B;取决于用户设备的状态报告(SR)。 如果用户的小区接收不佳或其他连接问题，他们可能不会立即收到消息。 在这种情况下，提供商有责任重试投放或解释为何未生成SR。 如果提供商发现任何不一致，则必须确保Campaign的行为与预期一致。

以下是标准短信投放状态：

* **挂起**：消息尚未发送到聚合器。

* **提供程序已考虑**：邮件已发送到聚合器，聚合器已确认接收。

* **已发送**：聚合器已确认消息已成功推送到用户的移动网络，并且没有立即错误。

* **在移动设备上接收**：用户的移动设备已确认接收，并且聚合器已对此进行验证。

* **失败**：消息已发送到聚合器，该聚合器尝试在定义的时间段（例如，几个小时）内传递到用户的移动设备。 由于网络问题、用户设备不可用或其他原因，投放最终失败。
