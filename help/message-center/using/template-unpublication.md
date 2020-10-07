---
title: 模板发布
seo-title: 模板发布
description: 模板发布
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 4%

---


# 模板取消发布{#template-unpublication}

在执行实例上发布消息模板后，即可取消发布该消息模板。

>[!NOTE]
>
>此功能可从活动20.2版开始使用。

事实上，仍可以调用已发布的模板。 因此，如果您不再使用消息模板，建议取消发布该模板。 这是为了避免误发送不需要的事务性消息。 例如，您发布了仅用于圣诞节活动的消息模板。 在圣诞节结束后，您可能希望取消发布它，并在明年再次发布它。

此外，无法删除具有状态的 **[!UICONTROL Published]** 事务性消息模板。 必须先取消发布它。

要取消发布事务性消息模板，请按照以下步骤操作。

1. 在控制实例中，转 **[!UICONTROL Message Center > Transactional message templates]** 到树的文件夹。
1. 选择要取消发布的模板。
1. 单击 **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. 单击 **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

事务性消息模板状态从变 **[!UICONTROL Published]** 回 **[!UICONTROL Being edited]**&#x200B;为。

取消发布完成后：

* 两个消息模板(应用于批处理和实时类型事件)均从每个执行实例中删除。 文件夹中不再显示这 **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** 些文件。

* 取消发布模板后，您可以根据需要从控制实例中删除它。 为此，请从列表中选择它，然 **[!UICONTROL Delete]** 后单击屏幕右上方的按钮。