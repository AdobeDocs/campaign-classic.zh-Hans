---
product: campaign
title: 导入和导出受众
description: 导入和导出受众
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 2%

---


# 导入和导出受众{#importing-and-exporting-audiences}



## 导入受众 {#importing-an-audience}

您可以通过收件人列表，将受众/区段从Audience Manager或People核心服务导入Adobe Campaign。

1. 转到 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** Adobe Campaign节点。
1. 在操作栏中，选择 **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. 在打开的窗口中，单击 **[!UICONTROL Select a shared audience]** 转到其他Adobe Experience Cloud解决方案中可用的共享受众/区段列表。
1. 选择受众并进行确认。 受众的信息会自动填写。

   请注意，为了能够导入共享受众，您应该被分配 **[!UICONTROL Audience library]** 产品，并且是Audience Manager的管理员。 有关详细信息，请参见 [Admin console文档](https://helpx.adobe.com/cn/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. 从中选择AMC数据源 **[!UICONTROL AMC Data source]** 字段，用于定义预期的数据类型。

   ![](assets/aam_import_audience_2.png)

1. 保存受众。

受众通过技术工作流导入。 导入的列表包含可以使用AMC数据源协调的元素。 Adobe Campaign无法识别的元素将不会导入。

直接从People核心服务或Audience Manager导入区段时，导入过程需要24-36小时才能同步。 在此时段后，您将能够在Adobe Campaign中查找和使用新受众。

>[!NOTE]
>
>如果您要将受众从Adobe Analytics导入Adobe Campaign，则需要首先在People核心服务或Audience Manager中共享这些受众。 此过程需要12-24小时，必须将其添加到与Campaign的24-36小时同步中。
>
>在该特定情况下，受众共享时间范围最长可达60小时。 有关在人员核心服务和Audience Manager中共享Adobe Analytics受众的更多信息，请参阅 [Adobe Analytics文档](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

每次同步受众数据时，受众数据都会被完全替换。 只能导入区段。 不支持包含键值对、特征和规则的粒度数据。

## 导出受众 {#exporting-an-audience}

您可以使用工作流将受众从Adobe Campaign导出到Audience Manager或People核心服务。 有关创建和使用工作流的详细流程，请参见 [本文档](../../workflow/using/building-a-workflow.md). 导出的受众将作为区段保存在People核心服务中：

1. 创建新的定位工作流。
1. 使用不同的可用活动，定位一组收件人。
1. 定向后，拖放 **[!UICONTROL Update shared audience]** 活动，然后打开它。

   ![](assets/aam_export_example.png)

1. 定义要通过导出的受众 **[!UICONTROL Select a shared audience]** 选项。 在打开的窗口中，您可以选择现有受众或创建新受众。

   如果选择现有受众，则只有新记录会添加到该受众。

   要将收件人列表导出到新受众，请完成 **[!UICONTROL Segment name]** 字段，然后单击 **[!UICONTROL Create]** ，然后再选择新创建的受众。

   单击窗口右上角的复选符号完成该操作，然后单击 **[!UICONTROL OK]** 按钮。

1. 选择 **[!UICONTROL AMC Data source]** 以指定预期的数据类型。 将自动确定架构。

   ![](assets/aam_export_audience_activity.png)

1. 保存受众。

随后将导出受众。 保存受众活动有两个叫客过渡。 主过渡包含已成功导出的收件人。 额外的过渡包含无法映射为访客ID或声明的ID的收件人。

Adobe Campaign与People核心服务之间的同步需要24-36小时。 在此时段后，您将能够在People核心服务中找到新受众，并在其他Adobe Experience Cloud解决方案中重复使用它。 有关在Adobe人员核心服务中使用Adobe Campaign共享受众的更多信息，请参阅此 [文档](https://experienceleague.adobe.com/docs/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>为了进行协调，记录必须具有Adobe Experience Cloud ID（“访客ID”或“声明的ID”）。 导出和导入受众时，将忽略没有Adobe Experience Cloud ID的记录。
