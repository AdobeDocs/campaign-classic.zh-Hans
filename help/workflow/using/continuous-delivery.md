---
product: campaign
title: 连续投放
description: 连续投放
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 10%

---

# 连续投放{#continuous-delivery}

![](../../assets/common.svg)

**连续投放**&#x200B;类型操作允许您向现有投放添加新收件人。 此投放类型可避免您每次都必须创建新投放：此模式通常更有效，尤其是对于需要时发送的低容量警报或通知。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#continuous-delivery-video)

在投放模板级别，您可以指定一个脚本来计算关联投放的标签（和营销活动文件夹）。 如果脚本计算的投放尚不存在，则会即时创建该投放。

![](assets/edit_diffusion_fil.png)

**[!UICONTROL Process errors]**&#x200B;选项显示一个特定过渡，如果生成错误，该过渡将被激活。 在这种情况下，工作流不会进入错误模式并继续执行。

需考虑的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。

## 输入参数 {#input-parameters}

* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。

仅当选择&#x200B;**[!UICONTROL Specified by the inbound event]**&#x200B;选项时。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这组三个值用于标识由即时投放生成的目标。 **[!UICONTROL tableName]** 是用于存储目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms:recipient）， **[!UICONTROL recCount]** 是表中元素的数量。

与补码关联的过渡具有相同的参数。

## 如何设置连续投放

本节介绍如何设置连续投放。

**连续投放**&#x200B;允许您向现有投放添加新收件人，并避免在每次添加新收件人时都创建新投放。 您可以直接在营销活动工作流中更新创作内容，它将在投放模板资源文件夹中更新模板。

连续投放将创建单个投放和投放日志(broadLog)以及跟踪日志，这些日志引用每次执行一次投放时都添加一次投放。

![连续投放](assets/delivery_continuous.jpg)

## 教程视频 {#continuous-delivery-video}

本视频演示了如何使用增量查询配置连续投放。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

其他Campaign Classic操作方法视频可在[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)获取。
