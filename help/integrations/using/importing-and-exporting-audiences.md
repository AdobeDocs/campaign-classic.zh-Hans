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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Importing and exporting audiences{#importing-and-exporting-audiences}

## 导入受众 {#importing-an-audience}

您可以通过收件人列表将受众／区段从Audience Manager或People核心服务导入Adobe Campaign。

1. 转到Adobe Campaign资 **[!UICONTROL Profiles and Targets]** 源管 **[!UICONTROL Lists]** 理器中的>节点。
1. 在操作栏中，选择 **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在打开的窗口中，单 **[!UICONTROL Select a shared audience]** 击以转到其他Adobe Experience cloud解决方案中可用的共享受众／区段列表。
1. 选择受众并进行确认。 受众信息会自动完成。

   请注意，要能够导入共享的受众，您应该在管理控制台中为 **[!UICONTROL Audience library]** 您分配产品，并成为Audience manager中的管理员。 有关详细信息，请参阅 [Admin Console文档](https://helpx.adobe.com/enterprise/managing/user-guide.html)。

   ![](assets/aam_import_audience_3.png)

1. 从字段中选择AMC数 **[!UICONTROL AMC Data source]** 据源以定义所需的数据类型。

   ![](assets/aam_import_audience_2.png)

1. 拯救受众。

受众通过技术工作流导入。 导入的列表包含可使用AMC数据源调节的元素。 Adobe Campaign无法识别的元素不会导入。

从People核心服务或Audience manager直接导入区段时，导入过程需要24到36小时才能同步。 在此期间后，您将能够在Adobe Campaign中查找和使用您的新受众。

>[!NOTE]
>
>如果要将受众从Adobe Analytics导入Adobe Campaign，则需要首先在People Core service或Audience Manager中共享这些受众。 此过程需要12-24小时，必须将其添加到与Campaign的24-36小时同步中。
>
>在这种情况下，受众共享的时间范围最长可达60小时。 有关People Core服务和Audience Manager中Adobe Analytics受众共享的更多信息，请参阅此 [文档](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html)。

每次同步时，受众数据都会被完全替换。 只能导入区段。 不支持包括键值对、特征和规则在内的粒度数据。

## 导出受众 {#exporting-an-audience}

您可以使用工作流将受众从Adobe Campaign导出到Audience Manager或People核心服务。 本文档详细介绍了创建和使用工作流 [的过程](../../workflow/using/building-a-workflow.md)。 导出的受众会作为区段保存在People核心服务中：

1. 创建新的定位工作流。
1. 使用可用的不同活动定位一组收件人。
1. 定位后，拖放活动， **[!UICONTROL Update shared audience]** 然后打开它。

   ![](assets/aam_export_example.png)

1. 定义要通过选项导出的受 **[!UICONTROL Select a shared audience]** 众。 在打开的窗口中，您可以选择现有受众或创建新受众。

   如果您选择现有受众，则只会向受众添加新记录。

   要导出新受众中的收件人列表，请填写字段，然 **[!UICONTROL Segment name]** 后单击，然 **[!UICONTROL Create]** 后选择新创建的受众。

   单击窗口右上方的复选符号，然后单击按钮，即可完成操 **[!UICONTROL OK]** 作。

1. 选择 **[!UICONTROL AMC Data source]** 以指定预期的数据类型。 此架构将自动确定。

   ![](assets/aam_export_audience_activity.png)

1. 拯救受众。

随后将导出受众。 保存的受众活动有两个出站过渡。 主转换包含成功导出的收件人。 附加的过渡包含无法用访客ID或声明ID映射的收件人。

Adobe Campaign与People核心服务之间的同步需要24-36小时。 在此期间后，您将能够在People核心服务中找到新的受众，并在其他Adobe Experience cloud解决方案中重复使用它。 有关在Adobe People核心服务中使用Adobe Campaign共享受众的更多信息，请参阅此 [文档](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html)。

>[!NOTE]
>
>要进行核对，记录必须具有Adobe Experience Cloud ID（“访客ID”或“声明ID”）。 导出和导入受众时，将忽略没有Adobe Experience Cloud ID的记录。

