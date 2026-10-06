---
product: campaign
title: 恢复
description: 恢复
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
TQID: 'https://experienceleague.adobe.com/ZXUhBpNXWOjaLlJ0U1ToxAi9HlC0AKenRKIIu0z-63c'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 25%
---
# 恢复{#restoration}



在干净的服务器上，恢复过程如下：

* 在已安装并配置的操作系统（网络）上，
* 安装第三方应用程序：Web服务器、JDK（如有必要）、
* 安装与源系统具有相同内部版本的Adobe Campaign二进制文件，
* 复制配置文件、跟踪日志和重定向文件，
* 创建和重建数据库，
* 启动Adobe Campaign。

有关详细信息，请参阅&#x200B;**安装指南**。
