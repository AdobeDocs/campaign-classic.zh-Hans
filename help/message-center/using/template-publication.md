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
source-wordcount: '206'
ht-degree: 4%

---


# 模板发布{#template-publication}

在控制实例上创建的消息模板完成后，您可以在所有执行实例上发布它。 “出版物”允许您在执行实例上自动创建两个消息模板，以便发送链接到实时消息和批次事件的消息。

>[!IMPORTANT]
>
>请记住，只要您对模板进行任何更改，就应发布模板，以使这些更改在事务性消息投放下有效。

>[!NOTE]
>
>发布事务性消息模板时，类型规则会自动发布到执行实例。

1. 在控制实例中，转 **[!UICONTROL Message Center > Transactional message templates]** 到树的文件夹。
1. 选择要在执行实例上发布的模板。
1. 单击 **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

发布完成后，将在文件夹中生产实例的树中创建要应用于批处理和实时类型事件的消息模 **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** 板。

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>如果将事务性消息模板的现有字段（如发送者地址）替换为空值，则执行实例上的相应字段在再次发布事务性消息后将不会更新。 它仍将包含上一个值。 但是，如果添加非空值，则在下次发布后，相应字段将像往常一样进行更新。
