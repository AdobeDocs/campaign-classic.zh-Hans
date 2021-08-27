---
product: campaign
title: 技术说明
description: 技术说明
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Apple推送通知服务服务器证书更新 {#apns-certificate-update}

![](../../assets/v7-only.svg)

2021年3月29日，Apple推送通知服务(APNs)基础架构更新将影响Adobe Campaign Classic iOS渠道。 要避免iOS推送渠道中断，操作系统配置更改为&#x200B;**必需**。

在本页](https://developer.apple.com/news/?id=7gx0a2lp)中了解有关APNs更改[的更多信息。

作为托管客户，无需执行任何操作：Adobe已将新的根证书纳入到您的环境中。

作为内部部署/混合型客户，您需要更新配置以确保在2021年3月29日之前实现无缝过渡&#x200B;****。

要合并新证书，请执行以下步骤：

1. 从此页面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)下载&#x200B;**AACertificateServices 5/12/2020**&#x200B;根证书[。

1. 检查OS和JAVA Trustores中均存在AAA证书。 如果没有，请添加。

1. 重新启动Adobe Campaign Web服务：

   ```
   nlserver restart web
   ```
