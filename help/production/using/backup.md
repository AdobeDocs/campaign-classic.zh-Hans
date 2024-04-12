---
product: campaign
title: 备份
description: 备份
feature: Monitoring
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 2%

---

# 备份{#backup}

为了避免在机器上发生问题（无论是物理问题还是系统相关问题）时丢失数据，备份是必不可少的。

数据存储在两个不同的位置：

* 物理文件存储在Adobe Campaign目录中，
* 其它数据则存储在数据库中。

大部分数据都在数据库中。 这代表要备份的信息的99%。

## 物理文件 {#physical-files}

文件分为以下几个类别：

* 配置文件，存储在 **nl6/conf**，使您能够快速重新配置Adobe Campaign。

* 重定向文件，存储在  **nl6/var/`<instance-name>`/redir**，位于跟踪（通常称为“前端”）服务器上，并且包括所有以前的营销活动重定向。 它们仍由以前的营销活动使用。

* 日志文件，存储在 **nl6/var/`<instance-name>`/log**，可用于跟踪问题。

因此，要备份的目录包括：

* nl6/conf

* nl6/var/`<instance-name>`/redir（对于每个实例）

* nl6/var/`<instance-name>`/log （可选）

* nl6/var/`<instance-name>`/relay （可选）


## 数据库 {#database}

>[!IMPORTANT]
>
>必须备份数据库。


该数据库包含Adobe Campaign富客户端控制台中显示的所有信息，以及所有业务线数据。

您的托管公司（特别是其数据库管理员）负责此操作。
