---
product: campaign
title: 持续投放
description: 持续投放
feature: Workflows, Channels Activity
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 10%

---

# 持续投放{#continuous-delivery}



**连续投放**&#x200B;类型操作允许您向现有投放添加新收件人。 此投放类型使您每次都无需创建新投放：此模式通常更有效，尤其是对于在需要时发送的小流量警报或通知。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#continuous-delivery-video)

在投放模板级别，您可以指定脚本以计算关联投放的标签（和活动文件夹）。 如果脚本计算的投放尚不存在，则会动态创建。

![](assets/edit_diffusion_fil.png)

**[!UICONTROL Process errors]**&#x200B;选项显示特定过渡，如果生成错误，将激活该过渡。 在这种情况下，工作流不会进入错误模式并继续执行。

考虑的错误是文件系统错误（无法移动文件、无法访问目录等）。

此选项不处理与活动配置相关的错误，即无效值。

## 输入参数 {#input-parameters}

* 表名
* 模式

每个入站事件必须指定由这些参数定义的目标。

仅在选择了&#x200B;**[!UICONTROL Specified by the inbound event]**&#x200B;选项时。

## 输出参数 {#output-parameters}

* 表名
* 模式
* recCount

这组三个值标识动态投放产生的目标。 **[!UICONTROL tableName]**&#x200B;是存储目标标识符的表的名称，**[!UICONTROL schema]**&#x200B;是群体的架构（通常为nms：recipient），**[!UICONTROL recCount]**&#x200B;是表中的元素数。

与补充关联的转换具有相同的参数。

## 如何设置连续投放

本节介绍如何设置连续投放。

**连续投放**&#x200B;允许您向现有投放添加新收件人，并避免每次添加新收件人时都必须创建新投放。 您可以直接在活动工作流中更新创意，活动工作流将更新投放模板资源文件夹中的模板。

连续投放将创建单个投放和投放日志(broadLog)以及跟踪日志，日志引用每次执行投放时添加一个投放。

![连续投放](assets/delivery_continuous.jpg)

## 教程视频 {#continuous-delivery-video}

本视频演示了如何使用增量查询配置连续投放。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign Classic操作方法视频。
