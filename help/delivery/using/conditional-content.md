---
title: 条件内容
seo-title: 条件内容
description: 条件内容
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 2%

---


# 条件内容{#conditional-content}

通过配置条件内容字段，您可以根据收件人的用户档案创建动态个性化。 当满足特定条件时替换文本块和／或图像。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#conditionnal-content-video)


## 在电子邮件中使用条件 {#using-conditions-in-an-email}

在以下示例中，您将学习如何创建信息，根据收件人的性别和兴趣动态个性化。

* 展示“先生” 或“女士” 根据数据源 **[!UICONTROL Gender]** 中字段（M或F）的值，
* 根据所显示或检测到的兴趣个性化组合新闻稿或促销优惠:

   * 利息1 — >块1
   * 利息2 — >块2
   * 利息3 — >第3块
   * 利息4 — >第4块

要根据字段的值创建条件内容，请应用以下步骤：

1. 单击个性化图标并选择 **[!UICONTROL Conditional content > If]**。

   ![](assets/s_ncs_user_conditional_content02.png)

   个性化元素会插入消息正文中。 您现在必须配置它们。

1. 然后，填写if表达式的 **参数** 。

   操作步骤：

   * 选择表达式的第一个元素 **`<field>`**(默认情况下，插入if表达式时，此元素会高亮 **显示** )，然后单击个性化图标以将其替换为测试字段。

      ![](assets/s_ncs_user_conditional_content03.png)

   * 替 **`<value>`** 换为满足条件的字段的值。 此值必须用引号表示。
   * 指定满足条件时要插入的内容。 这可能由文本、图像、表单、超文本链接等组成。

      ![](assets/s_ncs_user_conditional_content04.png)

1. 单击选 **[!UICONTROL Preview]** 项卡以根据视图收件人投放消息的内容：

   * 选择条件为True的收件人:

      ![](assets/s_ncs_user_conditional_content05.png)

   * 选择条件不为真的收件人:

      ![](assets/s_ncs_user_conditional_content06.png)

您可以添加其他情况并根据一个或多个字段的值定义不同的内容。 为此，请使用 **[!UICONTROL Conditional content > Else]** 和 **[!UICONTROL Conditional content > Else if]**。 这些表达式的配置方式与if表达式 **相同** 。

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>要遵循JavaScript语法，必 **须在添加Else和Else条件后** ，删除%> **&lt;** % **>** 字符（如果条件）。

单 **[!UICONTROL Preview]** 击并选择收件人以视图条件内容。

![](assets/s_ncs_user_conditional_content08.png)

## 创建多语言电子邮件 {#creating-multilingual-email}

在以下示例中，您将学习如何创建多语言电子邮件。 内容将以一种语言或另一种语言显示，具体取决于收件人喜欢的语言。

1. 创建电子邮件并选择目标群。 在此示例中，显示一个版本或另一个版本的条件将基于 **收件人** 用户档案的“语言”值。 在此示例中，这些值设 **置为** EN **、FR**、 **ES**。
1. 在电子邮件HTML内容中，单击 **[!UICONTROL Source]** 选项卡并粘贴以下代码：

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. 通过选择使用不同首选 **[!UICONTROL Preview]** 语言的收件人，在选项卡中测试电子邮件内容。

   >[!NOTE]
   >
   >由于电子邮件内容中未定义任何替代版本，请确保在发送电子邮件之前过滤目标群。

## 如何创建包含条件内容的多语言新闻稿 {#conditionnal-content-video}

通过多语言新闻快讯的示例，了解如何向投放添加条件内容。

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)
