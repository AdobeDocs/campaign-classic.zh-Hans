---
title: 活动本地、混合和托管能力矩阵
description: 了解托管部署和内部部署之间的主要区别
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c03e90b2e2f57606749c86cda343ce5756fec122
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 18%

---


# 能力矩阵 {#capability-matrix-per-model}

Adobe Campaign Classic 随附了一组模块和选项。这些模块的可用性及其使用取决于您的安装部署类型。 本文分享了完全托管(Managed Services)和内部部署之间某些功能的主要区别。

本页显示了托管(Managed Services)和内部部署之间的主要区别。 混合部署的具体性取决于由Adobe托管并托管在您所在地的元素。

本节介绍不同的 [托管模型](../../installation/using/hosting-models.md)。

## 每个部署模型的可用性 {#capability-matrix}

| 功能 | 托管 | 混合 | 内部部署 | 详细信息 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 配置活动服务器 | 按需 | 可用 | 可用 | [了解详情](../../installation/using/the-server-configuration-file.md) |
| 密件抄送 | 按需 | 按需 | 可用 | [了解详情](../../installation/using/email-archiving.md) |
| 管理消息中心执行实例 | 按需 | 按需 | 可用 | [了解详情](../../message-center/using/about-transactional-messaging.md) |
| 管理中间源平台 | 按需 | 按需 | 可用 | [了解详情](../../installation/using/mid-sourcing-server.md) |
| 通过Litmus呈现收件箱 | 按需 | 按需 | 可用 | [了解详情](../../delivery/using/inbox-rendering.md) |
| 与因特网管理系统(Adobe ID)集成 | 按需 | 按需 | 按需 | [了解详情](../../integrations/using/about-adobe-id.md) |
| 为文件传输加密／解密数据 | 按需 | 可用 | 可用 | [了解详情](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 压缩／解压文件 | 按需 | 可用 | 可用 | [了解详情](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 域名委派 | 按需 | 按需 | 不可用 | [了解详情](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html) |
| 安装SpamAssassin | 按需 | 可用 | 可用 | [了解详情](../../delivery/using/spamassassin.md) |
| 访问交付性报告 | 可用 | 按需 | 可用 | [了解详情](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份验证 | 不可用 | 可用 | 可用 | [了解详情](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [了解详情](../../platform/using/about-fda.md)

>[!CAUTION]
>
>通过联合数据访问访问外部数据库仅可用于内部安装或混合安装，Snowflake连接器 [除外](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)。


**另请参阅**

* [兼容性矩阵](../../rn/using/compatibility-matrix.md)
* [发行说明](../../rn/using/latest-release.md)
* [Campaign Classic升级](../../rn/using/rn-overview.md)
* [已弃用和已删除的功能](../../rn/using/deprecated-features.md)
* [Gold Standard版本](../../rn/using/gold-standard.md)
* [金本位项目](https://helpx.adobe.com/cn/campaign/kb/gold-standard.html)
