---
title: 连续投放
seo-title: 连续投放
description: 连续投放
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
source-git-commit: 3566f42b92cc1b7280bf9b6e9e0b4da7a54f61db
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# 连续投放{#continuous-delivery}

通过 **连续投放** 类型操作，您可以向现有投放添加新收件人。 此投放类型可避免您每次都必须创建新投放:此模式通常更有效，尤其是对于需要时发送的低容量警报或通知。 在投放模板级别，您可以指定一个脚本来计算关联投放的标签(和活动文件夹)。 如果脚本计算尚不存在的投放，则会动态创建该脚本。

![](assets/edit_diffusion_fil.png)

该 **[!UICONTROL Process errors]** 选项显示将在生成错误时激活的特定过渡。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。

## 输入参数 {#input-parameters}

* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。

仅当选 **[!UICONTROL Specified by the inbound event]** 择该选项时。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识由动态目标产生的投放。 **[!UICONTROL tableName]** 是存储目标标识符的表的名称， **[!UICONTROL schema]** 是收件人的模式（通常是nms:） **[!UICONTROL recCount]** ，是表中元素的数量。

与补码关联的过渡具有相同的参数。

## 如何设置连续投放

本节介绍如何设置连续投放。

连续 **投放** 允许您向现有投放添加新收件人，并避免每次添加新收件人时必须创建新投放。 您可以直接在活动工作流中更新创意，它将更新投放模板资源文件夹中的模板。

连续投放将创建SINGLE投放和投放日志(broadLog)以及引用每次执行一个投放时都添加一个的跟踪日志。

![连续投放](assets/delivery_continuous.jpg)

此视频演示如何使用增量投放配置连续查询。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)
