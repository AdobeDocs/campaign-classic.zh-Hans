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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 模板发布{#template-publication}

在控件实例上创建的消息模板完成后，您可以在所有执行实例上发布它。 “发布”允许您在执行实例上自动创建两个消息模板，这允许您发送链接到实时和批处理事件的消息。

>[!CAUTION]
>
>请记住，只要您对模板做任何更改，就应该发布模板，以便这些更改在事务性消息传送过程中有效。

>[!NOTE]
>
>发布事务性消息模板时，类型学规则会自动发布到执行实例上。

1. 在控件实例中，转到树 **[!UICONTROL Message Center > Transactional message templates]** 的文件夹。
1. 选择要在执行实例上发布的模板。
1. 单击 **[!UICONTROL Publication]** .

   ![](assets/messagecenter_publish_model_008.png)

发布完成后，将在文件夹中生产实例树中创建要应用于批处理和实时类型事件的消息模板 **[!UICONTROL Administration > Production > Message Center > Default > Transactional message templates]** 。

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>如果将事务消息模板的现有字段（如发送者地址）替换为空值，则在事务消息再次发布后，执行实例上的相应字段将不会更新。 它仍将包含上一个值。 但是，如果添加非空值，则相应的字段将像往常一样在下一个发布后更新。

