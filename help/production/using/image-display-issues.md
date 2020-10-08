---
title: 图像显示问题
seo-title: 图像显示问题
description: 图像显示问题
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 8%

---


# 图像显示问题{#image-display-issues}

如果您在已发送的邮件中遇到图像显示问题，原因可能与错误位置相关：

* 位置可能不匹配，或者图像可能未正确推送到重复跟踪服务器：检查配置。
* 图像不能驻留在营销实例的公共资源文件夹中：将图像上传到您的资源文件夹中以解决此问题。
* 如果您使用的是中间源架构：发送验证时，检查图像上传时没有错误(信息显示在分析日志中)。

如何进行疑难解答：

1. 发送将显示图像的验证。
1. 验证实例设置中的资源配置是否正确。
1. 检查公共资源文件夹，或者(如果它不在公共资源文件夹中)检查投放中引用的文件夹。

