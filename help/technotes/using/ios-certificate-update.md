---
product: campaign
title: 技术说明 — Apple推送通知服务服务器证书更新
description: Apple推送通知服务服务器证书更新
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Apple推送通知服务服务器证书更新 {#apns-certificate-update}



2021年3月29日，Apple推送通知服务(APNs)基础架构更新影响了Adobe Campaign Classic iOS渠道。 操作系统配置更改为 **强制** 以避免iOS推送渠道中断。

进一步了解APNs的更改 [本页](https://developer.apple.com/news/?id=7gx0a2lp).

作为托管客户，无需执行任何操作：Adobe已将新的根证书纳入到您的环境中。

作为内部部署/混合客户，您需要更新配置以确保无缝过渡 **2021年3月29日之前**.

要合并新证书，请执行以下步骤：

1. 下载 **AACertificateServices 5/12/2020** 根证书 [从此页](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. 检查OS和JAVA Trustores中均存在AAA证书。 如果没有，请添加。

1. 重新启动Adobe Campaign Web服务：

   ```
   nlserver restart web
   ```
