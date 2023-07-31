---
product: campaign
title: 发布消息模板
description: 了解Adobe Campaign Classic中的事务性消息模板发布和取消发布
feature: Transactional Messaging, Message Center, Templates
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# 发布消息模板 {#publishing-template-messages}



## 模板发布 {#template-publication}

当 [消息模板](../../message-center/using/creating-the-message-template.md) 在控制实例上创建的操作即完成，并且您可以 [已测试](../../message-center/using/testing-message-templates.md) 你可以发布它。 此进程还将在所有执行实例上发布它。

通过发布，您可以自动创建 **两个消息模板** ，这将允许您发送链接到的消息 **实时事件** 和 **批次事件**.

>[!NOTE]
>
>发布事务性消息模板时，也会在执行实例上自动发布分类规则。

>[!IMPORTANT]
>
>无论何时对模板进行更改，请确保再次发布模板，以便这些更改在事务型消息投放期间生效。

1. 在控制实例上，转到 **[!UICONTROL Message Center > Transactional message templates]** 树的文件夹。
1. 选择要在执行实例上发布的模板。
1. 单击 **[!UICONTROL Publish]**。

   ![](assets/messagecenter_publish_model_008.png)

发布完成后，将在的生产实例的树中创建要应用于批量事件和实时类型事件的消息模板 **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** 文件夹。

![](assets/messagecenter_deployed_model_001.png)

发布模板后，如果触发了相应的事件，执行实例将收到该事件，将其链接到事务型模板，并向每个收件人发送相应的事务型消息。 有关此内容的更多信息，请参阅 [事件处理](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>如果将事务型消息模板的现有字段（如发件人地址）替换为空值，则再次发布事务型消息后，执行实例上的相应字段将不会更新。 它仍将包含先前的值。
>
>但是，如果添加非空值，则相应的字段将在下次发布后正常更新。

## 模板取消发布 {#template-unpublication}

在执行实例上发布消息模板后，可以取消发布该模板。 有关模板发布过程的更多信息，请参阅 [本节](#template-publication).

* 事实上，如果触发了相应的事件，仍可调用已发布的模板：如果您不再使用消息模板，则建议取消发布该模板。 这是为了避免错误地发送不需要的事务型消息。

  例如，您发布了一个消息模板，该模板仅用于圣诞节促销活动。 您可能需要在圣诞节结束后取消发布它，并在明年再次发布。

* 此外，无法删除具有以下特征的事务型消息模板： **[!UICONTROL Published]** 状态。 必须先取消发布它。

>[!NOTE]
>
>此功能从Campaign 20.2版本开始提供。

要取消发布事务型消息模板，请执行以下步骤。

1. 在控制实例上，转到 **[!UICONTROL Message Center > Transactional message templates]** 树的文件夹。
1. 选择要取消发布的模板。
1. 单击 **[!UICONTROL Unpublish]**。

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. 单击 **[!UICONTROL Start]**。

![](assets/message-center-unpublish.png)

事务性消息模板状态会更改回 **[!UICONTROL Published]** 到 **[!UICONTROL Being edited]**.

取消发布完成后：

* 将从每个执行实例中删除消息模板（应用于批处理事件和实时类型事件）。

  它们不再出现在 **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** 文件夹(请参阅 [本节](#template-publication))。

* 取消发布模板后，您可以将其从控制实例中删除。

  要执行此操作，请从列表中选择它，然后单击 **[!UICONTROL Delete]** 按钮。
