---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 96%

---

# 最新版本 {#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 版本 7.4.2  {#release-7-4-2}

### 版本9391 {#build-9391}

[!BADGE 有限发布版]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="有限发布版"}

_2025年5月12日_

此内部版本包含以下修复：

* 修复了在非Oracle设置中遇到的升级后问题。 (NEO-87012)
* 修复了影响客户端控制台和服务器的TLS/HTTPS后端问题。 (NEO-87432)

### 版本9390 {#build-9390}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

_2025 年 4 月 2 日_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**安全性改进**

此版本附带多项安全性修复。

通过 **[!UICONTROL Adobe Experience Cloud]** 外部帐户与 Adobe 解决方案和应用程序的连接已更新，以加强安全性。

**主要修复**

此版本附带以下主要修复：

* TLS / SMPP 连接 - 修复了 SMPP 稳定性问题

* Google BigQuery 修复：

   * 修复了 BOOLEAN 数据类型的回归
   * 修复了代理设置问题
   * 修复了 DATETIME 数据类型的回归
   * 修复了批量加载稳定性
   * 改进了 ODBC 版本的内部测试
   * 修复了连接字符串的特殊字符问题
   * 移除了 Google BigQuery 查询的默认超时（5 分钟）

* 邮件传输代理 (MTA) - 修复了孤立 MTA 子项停留在 **[!UICONTROL Start pending]** 状态。


**其他修复**

此版本中还修复了以下问题：

* 修复了&#x200B;**数据加载（文件）**&#x200B;活动无法将文件上传到服务器<!--after an upgrade to version 8.3.8-->的问题。用户现在可以成功上传文件，而不会遇到进度停滞或控制台错误。(NEO-47269)

* 解决了 Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349--> 中的分段错误问题。此修复可防止生成核心文件，并确保服务器稳定运行。(NEO-59059)

* 已解决 Google BigQuery 数据库 <!--after upgrading to version 7.3.3 build 9359--> 的连接问题。用户现在可以使用 GCP 外部帐户成功测试连接。(NEO-62455)

* 增强了使用联合数据访问 (FDA) 的 Google BigQuery 表中布尔值和日期时间列更新的兼容性。此修复可确保在插入/更新操作期间正确处理数据类型。(NEO-65774)

* 修复了允许攻击者将 HTML 元素注入电子邮件端点的资源注入漏洞。此安全增强功能可防范未经授权的访问和网络钓鱼企图。(NEO-66462)

* 解决了将数据插入 Google BigQuery 表时因 HTTP 内容或传输编码问题而导致的间歇性错误。此修复可确保稳定的数据加载工作流。(NEO-66989)

* 解决了工作流中 `File.list()` 方法的路径遍历漏洞。此安全增强功能可防止未经授权的目录访问并保护敏感文件。(NEO-77898)

* 修复了短信投放日志未正确更新为“已在移动设备上接收”状态的问题。此增强功能可确保投放报告准确。(NEO-78843)

* 解决了使用 Azure 联合数据访问 (FDA) 时 Adobe Campaign Classic 中的登录错误。用户现在可以通过客户端控制台成功登录。(NEO-79373)

* 修复了 `CCurlAzureBlobStorage::UploadStream()` 方法导致的工作流崩溃。此增强功能可确保工作流稳定执行。(NEO-79598)

* 在 Windows 上激活了两个关键编译标志（`ControlFlowGuard` 和 `StackProtection`），以增强产品安全性并降低漏洞被利用的风险。(NEO-80145)

* 修复了 broadlog 处于失败状态时错误发送事件状态的问题。此增强功能可确保进行准确的事件报告。(NEO-80245)

* POP3 OAuth 刷新和访问令牌现在保存在数据库中，在刷新令牌过期后不再出现 `Authentication failure: unknown user name or bad password` 错误。(NEO-80683)

* 现在将选项 `XApiKey` 用作客户 ID 的值以连接到 Adobe Analytics，而不是使用 Marketing Cloud (MAC) 外部帐户的客户 ID。(NEO-80434)

* 解决了 inMail 用户因令牌过期而遇到身份验证错误的问题。用户现在可以测试连接并重新启动服务器以解决类似问题。(NEO-80683)

* 通过确保所有分析调用都使用一致的 API 密钥 (Campaign1) 进行身份验证（即使切换到随机客户 ID 也是如此），改进了 Analytics API 功能。这可确保无缝分析跟踪。(NEO-80434)

* 通过允许用户调整查询的超时期限，增强了 BigQuery 联合数据访问 (FDA) 连接器。这项改进可防止长时间运行查询期间出现超时错误。(NEO-81222)

* 更新了 Campaign <!--7.4.1--> 版本升级过程，纳入了所需的依赖项。此增强功能简化了用户的升级过程。(NEO-81433)

* 修复了将子工作流与 `enum` 字段结合使用时的控制台崩溃问题。此增强功能可确保工作流稳定执行。(NEO-81864)

* 解决了 MTA 子进程停滞、阻止投放插槽的问题。此修复可确保推送和 WhatsApp 通信的顺利投放。(NEO-82351)

* 修复了由于投放活动暂停而导致投放卡在个性化待处理的问题。此增强功能可确保成功执行投放。(NEO-82781)

* 利用 CampaignIO 端点进行身份验证，增强了 IMS 登录功能。这一改进简化了登录流程。(NEO-82838)

* 重新修复了 Google BigQuery 联合数据访问 (FDA) 超时错误，以确保在部署热修复程序后稳定执行查询。(NEO-82923)

* 解决了将大量数据加载到 Teradata 表中时的间隔问题。此增强功能可确保稳定的数据加载操作。(NEO-83252)

* 修复了由于日期和时间戳比较不匹配导致 GCP 查询失败的问题<!--after upgrading to version 9383-->。此增强功能可确保查询兼容性。(NEO-83826)

* 解决了由于恢复暂停的投放活动而导致的投放故障。此修复可确保成功执行投放。(NEO-83809)

* 修复了使用私钥身份验证时 Snowflake 联合数据访问 (FDA) 连接器的身份验证错误。此增强功能可确保成功连接数据库。(NEO-84024)

* 实施了对看门狗模块的更改，以解决由进程停滞导致的 MTA 子插槽阻止问题。此增强功能可确保顺利投放。(NEO-84553)

* 增强的 Javascript 等待检查可解决工作中的进程导致的 MTA 子插槽阻止问题。此修复可确保稳定的投放操作。(NEO-85150)

