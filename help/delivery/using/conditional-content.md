---
solution: Campaign Classic
product: campaign
title: 条件内容
description: 条件内容
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 4%

---


# 条件内容{#conditional-content}

通过配置条件内容字段，您可以基于收件人的用户档案创建动态个性化。 当满足特定条件时替换文本块和/或图像。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#conditionnal-content-video)


## 在电子邮件{#using-conditions-in-an-email}中使用条件

在以下示例中，您将学习如何创建消息，根据收件人的性别和兴趣动态个性化。

* 显示“先生” 或“Ms” 根据数据源中&#x200B;**[!UICONTROL Gender]**&#x200B;字段（M或F）的值，
* 根据显示或检测到的兴趣个性化组合新闻稿或促销优惠:

   * 利息1 — >块1
   * 兴趣2 — >第2块
   * 利息3 — >第3块
   * 兴趣4 — >第4块

要根据字段的值创建条件内容，请应用以下步骤：

1. 单击个性化图标，然后选择&#x200B;**[!UICONTROL Conditional content > If]**。

   ![](assets/s_ncs_user_conditional_content02.png)

   个性化元素将插入消息正文中。 您现在必须配置它们。

1. 接下来，填写&#x200B;**if**&#x200B;表达式的参数。

   操作步骤：

   * 选择表达式的第一个元素&#x200B;**`<field>`**,(默认情况下，插入&#x200B;**if**&#x200B;表达式时，将突出显示此元素)，然后单击个性化图标将其替换为测试字段。

      ![](assets/s_ncs_user_conditional_content03.png)

   * 将&#x200B;**`<value>`**&#x200B;替换为满足条件的字段的值。 此值必须用引号表示。
   * 指定满足条件时要插入的内容。 这可能包括文本、图像、表单、超文本链接等。

      ![](assets/s_ncs_user_conditional_content04.png)

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，根据投放收件人视图消息内容：

   * 选择条件为True的收件人:

      ![](assets/s_ncs_user_conditional_content05.png)

   * 选择条件不为真的收件人:

      ![](assets/s_ncs_user_conditional_content06.png)

您可以添加其他情况，并根据一个或多个字段的值定义不同的内容。 要执行此操作，请使用&#x200B;**[!UICONTROL Conditional content > Else]**&#x200B;和&#x200B;**[!UICONTROL Conditional content > Else if]**。 这些表达式的配置方式与&#x200B;**if**&#x200B;表达式相同。

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>要遵循JavaScript语法，在添加&#x200B;**Else**&#x200B;和&#x200B;**Else if**&#x200B;条件后，必须删除&#x200B;**%> &lt;%**&#x200B;字符。

单击&#x200B;**[!UICONTROL Preview]**&#x200B;并选择收件人以视图条件内容。

![](assets/s_ncs_user_conditional_content08.png)

## 创建多语言电子邮件{#creating-multilingual-email}

在以下示例中，您将学习如何创建多语言电子邮件。 内容将显示为一种语言或另一种语言，具体取决于收件人的首选语言。

1. 创建电子邮件并选择目标群。 在此示例中，显示一个或另一个版本的条件将基于收件人用户档案的&#x200B;**Language**&#x200B;值。 在本例中，这些值设置为&#x200B;**EN**、**FR**、**ES**。
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

1. 通过选择使用不同首选语言的收件人，在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中测试电子邮件内容。

   >[!NOTE]
   >
   >由于电子邮件内容中未定义任何替代版本，请确保在发送电子邮件之前过滤目标填充。

## 教程视频{#conditionnal-content-video}

阅读多语言新闻稿示例，了解如何向投放添加条件内容。

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

其他Campaign Classic操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。
