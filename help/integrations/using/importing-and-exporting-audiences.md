---
product: campaign
title: 导入和导出受众
description: 导入和导出受众
feature: Audiences
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---


# 导入和导出受众{#importing-and-exporting-audiences}



## 导入受众 {#importing-an-audience}

您可以通过收件人列表，将受众/区段从Audience Manager导入Adobe Campaign。

1. 转到Adobe Campaign资源管理器中的&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]**&#x200B;节点。
1. 在操作栏中选择&#x200B;**[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在打开的窗口中，单击&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;以转到可从其他Adobe Experience Cloud解决方案访问的共享受众/区段列表。
1. 选择受众并进行确认。 受众的信息会自动填写。

   请注意，为了能够导入共享受众，您应该在Admin Console中获得&#x200B;**[!UICONTROL Audience library]**&#x200B;产品，并成为Audience Manager的管理员。 有关详细信息，请参阅[管理控制台文档](https://helpx.adobe.com/cn/enterprise/managing/user-guide.html)。

   ![](assets/aam_import_audience_3.png)

1. 从&#x200B;**[!UICONTROL AMC Data source]**&#x200B;字段中选择AMC数据源以定义预期的数据类型。

   ![](assets/aam_import_audience_2.png)

1. 保存受众。

受众通过技术工作流导入。 导入的列表包含可以使用AMC数据源协调的元素。 Adobe Campaign无法识别的元素将不会导入。

直接从Audience Manager导入区段时，导入过程需要24-36小时才能同步。 在此时段后，您将能够在Adobe Campaign中查找和使用新受众。

>[!NOTE]
>
>如果您要将受众从Adobe Analytics导入Adobe Campaign，则需要首先在Audience Manager中共享这些受众。 此过程需要12-24小时，必须将其添加到与Campaign的24-36小时同步中。
>
>在该特定情况下，受众共享时间范围最长可达60小时。 有关在Audience Manager中共享Adobe Analytics受众的更多信息，请参阅[Adobe Analytics文档](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hans){target="_blank"}。

每次同步受众数据时，受众数据都会被完全替换。 只能导入区段。 不支持包含键值对、特征和规则的粒度数据。

## 导出受众 {#exporting-an-audience}

您可以使用工作流将受众从Adobe Campaign导出到Audience Manager。 [本文档](../../workflow/using/building-a-workflow.md)中详细介绍了创建和使用工作流的过程。 导出的受众将另存为区段：

1. 创建新的定位工作流。
1. 使用不同的可用活动，定位一组收件人。
1. 定向后，拖放&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活动，然后将其打开。

   ![](assets/aam_export_example.png)

1. 定义要通过&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;选项导出的受众。 在打开的窗口中，您可以选择现有受众或创建新受众。

   如果选择现有受众，则只有新记录会添加到该受众。

   要在新受众中导出收件人列表，请先填写&#x200B;**[!UICONTROL Segment name]**&#x200B;字段，然后单击&#x200B;**[!UICONTROL Create]**，然后再选择新创建的受众。

   单击窗口右上角的复选符号，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;按钮完成该操作。

1. 选择&#x200B;**[!UICONTROL AMC Data source]**&#x200B;以指定预期的数据类型。 将自动确定架构。

   ![](assets/aam_export_audience_activity.png)

1. 保存受众。

随后将导出受众。 保存受众活动有两个叫客过渡。 主过渡包含已成功导出的收件人。 额外的过渡包含无法映射为访客ID或声明的ID的收件人。

解决方案之间的同步需要24 - 36个小时。 在此时段后，您将能够找到新受众，并在其他Adobe Experience Cloud解决方案中重复使用它。 有关使用Adobe Campaign共享受众的更多信息，请参阅此[文档](https://experienceleague.adobe.com/zh-hans/docs/core-services/interface/services/audiences/create){target="_blank"}。

>[!NOTE]
>
>为了进行协调，记录必须具有Adobe Experience Cloud ID（“访客ID”或“声明的ID”）。 导出和导入受众时，将忽略没有Adobe Experience Cloud ID的记录。
