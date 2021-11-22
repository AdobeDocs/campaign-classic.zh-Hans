---
product: campaign
title: 短信故障排除
description: 了解如何对短信渠道进行故障诊断的更多信息
audience: delivery
content-type: reference
topic-tags: configuring-channels
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---

# 短信疑难解答 {#troubleshooting-sms}

![](../../assets/common.svg)

## 不同外部帐户之间的冲突 {#external-account-conflict}

如果实例具有多个短信外部帐户，则必须检查问题不是由外部帐户之间的冲突造成的。

Adobe Campaign将外部帐户视为无关实体。

如果有多个帐户，请按照以下步骤隔离导致问题的外部帐户：

1. 禁用所有外部帐户。
1. 启用一个外部帐户。
1. 尝试重现问题。
1. 如果初始问题不总是出现，在结束之前，请进行合理的尝试。
1. 如果该单个帐户未出现问题，请禁用该帐户，然后在下一个帐户中重新启动到步骤2。

单独检查每个帐户后，可能会出现以下两种情况：

* **问题出现在一个或几个帐户上**

   在这种情况下，您可以单独对每个帐户应用其他故障排除过程。 最好在诊断帐户时禁用其他帐户，以减少网络流量和日志数量。

* **在任何时候只有一个帐户处于活动状态时，该问题未显示**

   帐户之间存在冲突。 如前所述，Adobe Campaign单独处理帐户，但提供商可能将它们视为单个帐户。

   * 您在所有帐户之间使用不同的登录/密码组合。
您必须联系提供商以诊断其方面的潜在冲突。

   * 某些外部帐户共享相同的登录/密码组合。
