---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 66387e2e008051901fe3385f571d7fe798829100
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# 最新版本 {#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.4.3 版 - 内部版本 9392 {#release-7-4-3}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

_2026年3月16日_

>[!CAUTION]
>
> 必须升级客户端控制台。

### 安全性改进 {#security-7-4-3}

* 为了保持最佳的安全性、稳定性和合规性，Debian已升级到版本13，PostgreSQL已升级到版本17。 请参阅[兼容性矩阵](compatibility-matrix.md)。

### 修复 {#fixes-7-4-3}

* 修复了条形码组件允许使用无限制高度参数的问题，该问题可能导致安全漏洞。 (NEO-89984)
* 修复了通过工作流创建的列表中的枚举字段缺少临时名称属性，导致界面中显示不正确或空白枚举标签的问题。 (NEO-91158)
* 修复了未完全重新计算某些投放的投放统计信息的问题，尤其是会影响成功指标的问题。 (NEO-88106)
* 修复了在包含重复数据删除活动的工作流中使用targetData字段时投放准备失败并出现个性化错误的问题。 (NEO-87693)
* 修复了在PostgreSQL 15中，由于类型转换要求而使单字符字符串字段与其他字符串连接失败的问题。 (NEO-88028)
* 修复了由于父投放与子投放ID不匹配，分布式营销中的协作营销活动的跟踪日志未写入数据库的问题。 (NEO-86836)
* 修复了投放日志显示消息已取消的问题（即使消息已成功发送），尤其是影响具有波次调度的投放。 (NEO-78933)
* 修复了数据库清理工作流无法有效清除数据，从而可能影响性能的问题。 (NEO-76439)

