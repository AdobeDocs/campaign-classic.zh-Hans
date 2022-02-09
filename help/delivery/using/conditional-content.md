---
product: campaign
title: 条件内容
description: 了解如何添加条件内容
feature: Personalization, Multilingual Messages
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 7%

---

# 条件内容{#conditional-content}

![](../../assets/common.svg)

通过配置条件内容字段，您可以创建基于收件人用户档案的动态个性化。 当满足特定条件时替换文本块和/或图像。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#conditionnal-content-video)


## 在电子邮件中使用条件 {#using-conditions-in-an-email}

在以下示例中，您将学习如何创建根据收件人的性别和兴趣动态个性化的消息。

* 显示“Mr.” 或“Ms” 根据 **[!UICONTROL Gender]** 字段（M或F），
* 根据所指示或检测到的兴趣个性化地组合新闻稿或促销优惠：

   * 兴趣1 — >块1
   * 兴趣2 — >块2
   * 兴趣3 — >第3块
   * 兴趣4 — >第4块

要根据字段的值创建条件内容，请应用以下步骤：

1. 单击个性化图标，然后选择 **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   个性化元素会插入到消息正文中。 您现在必须配置它们。

1. 接下来，填写 **if** 表达式。

   操作步骤：

   * 选择表达式的第一个元素， **`<field>`**,(默认情况下，此元素会在插入 **if** 表达式)，然后单击个性化图标以将其替换为测试字段。

      ![](assets/s_ncs_user_conditional_content03.png)

   * 替换 **`<value>`** ，其中字段的值将满足条件。 此值必须用引号表示。
   * 指定满足条件时要插入的内容。 这可以包含文本、图像、表单、超文本链接等。

      ![](assets/s_ncs_user_conditional_content04.png)

1. 单击 **[!UICONTROL Preview]** 选项卡，以根据投放收件人查看消息的内容：

   * 选择条件为true的收件人：

      ![](assets/s_ncs_user_conditional_content05.png)

   * 选择条件不为true的收件人：

      ![](assets/s_ncs_user_conditional_content06.png)

您可以添加其他大小写，并根据一个或多个字段的值定义不同的内容。 为此，请使用 **[!UICONTROL Conditional content > Else]** 和 **[!UICONTROL Conditional content > Else if]**. 这些表达式的配置方式与 **if** 表达式。

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>要遵循JavaScript语法，请 **%> &lt;%** 添加后必须删除字符 **Else** 和 **如果** 条件。

单击 **[!UICONTROL Preview]** 并选择收件人以查看条件内容。

![](assets/s_ncs_user_conditional_content08.png)

## 创建多语言电子邮件 {#creating-multilingual-email}

在以下示例中，您将学习如何创建多语言电子邮件。 内容将以一种或另一种语言显示，具体取决于收件人的首选语言。

1. 创建电子邮件并选择目标群体。 在此示例中，用于显示一个版本或另一个版本的条件将基于 **语言** 收件人用户档案的值。 在本例中，这些值被设置为 **EN**, **FR**, **ES**.
1. 在电子邮件HTML内容中，单击 **[!UICONTROL Source]** 选项卡，并粘贴以下代码：

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

1. 在 **[!UICONTROL Preview]** 选项卡，方法是选择使用不同首选语言的收件人。

   >[!NOTE]
   >
   >由于电子邮件内容中未定义任何替代版本，因此请确保在发送电子邮件之前过滤目标群体。

## 教程视频 {#conditionnal-content-video}

了解如何在多语言新闻稿的示例中向投放添加条件内容。

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
