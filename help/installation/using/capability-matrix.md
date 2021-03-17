---
solution: Campaign Classic
product: campaign
title: 活动内部部署、混合和托管功能矩阵
description: 了解托管部署和内部部署之间的主要差异
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 19%

---


# 每个型号的能力矩阵{#capability-matrix-per-model}

Adobe Campaign Classic 随附了一组模块和选项。这些模块的可用性及其使用情况取决于您的安装的部署类型。 本文分享了完全托管(Managed Services)和内部部署之间某些功能的主要区别。

本页显示托管(Managed Services)与内部部署之间的主要差异。 混合部署的具体性取决于由Adobe托管并托管在您的场所中的元素。

本节](../../installation/using/hosting-models.md)介绍了不同的托管模型。[

## 每个部署模型{#capability-matrix}的可用性

| 功能 | 托管 | 混合 | 内部部署 | 详细信息 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 配置活动服务器 | 按需 | 可用 | 可用 | [了解详情](../../installation/using/the-server-configuration-file.md) |
| 密件抄送 | 按需 | 按需 | 可用 | [了解详情](../../installation/using/email-archiving.md) |
| 管理消息中心执行实例 | 按需 | 按需 | 可用 | [了解详情](../../message-center/using/about-transactional-messaging.md) |
| 管理中间源平台 | 按需 | 按需 | 可用 | [了解详情](../../installation/using/mid-sourcing-server.md) |
| 通过Litmus呈现收件箱 | 按需 | 按需 | 可用 | [了解详情](../../delivery/using/inbox-rendering.md) |
| 与IMS集成(Adobe ID) | 按需 | 按需 | 按需 | [了解详情](../../integrations/using/about-adobe-id.md) |
| 加密/解密文件传输的数据 | 按需 | 可用 | 可用 | [了解详情](../../platform/using/unzip-decrypt.md) |
| 压缩/解压缩文件 | 按需 | 可用 | 可用 | [了解详情](../../platform/using/unzip-decrypt.md) |
| 域名委派 | 按需 | 按需 | 不可用 | [了解详情](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html) |
| 安装SpamAssassin | 按需 | 可用 | 可用 | [了解详情](../../delivery/using/spamassassin.md) |
| 访问交付性报告 | 可用 | 按需 | 可用 | [了解详情](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份验证 | 不可用 | 可用 | 可用 | [了解详情](../../installation/using/connecting-through-ldap.md) |


## 联合数据访问{#fda}

Adobe Campaign提供&#x200B;**联合数据访问**(联合数据访问)选项，以便处理存储在一个或多个外部数据库中的信息：您可以访问外部数据，而无需更改Adobe Campaign数据的结构。 [了解详情](../../installation/using/about-fda.md)

>[!CAUTION]
>
>只有内部部署或混合安装才能通过联合数据访问访问外部Snowflake库，但[连接器](../../installation/using/configure-fda-snowflake.md)除外。


**另请参阅**

* [兼容性矩阵](../../rn/using/compatibility-matrix.md)
* [发行说明](../../rn/using/latest-release.md)
* [Campaign Classic升级](../../rn/using/rn-overview.md)
* [已弃用和已删除的功能](../../rn/using/deprecated-features.md)
* [Gold Standard 版本](../../rn/using/gold-standard.md)
* [金本位项目](https://helpx.adobe.com/cn/campaign/kb/gold-standard.html)
