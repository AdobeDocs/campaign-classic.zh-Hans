---
solution: Campaign Classic
product: campaign
title: 导入和导出受众
description: 导入和导出受众
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---


# 导入和导出受众{#importing-and-exporting-audiences}

## 导入受众{#importing-an-audience}

您可以通过受众列表将受众管理器或人员核心服务中的收件人/区段导入Adobe Campaign。

1. 转到Adobe Campaign资源管理器中的&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]**&#x200B;节点。
1. 在操作栏中，选择&#x200B;**[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在打开的窗口中，单击&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;以转到其他Adobe Experience Cloud解决方案中可用的共享受众/区段的列表。
1. 选择受众并确认。 受众信息将自动完成。

   请注意，要能够导入共享受众，您应在管理控制台中分配&#x200B;**[!UICONTROL Audience library]**&#x200B;产品，并成为Audience Manager管理员。 有关详细信息，请参阅[管理控制台文档](https://helpx.adobe.com/cn/enterprise/managing/user-guide.html)。

   ![](assets/aam_import_audience_3.png)

1. 从&#x200B;**[!UICONTROL AMC Data source]**&#x200B;字段中选择AMC数据源以定义所需的数据类型。

   ![](assets/aam_import_audience_2.png)

1. 保存受众。

受众通过技术工作流导入。 导入的列表包含可使用AMC数据源对帐的元素。 不导入Adobe Campaign无法识别的元素。

从People核心服务或Audience Manager直接导入区段时，导入过程需要24-36小时才能同步。 在此期间后，您将能够在Adobe Campaign中查找和使用新受众。

>[!NOTE]
>
>如果要将受众从Adobe Analytics导入到Adobe Campaign，则首先需要在People Core Service或Audience Manager中共享这些受众。 此过程需要12-24小时，必须与活动同步24-36小时。
>
>在这种情况下，受众共享时间最长可达60小时。 有关People Core服务和受众管理器中Adobe Analytics受众共享的详细信息，请参阅此[文档](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-publish.html)。

每次受众时，都会完全替换该数据。 只能导入区段。 不支持包括键值对、特征和规则在内的粒度数据。

## 导出受众{#exporting-an-audience}

您可以使用工作流将受众从Adobe Campaign导出到受众管理器或人员核心服务。 创建和使用工作流的过程详见[此文档](../../workflow/using/building-a-workflow.md)。 导出的受众将作为区段保存在People核心服务中：

1. 创建新的定位工作流。
1. 使用可用的不同活动目标一组收件人。
1. 定位后，拖放&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活动，然后打开它。

   ![](assets/aam_export_example.png)

1. 定义要通过&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;选项导出的受众。 在打开的窗口中，您可以选择现有受众或创建新受众。

   如果您选择现有受众，则只会向受众添加新记录。

   要在新受众中导出收件人列表，请填写&#x200B;**[!UICONTROL Segment name]**&#x200B;字段，然后单击&#x200B;**[!UICONTROL Create]**，然后选择新创建的受众。

   单击窗口右上方的复选符号，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;按钮，即可完成操作。

1. 选择&#x200B;**[!UICONTROL AMC Data source]**&#x200B;以指定预期的数据类型。 模式自动确定。

   ![](assets/aam_export_audience_activity.png)

1. 保存受众。

然后导出受众。 保存受众活动有两个出站过渡。 主过渡包含成功导出的收件人。 附加过渡包含无法用访客ID或声明ID映射的收件人。

Adobe Campaign与人员核心服务之间的同步需要24-36小时。 在此期间之后，您将能够在People核心服务中找到新的受众，并在其他Adobe Experience Cloud解决方案中重复使用它。 有关在Adobe People核心服务中使用Adobe Campaign共享受众的详细信息，请参阅此[文档](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html)。

>[!NOTE]
>
>为了对帐，这些记录必须具有Adobe Experience Cloud ID(“访客ID”或“声明ID”)。 在导出和导入受众时，将忽略没有Adobe Experience Cloud ID的记录。

