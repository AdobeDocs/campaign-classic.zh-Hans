---
product: campaign
title: 条件内容
description: 了解如何添加条件内容
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Personalization, Multilingual Messages
role: User
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 6%

---

# 条件内容{#conditional-content}

通过配置条件内容字段，您可以根据收件人的用户档案创建动态个性化。 当满足特定条件时，替换文本块和/或图像。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#conditionnal-content-video)


## 在电子邮件中使用条件 {#using-conditions-in-an-email}

在下面的示例中，您将了解如何根据收件人的性别和兴趣动态个性化创建消息。

* 显示“先生”的显示器 或“女士” 根据数据源中&#x200B;**[!UICONTROL Gender]**&#x200B;字段（M或F）的值，
* 根据指明或检测到的兴趣对新闻稿或促销优惠进行个性化组合：

   * 兴趣1 — >块1
   * 兴趣2 — >块2
   * 利息3 — >第3块
   * 利息4 — >第4块

要根据字段值创建条件内容，请应用以下步骤：

1. 单击个性化图标并选择&#x200B;**[!UICONTROL Conditional content > If]**。

   ![](assets/s_ncs_user_conditional_content02.png)

   个性化元素将插入到消息正文中。 您现在必须配置它们。

1. 接下来，填写&#x200B;**if**&#x200B;表达式的参数。

   操作步骤：

   * 选择表达式的第一个元素&#x200B;**`<field>`**（默认情况下，在插入&#x200B;**if**&#x200B;表达式期间此元素会高亮显示），然后单击个性化图标以将其替换为测试字段。

     ![](assets/s_ncs_user_conditional_content03.png)

   * 将&#x200B;**`<value>`**&#x200B;替换为将满足条件的字段的值。 此值必须在引号中。
   * 指定满足条件时要插入的内容。 这可能包括文本、图像、表单、超文本链接等。

     ![](assets/s_ncs_user_conditional_content04.png)

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，根据投放收件人查看邮件内容：

   * 选择条件为true的收件人：

     ![](assets/s_ncs_user_conditional_content05.png)

   * 选择条件不为真的收件人：

     ![](assets/s_ncs_user_conditional_content06.png)

您可以添加其他案例，并根据一个或多个字段的值定义不同的内容。 为此，请使用&#x200B;**[!UICONTROL Conditional content > Else]**&#x200B;和&#x200B;**[!UICONTROL Conditional content > Else if]**。 这些表达式的配置方式与&#x200B;**if**&#x200B;表达式相同。

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>为遵循JavaScript语法，添加&#x200B;**Else**&#x200B;和&#x200B;**Else if**&#x200B;条件后必须删除&#x200B;**%> &lt;%**&#x200B;字符。

单击&#x200B;**[!UICONTROL Preview]**&#x200B;并选择收件人以查看条件内容。

![](assets/s_ncs_user_conditional_content08.png)

## 创建多语言电子邮件 {#creating-multilingual-email}

在下面的示例中，您将了解如何创建多语言电子邮件。 根据收件人的首选语言，内容将以一种或另一种语言显示。

1. 创建电子邮件并选择目标群体。 在此示例中，显示一个版本或另一个版本的条件将基于收件人配置文件的&#x200B;**语言**&#x200B;值。 在此示例中，这些值设置为&#x200B;**EN**、**FR**、**ES**。
1. 在电子邮件HTML内容中，单击&#x200B;**[!UICONTROL Source]**&#x200B;选项卡并粘贴以下代码：

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

1. 通过选择具有不同首选语言的收件人，在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中测试电子邮件内容。

   >[!NOTE]
   >
   >由于电子邮件内容中未定义替代版本，请确保在发送电子邮件之前筛选目标群体。

## 教程视频 {#conditionnal-content-video}

了解如何在多语言新闻稿的示例中向投放添加条件内容。

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign Classic操作方法视频。