提供商无法从哪个外部帐户了解 `BIND PDU` 来自，因此他们会将多个帐户中的所有连接视为单个连接。 他们可能已将MO和SR随机路由到两个帐户，从而导致问题。
如果提供商支持同一登录名/密码组合的多个短代码，则您必须要求他们在 `BIND PDU`. 请注意，此信息必须放在 `BIND PDU`，而不是 `SUBMIT_SM`，自 `BIND PDU` 是唯一允许正确路由MO的位置。
请参阅 [每种PDU中的信息](sms-protocol.md#information-pdu) 部分以了解 `BIND PDU`，通常在 `address_range`，但需要提供商的特殊支持。 请联系他们，了解他们希望如何单独发送多个短代码。
Adobe Campaign支持在同一外部帐户上处理多个短代码。

## 一般情况下，外部帐户出现问题 {#external-account-issues}

* 调查连接器最近是否被更改以及更改者（检查外部帐户为组）。

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 调查（在/postupgrade目录中）系统是否已升级以及何时升级
* 调查最近是否升级了影响短信的任何包(/var/log/dpkg.log)。

## 中间源（托管）问题{#issue-mid-sourcing}

* 如果问题在中间源环境中发生，请确保在中间源服务器上正确创建和更新了投放和广泛日志。 如果不是这样，则不是短信问题。

* 如果mid服务器上的一切正常，并且短信均已正确发送，但营销实例未正确更新，则可能会出现中间同步问题。

## 连接到提供程序时出现问题 {#issue-provider}

* 如果 `BIND PDU` 返回非零 `command_status` 代码，请咨询提供商以了解更多信息。

* 检查网络是否配置正确，以便能够与提供程序建立TCP连接。

* 要求提供商检查他们是否将IP正确添加允许列表到Adobe Campaign实例的。

* 检查 **外部帐户** 设置。 向提供商询问字段的值。

* 如果连接成功但不稳定，请检查 [连接不稳定的问题](troubleshooting-sms.md#issues-unstable-connection) 中。

* 如果连接问题难以诊断，网络捕获可以提供信息。 确保在出现问题时网络捕获同时运行，以便对其进行有效分析。 您还应注意问题出现的确切时间。

## 连接不稳定的问题 {#issues-unstable-connection}

如果发生以下任一情况，则连接被视为不稳定：

* 连接持续时间不足1小时。 由于Adobe Campaign Classic MTA的工作方式，Adobe Campaign Classic发送器连接是一个例外。

* 提供程序发送 `UNBIND PDU`s.

* `enquire_link` 超时(在Adobe Campaign端或提供商端)。 您可能会看到 `ENQUIRE_LINK_RESP` 非零错误代码。

* 有很多 `BIND PDU`s.一天中的连接数不应多于几个，具体取决于连接数。 每小时应有超过1个BIND PDU发出警报。

如何修复连接稳定性问题：

* 不稳定的连接很少是根本原因，它通常是另一个导致断开连接的问题的结果。 首先要找到根本原因。

* 启用详细的SMPP跟踪。 您需要他们查看连接重新启动时所发生的情况。

* 如果提供商发送 `BIND PDU`可能出了点问题。 询问您的提供商为什么 `UNBING` 已发送。

* 有时，获取网络捕获是查看连接如何关闭的唯一方法。

* 如果提供程序通过发送 `TCP FIN` 或 `TCP RST packet`，请咨询您的提供商详细信息。

* 如果提供程序在发送清理错误(如 `DELIVER_SM_RESP` 如果出现错误代码，则他们必须修复其连接器，否则将阻止其他类型的消息传输，并触发MTA限制。 在收发器模式下，关闭连接会影响MT和SR，这一点尤其重要。

## 发送MT（发送给最终用户的常规短信）时出现问题{#issue-MT}

* 检查连接是否稳定。 除Adobe Campaign Classic上的发射器外，SMPP连接应持续保持至少1小时的高度。 请参阅部分 [连接不稳定的问题](sms-protocol.md#issues-unstable-connection).

* 如果重新启动MTA会使发送MT在较短的时间内再次工作，则可能由于连接不稳定而出现限制。 请参阅部分 [连接不稳定的问题](troubleshooting-sms.md#issues-unstable-connection).

* 检查广泛日志是否存在，且状态正确且日期正确。 如果不是，则可能是投放或投放准备问题。

* 检查MTA是否实际处理了消息。 如果不是这样，则可能不是短信问题。

* 检查SMS连接器是否与提供商的设备绑定。 请向提供者提供反馈，以确保所有系统都通信正确。 请参阅 `BIND_TRANSMITTER` 和 `BIND_TRANSCEIVER PDU`s ，以了解有关绑定过程的信息。 您可能需要启用SMPP跟踪才能进行正确的故障诊断。

* 启用SMPP跟踪后，检查 `SUBMIT_SM PDU` 包含正确的信息。

* 检查提供程序是否使用 `SUBMIT_SM_RESP PDU` 值（代码0）。 确保PDU到达合理延迟：超过1秒的内容必须与提供商讨论，通常在100毫秒内到达。

* 如果所有这些步骤都有效，您可以确信问题在提供方方。 他们必须在其平台上进行故障排除。

* 如果发送窗口有效，但吞吐量不一致，请尝试调整发送窗口并降低MT吞吐量。 您需要与提供商合作来调整该值。 Adobe Campaign可以非常快地发送消息，因此提供商的设备可能会出现性能问题。

## MT是重复的（同一条短信会连续多次发送）{#duplicated-MT}

重复项通常由重试引起。 重试消息时通常会出现重复项，您应尝试删除重试的根本原因。

* 如果您看到重复项间隔60秒发送，则在提供程序端可能会出现问题，他们不会发送 `SUBMIT_SM_RESP` 快点。

* 如果您看到许多 `BIND/UNBIND`，则连接不稳定。 请参阅[连接不稳定的问题](troubleshooting-sms.md#issues-unstable-connection) 部分，以了解解决重复消息问题。

请减少重试时的重复数量：

* 降低发送窗口。 发送窗口应该足够大，可以盖住 `SUBMIT_SM_RESP` 延迟。 其值表示在窗口已满时发生错误时可复制的消息数量上限。

## 处理SR（交货收据）时发出 {#issue-process-SR}

* 您需要启用SMPP跟踪才能进行任何类型的SR故障排除。

* 检查 `DELIVER_SM PDU` 来自提供商，且其格式正确。

* 检查Adobe Campaign是否成功回复 `DELIVER_SM_RESP PDU` 及时。 在Adobe Campaign Classic上，这保证SR已插入 `providerMsgId` 用于短信流程延期处理的表。

如果 `DELIVER_SM PDU` 未成功确认，则应检查以下内容：

* 在中检查与id提取和错误处理相关的正则表达式 **外部帐户**. 您可能需要根据 `DELIVER_SM PDU`.

* 检查错误是否在 `broadLogMsg` 表。

如果 `DELIVER_SM PDU` 已得到Adobe Campaign Classic扩展SMPP连接器的确认，但broadLog未正确更新，请检查部分中描述的ID协调过程 [匹配MT、SR和broadlog条目](sms-protocol.md#matching-mt).

如果您修复了所有问题，但某些无效SR仍在提供商的缓冲区中，则可以使用“无效ID确认计数”选项跳过它们。 应当谨慎使用，并在缓冲区清理后尽快将其重置为0。

## 处理MO（和阻止名单/自动回复）时出现问题{#issue-process-MO}

* 在测试期间启用SMPP跟踪。 如果不启用TLS，则在对MO进行故障排除时，应执行网络捕获，以检查PDU是否包含正确的信息且格式正确。

* 在捕获网络流量或分析SMPP跟踪时，如果配置了回复，请务必捕获与MO及其回复MT的整个对话。

* 如果MO(`DELIVER_SM PDU`)未显示在跟踪中，问题出在提供程序端。 他们必须在其平台上进行故障排除。

* 如果 `DELIVER_SM PDU` 显示，检查是否已由Adobe Campaign确认成功 `DELIVER_SM_RESP PDU` （代码0）。 此RESP可保证Adobe Campaign（自动回复和允许/）已应用所有处阻止列表理逻辑。 如果不适用，请在短信流程日志中搜索错误消息。

* 如果启用了自动回复，请检查 `SUBMIT_SM` 已发送给提供商。 如果没有，则保证在短信流程日志中找到错误消息。

* 如果 `SUBMIT_SM MT PDU` 包含回复的内容位于跟踪中，但短信未到达手机，您必须联系提供商以获取疑难解答帮助。

## 投放准备期间未排除隔离的收件人（由自动回复功能隔离）的问题 {#issue-delivery-preparation}

* 检查隔离表和投放日志中的电话号码格式是否完全相同。 如果不是，请参阅此 [部分](sms-protocol.md#automatic-reply) 如果您遇到国际电话号码格式的加号前缀问题。

* 检查短代码。 如果收件人的短代码与外部帐户中定义的短代码相同，或者为空(empty = any shortcode)，则可能会排除。 如果整个Adobe Campaign实例只使用一个简短代码，则更容易保留所有 **短码** 字段为空。

## 编码问题 {#encoding-issues}

**步骤1:与提供商联系**

联系他们，看看他们有什么问题。 他们应该能告诉你，问题是站在他们这边还是Adobe Campaign那边。 如果问题出在Adobe Campaign中，他们应该能够告诉您确切的字段不正确。

**步骤2:了解您的消息中包含的内容**

Unicode允许许多类似字符的变体，Adobe Campaign无法处理所有这些变体。

最常见的问题源于文字处理器的复制粘贴，该复制粘贴会将常用字符更改为分类正确的版本：空格更改为不中断空格，双引号更改为开号和闭号，减号更改为各种连字符等。

测试时，请勿复制并粘贴您的消息，请始终在界面中直接键入该消息。

使用十六进制，您可以区分相似字符之间的差异。 小写L、大写I、O、0、所有不同类型的引号、非拉丁编码，甚至不同类型的空格都可能看起来相同甚至根本不显示。

要将Unicode转换为十六进制，您可以使用在线工具，如 [Unicode代码转换器](https://r12a.github.io/app-conversion/) 网站。 键入文本，确保没有PII（如电话号码），然后单击 **转换**. 您将在底部看到十六进制值（UTF-32区域）。

打开有关编码问题的票证时，无论是与提供商还是 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，将始终包含您键入的内容和看到的内容的十六进制版本。

**步骤3:知道您应发送什么**

确定预期使用的编码，并联机搜索其字符表。 检查您打算发送的字符是否实际可在目标代码页面中使用。 检查 `data_coding` 字段正确，且与您和提供商的期望值相匹配。

**步骤4:了解您实际发送的内容**

您需要连接器的调试输出才能准确查看您发送给提供程序的字节。 中出现编码问题 `SUBMIT_SM PDU`所以一定要抓住他们。 发送非常独特的消息，这些消息在日志中很容易找到。

测试时发送不同种类的特殊字符。 例如，GSM7编码的扩展字符以十六进制形式非常不同，因此很容易发现，因为它们不显示在任何其他编码中。

## 有关短信问题通信时要包含的元素 {#element-include}

每当您在短信问题上寻求帮助(无论是向Adobe Campaign开启支持票证还是向短信提供商提供帮助，还是就此问题进行任何类型的通信)时，都需要包含以下信息以确保其符合相应的资格条件。 合格的问题是更快地解决问题的关键。

* **启用详细SMPP消息** 当问题出现时。 没有这个，大多数短信问题都无法解决。

* 如果问题与短信流量相关，请先与提供商联系。 其平台最适合于对短信流量问题进行实时高效诊断。

* 包括对问题的简短但事实的描述。

* 包括预期结果的描述。

* 包括来自提供商的反馈。

* 包括相关日志和/或网络捕获。 执行捕获时，请确保在捕获期间重现问题。

* 如果包含日志、跟踪或捕获，则当出现问题时，可准确定位文件中的确切位置。

* 如果引用消息、PDU或日志，则会清楚地声明其时间戳，以便更便于查找。

* 尝试在测试环境中重现问题。 如果不确定某个设置，请在测试环境中尝试该设置，然后使用SMPP跟踪检查结果。 通常最好报告在测试环境中复制的问题，而不是直接报告生产环境中的问题。

* 包括对平台所做的任何更改或调整。 此外，还应包括提供商可能在其一侧所做的任何更改。

### 网络捕获 {#network-capture}

并非总是需要网络捕获，通常只需详细的SMPP消息即可。 以下是一些准则，可帮助您确定是否需要网络捕获：

* 连接问题，但详细消息不显示任何 `BIND_RESP PDU`.

* 无法解释的断开连接，且没有错误消息，连接器在检测到低级别协议错误时的常见行为。

* 提供程序抱怨解除绑定/断开连接过程。

* 可选TLV字段中的编码问题。

* 流量可能在不同连接之间混合。

在所有其他情况下，请尝试先分析详细的SMPP消息，并仅在详细日志中缺少信息时请求网络捕获。

在某些情况下，不需要捕获网络流量。 以下是最常见的情况：

* 已启用TLS:根据定义，TLS流量会进行加密，因此无法捕获。

* 性能问题：日志包含跟踪性能问题所需的所有信息。

* 计时问题(`retry timing`, `enquire_link` 句点、吞吐量上限等)

* SR解析和处理：详细的日志提供了更多的上下文和更好的演示。

* MO处理（自动回复、隔离）。

* 不涉及实际SMPP流量的错误：投放准备、消息中心API问题、工作流问题等。

## 启用SMPP跟踪 {#enabling-smpp-traces}

新连接器支持通过跟踪进行扩展的日志记录：SMPP。 跟踪是在MTA日志中输出，而不是在标准输出中输出。

**按外部帐户启用（首选方法）**

1. 在 **外部帐户**，勾选 **在日志文件中启用详细的SMPP跟踪**.
1. 等待10分钟，让服务器重新加载外部帐户。

它现在应该处于活动状态。

**在配置中启用**

在 `config-instance.xml` ，请设置以下参数：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 检查容器上打开的连接数 {#open-connections}

要检查容器上打开的连接数，可以使用以下命令：

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

这将列出为给定端口打开的连接数。 这里我们用的是3600端口。

结果应如下：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

为sms进程打开4个连接，每个mta子项有2个子项。
