---
product: campaign
title: 图像显示问题
description: 图像显示问题
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 11%

---

# 图像显示问题{#image-display-issues}



如果您在发送的消息中遇到图像显示问题，原因可能与错误位置有关：

* 位置可能不匹配，或者图像可能未正确推送到重复的跟踪服务器：请检查您的配置。
* 图像可能不在营销实例的公共资源文件夹中：请将图像上传到资源文件夹以解决该问题。
* 如果您在中间源架构中工作：发送验证时，检查图像上传且没有错误（分析日志中显示信息）。

如何进行故障排除：

1. 发送将显示图像的校样。
1. 验证实例设置中的资源配置是否正确。
1. 检查公共资源文件夹，如果不在公共资源文件夹中，则检查投放中引用的文件夹。
