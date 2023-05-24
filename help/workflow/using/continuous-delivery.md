---
product: campaign
title: 连续投放
description: 连续投放
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 10%

---

# 连续投放{#continuous-delivery}



A **连续投放** type操作允许您将新收件人添加到现有投放。 此投放类型可避免您每次都创建新投放：此模式通常更有效，尤其是对于在需要时发送的小量警报或通知。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#continuous-delivery-video)

在投放模板级别，您可以指定一个脚本来计算关联投放的标签（和营销活动文件夹）。 如果脚本计算的投放尚不存在，则会动态创建。

![](assets/edit_diffusion_fil.png)

此 **[!UICONTROL Process errors]** 选项显示特定过渡，如果生成错误，将激活该过渡。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件都必须指定由这些参数定义的目标。

仅当 **[!UICONTROL Specified by the inbound event]** 选项。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识动态投放产生的目标。 **[!UICONTROL tableName]** 是存储目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

与补充关联的过渡具有相同的参数。

## 如何设置连续投放

本节介绍如何设置连续投放。

此 **连续投放** 允许您将新收件人添加到现有投放，并避免每次添加新收件人时都必须创建新投放。 您可以直接在活动工作流中更新创意，它将会更新投放模板资源文件夹中的模板。

连续投放将创建单个投放和投放日志(broadLog)以及跟踪日志，这些日志引用每次执行投放时都添加一个投放。

![连续投放](assets/delivery_continuous.jpg)

## 教程视频 {#continuous-delivery-video}

本视频演示了如何使用增量查询配置连续投放。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
