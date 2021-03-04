---
solution: Campaign Classic
product: campaign
title: 最新版本
description: 最新 Campaign Classic 发行说明
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 14513d5ecbfdd5637b764c8f19bc01358e63c130
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# 最新版本{#latest-release}

此页面列出了&#x200B;**最新 Campaign Classic 发行候选版本**&#x200B;随附的新功能、改进和修复。

对于 Campaign Classic Gold Standard 版本（最新 GA 内部版本），[请参阅此页面](../../rn/using/gold-standard.md)。

## ![](assets/do-not-localize/blue_2.png) 版本 21.1.1 - 版本 9277 {#release-21-1-1-build-9277}

_2021年2月22日_

**安全性增强**

* 已改进控制台身份验证机制以优化安全性。 (NEO-26944)
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-28532)

**兼容性更新**

Campaign 现在支持以下系统：

* 现在，使用Salesforce CRM外部帐户时支持Salesforce API版本49。

**已弃用的功能**

**技术交付性监控**&#x200B;报告现已弃用。

在[已弃用和已删除的功能页面](../../rn/using/deprecated-features.md)中了解详情。

**改进**

**电子邮件反馈服务(EFS)是一** 项可扩展的服务，可直接从增强的MTA中捕获反馈，从而提高报告准确性。此功能作为专用测试版发布，并将在未来版本中逐步向所有客户提供。

* 现在可捕获所有类别的反馈，以实现完整且精确的报告。
* 现在，已传送指示器的计算基于来自增强型 MTA 的实时反馈，以提高准确性和反应性。
* EFS 解决了同步软退回报告的延迟问题。

有关更多信息，请参阅[详细文档](../../delivery/using/sending-with-enhanced-mta.md#efs)。如果您有兴趣参加此私有测试版，请填写此[表单](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我们将回复给您。

**其他变更**

* 对于大型跟踪日志，使用压缩提高了传输速度。
* 工作流热图已得到改进，可避免在运行具有多个工作流的活动时超时。 (NEO-27423).
* 修复了即使优惠的结束日期已过，也可能允许显示该订阅的问题。 Campaign Classic现在考虑结束日期的整个时间戳，而不是只考虑日期。 (NEO-27590)
* Google+链接已从&#x200B;**社交网络共享链接**&#x200B;个性化块中删除。
* 修复了在上一版本中实施错误修复之后的问题。 使用导致SMS投放失败的SSL/TLS连接时，在主机名上添加了检查。 已对POP3、SMS和带代理的HTTP等大多数协议禁用主机名验证，并且SMS外部帐户的证书检查已改进为具有三个值(NEO-29581)。 [了解详情](../../delivery/using/sms-protocol.md#skip-tls)

**修补程序**

* 修复了Tab键、Enter键和Esc键盘快捷键无法在新登录屏幕上工作的问题。
* 修复了在保存后导致新创建工作流的名称替换为默认值(NEO-26106)的刷新问题。
* 修复了在使用&#x200B;**外部文件**&#x200B;工作流运行&#x200B;**投放**&#x200B;活动之前，将新字段添加为&#x200B;**扩充**&#x200B;目标映射的一部分时发生的问题：将不需要的字段添加到&#x200B;**外部文件**&#x200B;目标映射。 (NEO-27687)
* 修复了在重新打开先前创建和保存的Web应用程序时，导致源代码中的某些字符发生更改的问题。 (NEO-27597)
* 修复了升级到包含跟踪链接的新签名机制(从内部版本19.1.4和活动 20.2)的内部版本时可能发生的问题：当多个模板与某个事件关联时，升级可能会导致在发送事务性消息时选择错误的模板。 (NEO-28326)
* 修复了导致MTA无响应且无法处理投放的问题，除非重新启动。 (NEO-27455)
* 修复了在对日期时间类型列执行批量加载操作期间与时间戳管理相关的MSSQL数据库问题。
* 修复了使用Redshift xtk函数时的工作流查询问题。 SubDays、SubSeconds、SubMinutes和SubHours现在接受Redshift时间戳类型(NEO-24962)。
* 修复了在尝试预览具有匿名访问权限的报表时显示脚本错误消息的问题。 (NEO-27081)
* 修复了在执行投放分析时，可能会减少服务器内存使用的问题。
* 修复了在尝试运行特定复杂查询时，可能会阻止实例工作的问题。
* 修复了可能会阻止&#x200B;**同步Twitter页面**&#x200B;技术工作流运行的问题。 (NEO-28634)
* 修复了在尝试使用&#x200B;**Tweet(twitter)**&#x200B;投放模板在Twitter上发布时，可能显示与decryptPassword函数相关的错误消息的问题。 (NEO-28216)
* 修复了在工作流中使用&#x200B;**Javascript**&#x200B;活动发出HTTP请求时出现的问题。 在主机名中定义端口号后，调用将失败，并出现以下错误(NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 修复了无法发送具有目标投放个性化的新的问题。
* 修复了营销实例中发生多次崩溃导致核心文件的问题。
* 修复了导致&#x200B;**跟踪**&#x200B;工作流失败并出现以下错误(NEO-25206)的问题：

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 修复了在投放的&#x200B;**定位和工作流**&#x200B;选项卡中创建和保存活动时发生的问题：预览将失败，并出现以下错误(NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 修复了在营销实例与Adobe Campaign Standard实例或Campaign Classic中间源实例之间设置外部帐户时使用选项“DisableFOH2=1”时发生的错误。 当在外部帐户中使用“DisableFOH2=1”选项时，连接未正确关闭，并会累积导致以下错误(NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 修复了在服务器和提供程序之间发生连接问题时SMS出现错误。 然后，MTA子项将自动禁用连接。 只要尚未启动新子项，Adobe Campaign Classic不会尝试连接到此失败的连接。
