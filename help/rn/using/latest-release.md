---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# 最新版本{#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.3.5 版 - 内部版本 9368 {#release-7-3-5}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}


_2023 年 12 月 5 日_


### 安全性增强 {#release-7-3-5-security}


* 在 Campaign Classic v7.3.5 中，身份验证过程已得到改进并受保护。现在，技术操作员应使用 Adobe Identity Management System (IMS) 连接到 Campaign。请阅读[此技术说明](../../technotes/using/ims-migration.md)，了解如何迁移现有技术帐户。

* 此外，作为加强安全和身份验证过程的一部分，Adobe Campaign 强烈建议将终端用户身份验证模式从登录/密码本机身份验证迁移到 Adobe Identity Management System (IMS)。请阅读[此技术说明](../../technotes/using/migrate-users-to-ims.md)，了解如何迁移操作员。

* 现在，如果 Web 窗体有&#x200B;**待发布**&#x200B;状态，它不会自动上线。为防止出现安全问题，必须先将其发布，然后才能使其&#x200B;**上线**&#x200B;并通过 Web 浏览器中的 Web 窗体 URL 访问它。[了解更多信息](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### 修补程序 {#release-7-3-5-patches}

* 修复了使用 Google Big Query 数据库中的数据和更新 Oracle 数据库中的数据时出现的问题：在工作流临时表中，将所有键都设置为 `0`。(NEO-65091)
* 修复了当 Google Big Query 数据库上的两个查询合并到 **Union** 工作流活动中时导致工作流执行失败的问题。(NEO-63705)
* 修复了在 Campaign 报告中单击 `Back` 按钮时请求用户重新进行身份验证的问题。(NEO-65087)
* 修复了数据库清理工作流中发生的错误，在投放证明前删除投放时会发生该错误。(NEO-48114)
* 修复了连接到客户端控制台时的问题：最近对 TLS 验证的更新导致连接错误。(NEO-50488)
* 修复了 Campaign 升级到 7.3.1 后 HTTP 代理身份验证的问题。活动工作流中的 HTTP 请求失败，并出现 `error 407 – proxy auth required is returned`。(NEO-49624)
* 修复了&#x200B;**脚本**&#x200B;工作流活动中 GPG 解密的间歇性故障。相关的错误消息为：`gpg: decryption failed: No secret key`。(NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

