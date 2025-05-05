---
product: campaign
title: 技术说明 — Apple推送通知服务服务器证书更新
description: Apple推送通知服务服务器证书更新
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Apple推送通知服务服务器证书更新 {#apns-certificate-update}



2024年10月17日，Apple推送通知服务(APN)基础架构更新影响Adobe Campaign Classic iOS渠道。 操作系统配置更改是&#x200B;**必需的**，这样可避免iOS推送渠道中断。

在此页面[&#128279;](https://developer.apple.com/news/?id=09za8wzy)中了解有关APN更改的更多信息。

作为托管客户，无需执行任何操作：Adobe已将新的根证书并入您的环境。

作为内部部署/混合部署客户，您需要更新配置以确保在2025年2月24日之前实现无缝过渡&#x200B;**&#x200B;**。

要合并新证书，请执行以下步骤：

1. 从此页面[&#128279;](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO)下载&#x200B;**SHA-2根：USERTrust RSA Certification Authority证书**&#x200B;根证书。

1. 检查AAA证书是否同时存在于您的操作系统和JAVA信任库中。 如果不能，请添加它。

1. 重新启动Adobe Campaign Web服务：

   ```
   nlserver restart web
   ```
