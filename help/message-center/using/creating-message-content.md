---
title: 创建消息内容
seo-title: 创建消息内容
description: 创建消息内容
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 4%

---


# 创建消息内容{#creating-message-content}

事务性消息内容的定义与普通投放在Adobe Campaign中的定义相同。 例如，对于电子邮件投放，您可以创建HTML或文本格式的内容、添加附件或个性化投放对象。 有关此内容的详细信息，请参阅“电子邮件 [投放”一章](../../delivery/using/about-email-channel.md)。

>[!CAUTION]
>
>消息中包含的图像必须可以公开访问。 Adobe Campaign不为事务性消息提供任何图像上传机制。\
>与JSSP或webApp不同， `<%=` 没有任何默认转义。
>
>在这种情况下，您必须正确地从事件中逃出每个数据。 此转义取决于此字段的使用方式。 例如，在URL中，请使用encodeURIComponent。 要在HTML中显示，可以使用escapeXMLString。

定义消息内容后，您可以将事件信息集成到消息正文中并进行个性化。 事件信息由于采用个性化标记而插入到文本正文中。

![](assets/messagecenter_create_content_001.png)

* 所有个性化字段都来自有效载荷。
* 可以在事务性消息中引用一个或多个个性化块。 块内容将在发布到投放期间添加到执行实例内容。

要在电子邮件正文中插入个性化标记，请应用以下步骤：

1. 在消息模板中，单击与电子邮件格式（HTML或文本）匹配的选项卡。
1. 输入邮件正文。
1. 在文本正文中，使用菜单插入标 **[!UICONTROL Real time events>Event XML]** 签。

   ![](assets/messagecenter_create_custo_002.png)

1. 使用以下语法填写标记： **元素名称**。@**属性名** ，如下所示。

   ![](assets/messagecenter_create_custo_003.png)

