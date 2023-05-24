---
product: campaign
title: Campaign本地、混合和托管功能矩阵
description: 了解托管部署和内部部署之间的主要区别
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 28%

---

# 每个模型的功能矩阵{#capability-matrix-per-model}



Adobe Campaign Classic 随附了一组模块和选项。这些模块的可用性及其使用方式取决于安装的部署类型。 本文详细介绍了完全托管(Managed Services)部署与内部部署之间在某些功能上存在的主要差异。

本页显示了托管(Managed Services)部署与内部部署之间的主要区别。 混合部署的特定性取决于Adobe托管并在您的内部部署中托管的元素。

介绍了不同的托管模型 [在此部分中](../../installation/using/hosting-models.md).

## 每个部署模型的可用性 {#capability-matrix}

| 功能 | 托管 | 混合 | 内部部署 | 详细信息 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 配置 Campaign 服务器 | On-demand | 可用 | 可用 | [了解详情](../../installation/using/the-server-configuration-file.md) |
| 电子邮件密件抄送 | On-demand | On-demand | 可用 | [了解详情](../../installation/using/email-archiving.md) |
| 管理消息中心执行实例 | On-demand | On-demand | 可用 | [了解详情](../../message-center/using/about-transactional-messaging.md) |
| 管理中间源平台 | On-demand | On-demand | 可用 | [了解详情](../../installation/using/mid-sourcing-server.md) |
| 通过Litmus呈现收件箱 | On-demand | On-demand | 可用 | [了解详情](../../delivery/using/inbox-rendering.md) |
| 与IMS集成(Adobe ID) | On-demand | On-demand | On-demand | [了解详情](../../integrations/using/about-adobe-id.md) |
| 加密/解密用于文件传输的数据 | On-demand | 可用 | 可用 | [了解详情](../../platform/using/unzip-decrypt.md) |
| 压缩/解压缩文件 | On-demand | 可用 | 可用 | [了解详情](../../platform/using/unzip-decrypt.md) |
| 域名委派 | On-demand | On-demand | 不可用 | [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hans) |
| 安装SpamAssassin | On-demand | 可用 | 可用 | [了解详情](../../delivery/using/spamassassin.md) |
| 访问可投放性报告 | 可用 | On-demand | 可用 | [了解详情](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份验证 | 不可用 | 可用 | 可用 | [了解详情](../../installation/using/connecting-through-ldap.md) |


## 联合数据访问{#fda}

Adobe Campaign提供 **联合数据访问** (FDA)选项，用于处理存储在一个或多个外部数据库中的信息：无需更改Adobe Campaign数据的结构即可访问外部数据。 [了解详情](../../installation/using/about-fda.md)

>[!CAUTION]
>
>兼容的外部数据库系统取决于您的托管模型。 了解详情，请参阅 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md).

**另请参阅**

* [兼容性矩阵](../../rn/using/compatibility-matrix.md)
* [发行说明](../../rn/using/latest-release.md)
* [Campaign Classic升级](../../rn/using/rn-overview.md)
* [已弃用和已移除的功能](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] 版本](../../rn/using/gold-standard.md)
