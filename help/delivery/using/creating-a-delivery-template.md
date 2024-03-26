---
product: campaign
title: 创建投放模板
description: 创建投放模板
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Delivery Templates
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 7%

---

# 创建投放模板{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#delivery-template-video)

## 将现有投放转换为模板 {#converting-an-existing-delivery-to-a-template}

投放可以转换为模板，以便执行新的重复投放操作。 要将投放转换为模板，请从投放列表中选择它，可通过访问模板 **[!UICONTROL Campaign management]** 树节点。

右键单击并选择 **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

此操作根据选定的投放创建一个投放模板。 您必须输入保存该文件的文件夹(在 **[!UICONTROL Folder]** 字段)以及根据此模板创建的投放所在的文件夹(在 **[!UICONTROL Execution folder]** 字段)。

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

有关配置模式的详细信息，请参阅 [将模板链接到投放](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## 创建新模板 {#creating-a-new-template}

>[!NOTE]
>
>为避免配置错误，Adobe建议您复制本机模板并自定义其设置，而不是创建新模板。

要配置投放模板，请执行以下步骤：

1. 打开Campaign Explorer。
1. 在 **资源** 文件夹，选择 **模板** 则 **投放模板**.

   ![](assets/delivery_template_1.png)

1. 单击 **新建** ，以创建新投放模板，或者 **复制** 现有模板。

   ![](assets/delivery_template_2.png)

1. 修改 **标签** 和 **内部名称** 文件夹的。
1. 保存并重新打开模板。
1. 单击 **属性** 按钮，然后根据您的要求修改值。

   ![](assets/delivery_template_3.png)

1. 在 **常规** 选项卡，确认或更改在 **执行文件夹**， **文件夹**、和 **路由** 下拉菜单。

   ![](assets/delivery_template_4.png)

1. 完成 **电子邮件参数** 类别中包含您的电子邮件主题和目标群体。
1. 添加您的 **HTML内容** 要个性化您的模板，您可以显示镜像页面链接和退订链接。
1. 选择 **预览** 选项卡。 在 **测试个性化** 下拉菜单，选择 **收件人** 以预览模板作为所选用户档案。

   ![](assets/delivery_template_5.png)

1. 单击 **保存**. 您的模板现已准备就绪，可用于投放。


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

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
