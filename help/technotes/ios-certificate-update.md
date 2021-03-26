---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 08c6e84e07da2811c91aa58ddf40c5781de2b163
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Apple推送通知服务服务器证书更新{#apns-certificate-update}

2021年3月29日，Apple推送通知服务(APNs)基础架构更新将影响Adobe Campaign Classic iOS渠道。 操作系统配置更改为&#x200B;**mandatory**&#x200B;以避免iOS推送渠道中断。

了解有关APNs更改[的更多信息，请参阅本页](https://developer.apple.com/news/?id=7gx0a2lp)。

作为托管客户，无需执行任何操作：Adobe已将新根证书并入您的环境。

作为内部部署/混合型客户，您需要更新配置以确保在2021年3月29日之前实现&#x200B;**的无缝过渡。**

要合并新证书，请执行以下步骤：

1. 从此页面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)下载&#x200B;**AAACertificateServices 5/12/2020**&#x200B;根证书[。

1. 检查OS和JAVA信任库中均存在AAA证书。 否则，添加。

1. 重新启动Adobe Campaign Web服务：

   ```
   nlserver restart web
   ```

