---
product: campaign
title: 图像显示问题
description: 图像显示问题
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# 图像显示问题{#image-display-issues}



如果您在已发送的消息中遇到图像显示问题，原因可能与错误位置相关：

* 位置可能不匹配，或者图像可能未正确推送到重复的跟踪服务器：检查您的配置。
* 图像可能不位于营销实例的公共资源文件夹中：将图像上传到您的资源文件夹中，以解决此问题。
* 如果您在中间源架构中工作：发送校样时，检查图像在上传时没有出错（分析日志中显示信息）。

如何进行故障诊断：

1. 发送将显示图像的校样。
1. 验证实例设置中的资源配置是否正确。
1. 检查公共资源文件夹，如果不在公共资源文件夹中，则检查投放中引用的文件夹。
