---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cd0de82ba743fa04e59a4fa6f560a80cd5c8e940
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 99%

---

# 最新版本 {#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.4.2 版 - 内部版本 9390 {#release-7-4-2}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

_2025年4月2日_

>[!AVAILABILITY]
>
>此版本为&#x200B;**有限发布版** (LA)。仅限于托管/管理服务用户。不久将面向混合和内部部署客户提供此版本。

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### 安全性改进 {#security-7-4-2}

此版本附带多项安全性修复。

通过 **[!UICONTROL Adobe Experience Cloud]** 外部帐户与 Adobe 解决方案和应用程序的连接已更新，以加强安全性。

### 修复 {#release-7-4-2-fixes}

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

此版本中还修复了以下问题：

NEO-47269、NEO-59059、NEO-62455、NEO-65774、NEO-66462、NEO-66989、NEO-77898、NEO-78843、NEO-79373、NEO-79598、NEO-80145、NEO-80245、NEO-80434、NEO-80683、NEO-81222、NEO-81433、NEO-81864、NEO-82351、NEO-82781、NEO-82838、NEO-82923、NEO-83252、NEO-83809、NEO-83826、NEO-84024、NEO-84553、NEO-85150

