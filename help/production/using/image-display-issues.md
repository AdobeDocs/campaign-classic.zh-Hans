---
solution: Campaign Classic
product: campaign
title: 图像显示问题
description: 图像显示问题
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# 图像显示问题{#image-display-issues}

如果您在已发送的邮件中遇到图像显示问题，原因可能与错误位置相关：

* 位置可能不匹配，或者图像可能未正确推送到重复跟踪服务器：检查您的配置。
* 图像不能驻留在营销实例的公共资源文件夹中：将图像上传到您的资源文件夹中可解决此问题。
* 如果您使用的是中间源架构：发送验证时，检查图像上传时没有错误(信息显示在分析日志中)。

如何进行疑难解答：

1. 发送将显示图像的验证。
1. 验证实例设置中的资源配置是否正确。
1. 检查公共资源文件夹，如果不在公共资源文件夹中，则检查投放中引用的文件夹。
