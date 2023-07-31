---
product: campaign
title: 技术说明 — Apple推送通知服务服务器证书更新
description: Apple推送通知服务服务器证书更新
feature: Technote, Push
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Apple推送通知服务服务器证书更新 {#apns-certificate-update}



2021年3月29日，Apple推送通知服务(APN)基础设施更新影响Adobe Campaign Classic iOS渠道。 OS配置更改是 **必需** 以避免iOS推送渠道中断。

详细了解APNs更改 [本页内容](https://developer.apple.com/news/?id=7gx0a2lp).

作为托管客户，无需执行任何操作：Adobe已将新的根证书并入您的环境。

作为内部部署/混合部署客户，您需要更新配置以确保无缝过渡 **2021年3月29日之前**.

要合并新证书，请执行以下步骤：

1. 下载 **AAACertificateServices 5/12/2020** 根证书 [从此页面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. 检查AAA证书是否同时存在于您的操作系统和JAVA信任库中。 如果不能，请添加它。

1. 重新启动Adobe Campaign Web服务：

   ```
   nlserver restart web
   ```
