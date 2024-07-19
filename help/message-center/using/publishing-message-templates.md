---
product: campaign
title: 发布消息模板
description: 了解Adobe Campaign Classic中的事务性消息模板发布和取消发布
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# 发布消息模板 {#publishing-template-messages}



## 模板发布 {#template-publication}

当在控制实例上创建的[消息模板](../../message-center/using/creating-the-message-template.md)完成，并且[测试了](../../message-center/using/testing-message-templates.md)该模板后，您就可以发布它。 此进程还将在所有执行实例上发布它。

发布允许您在执行实例上自动创建&#x200B;**两个消息模板**，这将允许您发送链接到&#x200B;**实时事件**&#x200B;和&#x200B;**批处理事件**&#x200B;的消息。

>[!NOTE]
>
>发布事务性消息模板时，也会在执行实例上自动发布分类规则。

>[!IMPORTANT]
>
>无论何时对模板进行更改，请确保再次发布模板，以便这些更改在事务型消息投放期间生效。

1. 在控制实例上，转到树的&#x200B;**[!UICONTROL Message Center > Transactional message templates]**&#x200B;文件夹。
1. 选择要在执行实例上发布的模板。
1. 单击 **[!UICONTROL Publish]**。

   ![](assets/messagecenter_publish_model_008.png)

发布完成后，将在&#x200B;**[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**&#x200B;文件夹的生产实例树中创建要应用于批次和实时类型事件的消息模板。

![](assets/messagecenter_deployed_model_001.png)

发布模板后，如果触发了相应的事件，执行实例将收到该事件，将其链接到事务型模板，并向每个收件人发送相应的事务型消息。 有关详细信息，请参阅[事件处理](../../message-center/using/about-event-processing.md)。

>[!NOTE]
>
>如果将事务型消息模板的现有字段（如发件人地址）替换为空值，则再次发布事务型消息后，执行实例上的相应字段将不会更新。 它仍将包含先前的值。
>
>但是，如果添加非空值，则相应的字段将在下次发布后正常更新。

## 模板取消发布 {#template-unpublication}

在执行实例上发布消息模板后，可以取消发布该模板。 有关模板发布过程的详细信息，请参阅[此部分](#template-publication)。

* 事实上，如果触发了相应的事件，仍可调用已发布的模板：如果您不再使用消息模板，则建议取消发布该模板。 这是为了避免错误地发送不需要的事务型消息。

  例如，您发布了一个消息模板，该模板仅用于圣诞节促销活动。 您可能需要在圣诞节结束后取消发布它，并在明年再次发布。

* 此外，您无法删除状态为&#x200B;**[!UICONTROL Published]**&#x200B;的事务性消息模板。 必须先取消发布它。

>[!NOTE]
>
>此功能从Campaign 20.2版本开始提供。

要取消发布事务型消息模板，请执行以下步骤。

1. 在控制实例上，转到树的&#x200B;**[!UICONTROL Message Center > Transactional message templates]**&#x200B;文件夹。
1. 选择要取消发布的模板。
1. 单击 **[!UICONTROL Unpublish]**。

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. 单击 **[!UICONTROL Start]**。

![](assets/message-center-unpublish.png)

事务性消息模板状态从&#x200B;**[!UICONTROL Published]**&#x200B;变回&#x200B;**[!UICONTROL Being edited]**。

取消发布完成后：

* 将从每个执行实例中删除消息模板（应用于批处理事件和实时类型事件）。

  它们不再出现在&#x200B;**[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]**&#x200B;文件夹中（请参阅[此部分](#template-publication)）。

* 取消发布模板后，您可以将其从控制实例中删除。

  要执行此操作，请从列表中选择它，然后单击屏幕右上角的&#x200B;**[!UICONTROL Delete]**&#x200B;按钮。
