---
solution: Campaign Classic
product: campaign
title: 测试事务型消息模板
description: 了解如何管理事务型消息中的种子地址，以便在Adobe Campaign Classic中预览和测试它们。
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: a9054fb8e10bef37675922b2f81c7615cd04c1bb
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 2%

---

# 测试事务型消息模板{#testing-message-templates}

[消息模板](../../message-center/using/creating-the-message-template.md)准备就绪后，请按照以下步骤进行预览和测试。

## 管理事务性消息中的种子地址 {#managing-seed-addresses-in-transactional-messages}

种子地址允许您在发送电子邮件或短信之前显示消息预览、发送校样并测试消息个性化。 种子地址已链接到投放，无法用于其他投放。

要在事务型消息中创建种子地址，请执行以下步骤：

1. 在事务型消息模板中，单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡。

   ![](assets/messagecenter_create_seedaddr_001.png)

1. 为其分配标签以供日后选择。

   ![](assets/messagecenter_create_seedaddr_002.png)

1. 输入种子地址（根据通信渠道，可使用电子邮件或手机）。

   ![](assets/messagecenter_create_seedaddr_003.png)

1. 输入外部标识符：此可选字段允许您输入业务键（唯一ID、名称+电子邮件等） 网站上所有用于标识用户档案的应用程序都通用的配置文件。 如果此字段也存在于Adobe Campaign营销数据库中，则可以将事件与数据库中的用户档案进行协调。

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. 插入测试数据（请参阅[个性化数据](#personalization-data)）。

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. 单击&#x200B;**[!UICONTROL Add other seed addresses]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. 重复该过程以根据需要创建任意数量的地址。

   ![](assets/messagecenter_create_seedaddr_008.png)

创建地址后，即可显示其预览和个性化。 请参阅[事务型消息预览](#transactional-message-preview)。

## 个性化数据 {#personalization-data}

可以使用消息模板中的数据来测试事务型消息的个性化。 此功能用于生成预览或发送校样。 您还可以为各种互联网访问提供商显示消息的呈现。 有关更多信息，请参阅[收件箱呈现](../../delivery/using/inbox-rendering.md)。

此数据旨在在消息最终投放之前对其进行测试。 这些消息与要处理的实际数据不一致。 但是，XML结构必须与执行实例中存储的事件的结构相同，如下所示：

![](assets/messagecenter_create_custo_006.png)

此信息允许您使用个性化标记对消息内容进行个性化（有关更多信息，请参阅[创建消息内容](../../message-center/using/creating-the-message-template.md#creating-message-content)）。

1. 选择事务型消息模板。

1. 在模板中，单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡。

1. 在事件内容中，以XML格式输入测试信息。

   ![](assets/messagecenter_create_custo_001.png)

1. 单击 **[!UICONTROL Save]**。

## 事务性消息预览 {#transactional-message-preview}

创建一个或多个种子地址和消息正文后，即可预览消息并检查其个性化。

1. 在消息模板中，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。

   ![](assets/messagecenter_preview_001.png)

1. 在下拉列表中选择&#x200B;**[!UICONTROL A seed address]**。

   ![](assets/messagecenter_preview_002.png)

1. 选择之前创建的种子地址以显示个性化消息。

   ![](assets/messagecenter_create_seedaddr_009.png)

使用种子地址，您还可以显示各种互联网访问提供商的消息呈现。 有关更多信息，请参阅[收件箱呈现](../../delivery/using/inbox-rendering.md)。

## 发送验证 {#sending-a-proof}

您可以通过向之前创建的种子地址发送校样来测试消息投放。

发送校样的过程与常规投放](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)的过程相同。 [但是，使用事务型消息传递，您需要事先执行以下操作：

* 使用[个性化数据](#personalization-data)创建一个或多个[种子地址](#managing-seed-addresses-in-transactional-messages)。
* [创建消息内容](../../message-center/using/creating-the-message-template.md#creating-message-content)。

要发送校样，请执行以下操作：

1. 单击投放窗口中的&#x200B;**[!UICONTROL Send a proof]**&#x200B;按钮。
1. 分析投放。
1. 更正任何错误并确认投放。

   ![](assets/messagecenter_send_proof_001.png)

1. 检查消息是否已发送到种子地址，且其内容符合您的配置。

   ![](assets/messagecenter_send_proof_002.png)

可通过&#x200B;**[!UICONTROL Audit]**&#x200B;选项卡访问每个模板中的校样。 有关此内容的更多详细信息，请参阅[发送校样](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

![](assets/messagecenter_send_proof_003.png)

您的消息模板现已准备就绪，可用于[published](../../message-center/using/publishing-message-templates.md)。