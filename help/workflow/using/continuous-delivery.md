---
title: 持续交付
seo-title: 持续交付
description: 持续交付
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 持续交付{#continuous-delivery}

“连 **续传送类型** ”(Continuous delivery type)操作允许您向现有传送添加新收件人。 这种交付类型避免了您每次都必须创建新的交付：此模式通常更加有效，尤其是对于根据需要发送的小批量警报或通知。 在分发模板级别，您可以指定一个脚本来计算关联分发的标签（和系列活动文件夹）。 如果脚本计算尚不存在的交付，则会立即创建该交付。

![](assets/edit_diffusion_fil.png)

该选 **[!UICONTROL Process errors]** 项显示特定过渡，该过渡将在生成错误时被激活。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

仅当选中 **[!UICONTROL Specified by the inbound event]** 此选项时。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三个值集标识了由动态交付产生的目标。 **[!UICONTROL tableName]** 是存储目标标识符的表的名称，是 **[!UICONTROL schema]** 人口（通常nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素数。

与补码相关联的过渡具有相同的参数。
