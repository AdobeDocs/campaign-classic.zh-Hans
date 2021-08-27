---
product: campaign
title: Campaign本地、混合和托管功能矩阵
description: 了解托管部署和内部部署之间的主要区别
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 19%

---

# 每个模型的功能矩阵{#capability-matrix-per-model}

![](../../assets/v7-only.svg)

Adobe Campaign Classic 随附了一组模块和选项。这些模块的可用性及其用法取决于安装的部署类型。 本文将详细介绍完全托管(Managed Services)部署与内部部署之间某些功能的主要区别。

本页显示托管(Managed Services)部署与内部部署之间的主要差异。 混合部署的特性取决于由Adobe托管并在您的场所中托管的元素。

此部分](../../installation/using/hosting-models.md)引入了不同的托管模型。[

## 每个部署模型的可用性 {#capability-matrix}

| 功能 | 托管 | 混合 | 内部部署 | 详细信息 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 配置 Campaign 服务器 | 按需 | 可用 | 可用 | [了解详情](../../installation/using/the-server-configuration-file.md) |
| 电子邮件密送 | 按需 | 按需 | 可用 | [了解详情](../../installation/using/email-archiving.md) |
| 管理消息中心执行实例 | 按需 | 按需 | 可用 | [了解详情](../../message-center/using/about-transactional-messaging.md) |
| 管理中间源平台 | 按需 | 按需 | 可用 | [了解详情](../../installation/using/mid-sourcing-server.md) |
| 通过Litmus呈现收件箱 | 按需 | 按需 | 可用 | [了解详情](../../delivery/using/inbox-rendering.md) |
| 与IMS集成(Adobe ID) | 按需 | 按需 | 按需 | [了解详情](../../integrations/using/about-adobe-id.md) |
| 加密/解密用于文件传输的数据 | 按需 | 可用 | 可用 | [了解详情](../../platform/using/unzip-decrypt.md) |
| 压缩/解压缩文件 | 按需 | 可用 | 可用 | [了解详情](../../platform/using/unzip-decrypt.md) |
| 域名委派 | 按需 | 按需 | 不可用 | [了解详情](https://helpx.adobe.com/cn/campaign/kb/domain-name-delegation.html) |
| 安装SpamAssassin | 按需 | 可用 | 可用 | [了解详情](../../delivery/using/spamassassin.md) |
| 访问投放能力报告 | 可用 | 按需 | 可用 | [了解详情](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份验证 | 不可用 | 可用 | 可用 | [了解详情](../../installation/using/connecting-through-ldap.md) |


## 联合数据访问{#fda}

Adobe Campaign提供了&#x200B;**联合数据访问**(FDA)选项，以便处理存储在一个或多个外部数据库中的信息：您无需更改Adobe Campaign数据的结构即可访问外部数据。 [了解详情](../../installation/using/about-fda.md)

>[!CAUTION]
>
>只有内部部署或混合安装(使用[Snowflake连接器](../../installation/using/configure-fda-snowflake.md)除外)才能通过FDA访问外部数据库。


**另请参阅**

* [兼容性矩阵](../../rn/using/compatibility-matrix.md)
* [发行说明](../../rn/using/latest-release.md)
* [Campaign Classic升级](../../rn/using/rn-overview.md)
* [已弃用和已移除的功能](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] 发行版本](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard] 项目](../../rn/using/gs-overview.md)
