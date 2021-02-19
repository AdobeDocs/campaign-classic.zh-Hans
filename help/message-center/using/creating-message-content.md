---
solution: Campaign Classic
product: campaign
title: 创建消息内容
description: 创建消息内容
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---


# 创建消息内容{#creating-message-content}

事务性消息内容的定义与Adobe Campaign中常规投放的定义相同。 例如，对于电子邮件投放，您可以创建HTML或文本格式的内容、添加附件或个性化投放对象。 有关详细信息，请参阅[电子邮件投放](../../delivery/using/about-email-channel.md)中的一章。

>[!IMPORTANT]
>
>邮件中包含的图像必须可以公开访问。 Adobe Campaign不为事务性消息提供任何图像上传机制。\
>与JSSP或webApp不同，`<%=`没有任何默认转义。
>
>在这种情况下，您必须正确地从事件中转移每个数据。 此转义取决于此字段的使用方式。 例如，在URL中，请使用encodeURIComponent。 要在HTML中显示，可以使用escapeXMLString。

定义消息内容后，您可以将事件信息集成到消息正文中并对其进行个性化设置。 事件信息通过个性化标记插入文本正文。

![](assets/messagecenter_create_content_001.png)

* 所有个性化字段都来自有效负荷。
* 可以在事务性消息中引用一个或多个个性化块。 块内容将在发布到投放期间添加到执行实例内容。

要在电子邮件正文中插入个性化标记，请应用以下步骤：

1. 在消息模板中，单击与电子邮件格式（HTML或文本）匹配的选项卡。
1. 输入消息的正文。
1. 在文本正文中，使用&#x200B;**[!UICONTROL Real time events>Event XML]**&#x200B;菜单插入标记。

   ![](assets/messagecenter_create_custo_002.png)

1. 使用以下语法填充标记：**元素名称**。如下所示，@**属性名称**。

   ![](assets/messagecenter_create_custo_003.png)

