---
product: campaign
title: 创建投放模板
description: 创建投放模板
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Delivery Templates
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 7%

---

# 创建投放模板{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#delivery-template-video)

## 将现有投放转换为模板 {#converting-an-existing-delivery-to-a-template}

投放可以转换为模板，以便执行新的重复投放操作。 要将投放转换为模板，请从可通过树的&#x200B;**[!UICONTROL Campaign management]**&#x200B;节点访问的投放列表中选择该投放。

右键单击并选择&#x200B;**[!UICONTROL Actions > Save as template...]**。

![](assets/s_ncs_user_campaign_save_as_scenario.png)

此操作根据选定的投放创建一个投放模板。 您必须输入保存该投放的文件夹（在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中）以及基于此模板创建的投放的文件夹（在&#x200B;**[!UICONTROL Execution folder]**&#x200B;字段中）。

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

有关配置模式的详细信息，请参阅[将模板链接到投放](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery)。

## 创建新模板 {#creating-a-new-template}

>[!NOTE]
>
>为避免配置错误，Adobe建议您复制本机模板并自定义其设置，而不是创建新模板。

要配置投放模板，请执行以下步骤：

1. 打开Campaign Explorer。
1. 在&#x200B;**资源**&#x200B;文件夹中，选择&#x200B;**模板**，然后选择&#x200B;**投放模板**。

   ![](assets/delivery_template_1.png)

1. 单击工具栏中的&#x200B;**新建**&#x200B;以创建新的投放模板，或单击&#x200B;**复制**&#x200B;现有模板。

   ![](assets/delivery_template_2.png)

1. 修改文件夹的&#x200B;**标签**&#x200B;和&#x200B;**内部名称**。
1. 保存并重新打开模板。
1. 单击&#x200B;**属性**&#x200B;按钮，然后根据您的要求修改值。

   ![](assets/delivery_template_3.png)

1. 在&#x200B;**常规**&#x200B;选项卡中，确认或更改在&#x200B;**执行文件夹**、**文件夹**&#x200B;和&#x200B;**路由**&#x200B;下拉菜单中选定的位置。

   ![](assets/delivery_template_4.png)

1. 使用您的电子邮件主题和目标群体完成&#x200B;**电子邮件参数**&#x200B;类别。
1. 添加您的&#x200B;**HTML内容**&#x200B;以个性化您的模板，您可以显示镜像页面链接和退订链接。
1. 选择&#x200B;**预览**&#x200B;选项卡。 在&#x200B;**测试个性化**&#x200B;下拉菜单中，选择&#x200B;**收件人**&#x200B;以预览您的模板作为所选配置文件。

   ![](assets/delivery_template_5.png)

1. 单击&#x200B;**保存**。 您的模板现已准备就绪，可用于投放。


## 教程视频 {#delivery-template-video}

### 如何配置投放模板

以下视频演示了如何为临时投放配置模板。

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### 如何设置投放模板属性

以下视频介绍了如何设置投放模板属性，并详细说明每个属性。

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### 如何部署临时投放模板

此视频介绍了如何部署临时电子邮件投放模板，并说明了电子邮件投放与投放工作流之间的区别。

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign Classic操作方法视频。
