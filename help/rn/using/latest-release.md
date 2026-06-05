---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 376
ht-degree: 100%

---

# 最新版本 {#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。 每个新的内部版本都带有一个以颜色突出显示的状态。 在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.4.3 版 - 版本 9394 {#release-7-4-3}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

>[!CAUTION]
>
> 必须升级客户端控制台。

_2026 年 3 月 31 日_

### 安全性改进 {#security-7-4-3}

* 为了保持最佳的安全性、稳定性和合规性，Debian 已升级到版本13，PostgreSQL 已升级到版本 17。 请参阅[兼容性矩阵](compatibility-matrix.md)。

### 修复 {#fixes-7-4-3}

>[!NOTE]
>
> 以下列出的修复已在后续的 7.4.3 内部版本中逐步推出。导航到&#x200B;**[!UICONTROL Help > About...]**[&#x200B;菜单](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)以检查您是否拥有最新的 9394@28aaec9 内部版本。有关更多信息，请与 Adobe 代表联系。

* 修复了条形码组件允许使用无限制高度参数的问题，该问题可能导致安全漏洞。 (NEO-89984)
* 修复了通过工作流创建的列表中的枚举字段缺少临时名称属性，导致界面中显示不正确或空白枚举标签的问题。 (NEO-91158)
* 修复了在包含重复数据删除活动的工作流中使用 targetData 字段时投放准备失败并出现个性化错误的问题。 (NEO-87693)
* 修复了在 PostgreSQL 15 中，由于类型转换要求而使单字符字符串字段与其他字符串连接失败的问题。 (NEO-88028)
* 修复了由于父投放与子投放 ID 不匹配，分布式营销中的协作营销活动的跟踪日志未写入数据库的问题。 (NEO-86836)
* 修复了投放日志显示消息已取消的问题（即使消息已成功发送），尤其是影响具有波次调度的投放。 (NEO-78933)
* 修复了数据库清理工作流无法有效清除数据，从而可能影响性能的问题。 (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* 修复了未完全重新计算某些投放的投放统计信息的问题，尤其是会影响成功指标的问题。 (NEO-88106)<!-- moved from original 7.4.3 GA Fixes section -->
* 修复了客户端控制台在打开引用缺少的上游定位架构的特定工作流时可能会崩溃的问题。(NEO-28727)
* 修复了在启动失败后无法识别客户端控制台版本的问题，因为安装包中缺少版本文件。(NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

