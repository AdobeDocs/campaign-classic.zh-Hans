---
title: 导入和导出受众
seo-title: 导入和导出受众
description: 导入和导出受众
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---


# 导入和导出受众{#importing-and-exporting-audiences}

## 导入受众 {#importing-an-audience}

您可以通过受众列表将受众管理器或人员核心服务中的Adobe Campaign/细分导入收件人。

1. 转到Adobe Campaign **[!UICONTROL Profiles and Targets]** 资 **[!UICONTROL Lists]** 源管理器中的>节点。
1. 在操作栏中，选择 **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在打开的窗口中，单 **[!UICONTROL Select a shared audience]** 击以转至其他Adobe Experience Cloud解决方案提供的共享受众/区段的列表。
1. 选择受众并进行确认。 受众信息将自动完成。

   请注意，要能够导入共享受众，您应在管理控制台中 **[!UICONTROL Audience library]** 分配产品，并成为Audience Manager中的管理员。 For more on this, refer to the [Admin console documentation](https://helpx.adobe.com/cn/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. 从字段中选择AMC数 **[!UICONTROL AMC Data source]** 据源以定义所需的数据类型。

   ![](assets/aam_import_audience_2.png)

1. 保存受众。

受众通过技术工作流导入。 导入的列表包含可使用AMC数据源调节的元素。 Adobe Campaign无法识别的元素不会导入。

当区段直接从People核心服务或Audience Manager导入时，导入过程需要24到36小时进行同步。 在此期间后，您将能够在Adobe Campaign中查找和使用新受众。

>[!NOTE]
>
>如果要将受众从Adobe Analytics导入Adobe Campaign，则首先需要在People Core Service或Audience Manager中共享这些受众。 此过程需要12-24小时，必须与活动在24-36小时内进行同步。
>
>在这种情况下，受众共享时间最长可达60小时。 有关People Core服务和Adobe Analytics经理中的受众受众共享的详细信息，请参阅本 [文档](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-publish.html)。

每次同步受众数据时，将完全替换数据。 只能导入区段。 不支持包括键值对、特征和规则在内的粒度数据。

## 导出受众 {#exporting-an-audience}

您可以使用工作流将受众从Adobe Campaign导出到受众管理器或人员核心服务。 此文档详细介绍了创建和使用工作流 [的过程](../../workflow/using/building-a-workflow.md)。 导出的受众会作为区段保存在People核心服务中：

1. 创建新的定位工作流。
1. 使用不同的可用活动目标一组收件人。
1. 定位后，拖放一个 **[!UICONTROL Update shared audience]** 活动，然后打开它。

   ![](assets/aam_export_example.png)

1. 定义要通过选项导出的 **[!UICONTROL Select a shared audience]** 受众。 在打开的窗口中，您可以选择现有受众或创建新受众。

   如果您选择现有受众，则只会向受众添加新记录。

   要在新受众中导出收件人列表，请填写字 **[!UICONTROL Segment name]** 段，然后单 **[!UICONTROL Create]** 击，然后选择新创建的受众。

   单击窗口右上方的复选符号，然后单击按钮，完成操 **[!UICONTROL OK]** 作。

1. 选择 **[!UICONTROL AMC Data source]** 以指定预期的数据类型。 模式自动确定。

   ![](assets/aam_export_audience_activity.png)

1. 保存受众。

然后，将导出受众。 保存受众活动具有两个出站过渡。 主过渡包含成功导出的收件人。 附加过渡包含无法用访客ID或声明ID映射的收件人。

Adobe Campaign与人员核心服务之间的同步需要24到36小时。 在此期间，您将能够在People核心服务中找到新的受众，并在其他Adobe Experience Cloud解决方案中重复使用它。 有关在Adobe Campaign人员核心服务中使用受众共享Adobe的详细信息，请参阅本 [文档](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html)。

>[!NOTE]
>
>为了进行核对，记录必须具有Adobe Experience CloudID(“访客ID”或“声明ID”)。 在导出和导入受众时，不具有Adobe Experience CloudID的记录将被忽略。

