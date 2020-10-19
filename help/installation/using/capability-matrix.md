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
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 10%

---


# 每个托管模型的能力矩阵 {#capability-matrix-per-model}

Adobe Campaign Classic 随附了一组模块和选项。这些模块的可用性及其使用取决于您的安装部署类型。 本文分享了完全托管(Managed Services)和内部部署之间某些功能的主要区别。

本页显示了托管(Managed Services)和内部部署之间的主要区别。 混合部署的具体性取决于由Adobe托管并托管在您所在地的元素。

本节介绍不同的 [托管模型](../../installation/using/hosting-models.md)。

## 能力矩阵{#capability-matrix}

| 功能 | 托管 | 混合 | 内部部署 | 详细信息 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 配置活动服务器 | 按需 | 可用 | 可用 | 只[能通过Adobe](../../installation/using/the-server-configuration-file.md)，为托管客户修改服务器配置文件。 |
| 密件抄送 | 按需 | 按需 | 可用 | 对于托管和混合架构，请联系您的客户经理以激活电子邮件密送。 对于内部部署安装，请遵循文档中的准则。 [了解详情](../../installation/using/email-archiving.md) |
| 管理消息中心执行实例 | 按需 | 按需 | 可用 | 对于托管部署，某些设置(如在执行实例上创建用户)只能由Adobe执行。 [了解详情](../../message-center/using/about-transactional-messaging.md) |
| 管理中间源平台 | 按需 | 按需 | 可用 | 中间源托管的Adobe平台只能由Adobe配置。 |
| 通过Litmus呈现收件箱 | 按需 | 按需 | 可用 | 你需要一个利特姆斯账户。 您需要联系Adobe以获取必要的详细信息或执行收件箱渲染配置。 [了解详情](../../delivery/using/inbox-rendering.md) |
| 与因特网管理系统(Adobe ID)集成 | 按需 | 按需 | 按需 | IMS设置由Adobe执行。 此集成是Adobe Experience Cloud集成的先决条件。 [了解详情](../../integrations/using/about-adobe-id.md) |
| 为文件传输加密／解密数据 | 按需 | 可用 | 可用 | 要启用文件预处理或后处理，需要在Adobe Campaign服务器上安装必要的实用程序。 托管客户可以使用活动控制面板。 [了解详情](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 压缩／解压文件 | 按需提供 | 可用 | 要启用文件预处理或后处理，需要在Adobe Campaign服务器上安装必要的实用程序。 托管客户可以使用活动控制面板。 [了解详情](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 域名委派 | 按需 | 按需 | 不可用 | [了解详情](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html) |
| 安装SpamAssassin | 按需 | 可用 | 可用 | 安装SpamAssassin需要编辑服务器配置文件。 [了解详情](../../delivery/using/spamassassin.md) |
| 访问交付性报告 | 可用 | 按需 | 可用 | 在某些混合部署中，无法从营销实例访问交付能力报告。 |
| 配置LDAP身份验证 | 不可用 | 可用 | 可用 | LDAP配置仅可用于本地或混合安装。 [了解详情](../../installation/using/connecting-through-ldap.md) |


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
* [金本位项目](https://helpx.adobe.com/cn/campaign/kb/gold-standard.html)。
