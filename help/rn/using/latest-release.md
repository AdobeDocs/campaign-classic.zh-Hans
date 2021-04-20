---
solution: Campaign Classic
product: campaign
title: 最新版本
description: 最新 Campaign Classic 发行说明
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: abd5c7430c3f7a1a056a014ad46a0b94157e259f
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 97%

---

# 最新版本{#latest-release}

此页面列出了&#x200B;**最新 Campaign Classic 发行候选版本**&#x200B;随附的新功能、改进和修复。

>[!NOTE]
>
>活动&#x200B;**一般可用性(GA)内部版本**&#x200B;为：[[!DNL Gold Standard] 11发行版](../../rn/using/gold-standard.md#gs-11)和[活动 20.2.5发行版](../../rn/using/release--20-2.md)。

## ![](assets/do-not-localize/blue_2.png) 21.1.2 版 - 内部版本 9282 {#release-21-1-2-build-9282}

_2021年4月15日_

* 密码管理已得到改进，以优化安全性。
* 修复了可能导致MTA崩溃的问题。

## ![](assets/do-not-localize/red_2.png) 21.1.1 版 - 内部版本 9277 {#release-21-1-1-build-9277}

_2021 年 2 月 22 日_

**安全性增强**

* 改进了控制台身份验证机制以优化安全性。 (NEO-26944)
* 修复了一个安全问题，加强了针对服务器端请求伪造 (SSRF) 问题的防护。(NEO-28532)

**兼容性更新**

Campaign 现在支持以下系统：

* 现在，使用 Salesforce CRM 外部帐户时支持 Salesforce API 版本 49。

**已弃用的功能**

**技术性投放能力监控**&#x200B;报告功能现已弃用。

在[已弃用和已删除的功能页面](../../rn/using/deprecated-features.md)中了解详情。

**改进**

**电子邮件反馈服务 (EFS)**&#x200B;是一种可扩展服务，它直接从增强 MTA 获取反馈，从而提高报告准确性。此功能作为专用测试版发布，并将在未来版本中逐步向所有客户提供。

* 现在可捕获所有类别的反馈，以实现完整且精确的报告。
* “已投放”指标的计算现在以来自增强 MTA 的实时反馈为基础，以提高准确性和反应性。
* EFS 通过同步软退信报告的方式解决了延迟问题。

有关更多信息，请参阅[有详细说明的文档](../../delivery/using/sending-with-enhanced-mta.md#efs)。
如果您有兴趣参与此私人测试版的试用，请填写此[表单](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我们将回复您。

**其他变更**

* 通过使用压缩方法，提高了大型跟踪日志的传输速度。
* 改进了工作流热图以避免在运行具有多个活动的工作流时发生超时 (NEO-27423)。
* 修复了即使优惠的结束日期已过，仍可能允许显示该优惠信息的问题。Campaign Classic 现在会考虑结束日期的整个时间戳，而不是只考虑日期。(NEO-27590)
* Google+ 链接已从&#x200B;**社交网络分享链接**&#x200B;个性化区块中移除。
* 修复了上个版本中实施错误修复后出现的问题。在使用 SSL/TLS 连接时增加了对主机名的检查，因而导致 SMS 投放失败。已对 POP3、SMS 和带代理的 HTTP 等大多数协议禁用主机名验证，并且 SMS 外部帐户的证书校验已改进为提供三个值 (NEO-29581)。[了解详情](../../delivery/using/sms-protocol.md#skip-tls)

**修补程序**

* 修复了导致 Tab 键、Enter 键和 Esc 键盘快捷键无法在新登录屏幕上使用的问题。
* 修复了导致新创建的工作流的名称在保存后被替换为默认值的刷新问题 (NEO-26106)。
* 修复了运行工作流时，在进行使用&#x200B;**外部文件**&#x200B;目标映射的&#x200B;**投放**&#x200B;活动之前，将新字段添加为&#x200B;**扩充**&#x200B;活动的一部分时发生的问题：不需要的字段被添加至&#x200B;**外部文件**&#x200B;目标映射。(NEO-27687)
* 修复了重新打开之前创建和保存的 Web 应用程序时，会导致源代码中的部分字符发生更改的问题。(NEO-27597)
* 修复了升级到包含用于跟踪链接的新签名机制的内部版本时可能发生的问题（从内部版本 19.1.4 和 Campaign 20.2）：当多个模板与某个事件关联时，升级可能会导致在发送事务性消息时选择错误的模板。(NEO-28326)
* 修复了导致 MTA 无响应并且无法处理投放（除非重新启动）的问题。(NEO-27455)
* 修复了在对日期时间类型列执行批量加载操作时与时间戳管理相关的 MSSQL 数据库问题。
* 修复了使用 Redshift xtk 函数时的工作流查询问题。SubDays、SubSeconds、SubMinutes 和 SubHours 现在接受两种 Redshift 时间戳类型 (NEO-24962)。
* 修复了尝试以匿名访问方式预览报告时会显示脚本错误消息的问题。(NEO-27081)
* 修复了在执行投放分析时，可能会减少服务器内存使用的问题。
* 修复了在尝试运行特定的复杂查询时，可能会阻止实例工作的问题。
* 修复了可能会阻止&#x200B;**同步 Twitter 页面**&#x200B;技术工作流运行的问题。(NEO-28634)
* 修复了尝试使用 **Tweet (twitter)** 投放模板在 Twitter 上发布时，可能会显示与 decryptPassword 函数相关的错误消息的问题。(NEO-28216)
* 修复了在工作流中使用 **Javascript** 活动发出 HTTP 请求时出现的问题。在主机名称中定义端口号后，调用会失败，并出现以下错误 (NEO-29146)：

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 修复了导致无法发送带有目标数据个性化设置的新投放的问题 (NEO-30323)。
* 修复了营销实例中发生多次崩溃时导致核心文件出现的问题。
* 修复了会导致&#x200B;**跟踪**&#x200B;工作流失败并出现以下错误 (NEO-25206) 的问题：

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 修复了在营销活动的 **Targeting &amp; Workflow（定位和工作流）**&#x200B;选项卡中创建和保存投放时发生的问题：预览会失败，并出现以下错误 (NEO-29440)：

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 修复了在营销实例与 Adobe Campaign Standard 实例或 Campaign Classic 中间源实例之间设置外部帐户并使用选项“DisableFOH2=1”时发生的错误。当在外部帐户中使用“DisableFOH2=1”选项时，连接未正确关闭，并会堆积导致以下错误 (NEO-26258)：

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 修复了服务器和提供商之间发生连接问题时 SMS 出现的错误。之后，MTA 子项将自动禁用连接。只要尚未启动新子项，Adobe Campaign Classic 就不会尝试连接到此失败的连接。
