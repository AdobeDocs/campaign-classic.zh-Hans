---
title: 入站电子邮件
seo-title: 入站电子邮件
description: 入站电子邮件
seo-description: null
page-status-flag: never-activated
uuid: 6bcc7952-f051-4e50-8833-95d49c7ed781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 4c0530b1-0292-45bc-8730-668bc5b8550b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 入站电子邮件{#inbound-emails}

“入站 **电子邮件** ”活动允许您从POP3邮件服务器下载和处理电子邮件。

![](assets/email_rec_edit_1.png)

“入站电子邮 **件** ”活动的第一个选项卡允许您输入POP3服务器的参数，并输入在收到每条消息时要执行的脚本。 第二个选项卡允许您为活动分配计划，第三个选项卡定义活动到期条件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      激活此选项后，您可以选择外部POP3帐户，而不是输入连接参数。 该字 **[!UICONTROL External account]** 段指定用于连接到电子邮件服务的外部POP3帐户。 仅当启用“使用外部帐户”选项时，此字段才可见。

      如果未选择此选项，则必须指定以下参数：

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         POP3服务器的名称。

      * **[!UICONTROL POP3 account]**

         用户的名称。

      * **[!UICONTROL Password]**

         用户帐户密码。

      * **[!UICONTROL Port]**

         POP3连接端口号。 默认端口为110。
   * **[!UICONTROL Stop as soon as email is processed]**

      通过此选项，您可以逐个处理电子邮件。 活动仅激活其过渡一次，然后完成处理，在服务器上保留未处理的消息。


1. **[!UICONTROL Script]**

   该脚本允许您处理消息并执行取决于消息内容的各种操作。 对每条消息执行该脚本，并可确定要对消息（离开或删除消息）执行的操作以及对出站转换的激活。

   返回代码必须为以下值之一：

   * 1 —— 从服务器中删除消息并激活出站过渡。
   * 2 —— 将消息保留在服务器上并激活出站过渡。
   * 3 —— 从服务器删除消息。
   * 4 —— 将消息保留在服务器上。
   消息的内容可从全局变量中访 **[!UICONTROL mailMessage]** 问。

1. **[!UICONTROL Schedule]**

   要为活动定义计划，请单击选项卡 **[!UICONTROL Scheduling]** 并选中 **[!UICONTROL Plan execution]**。 单击按 **[!UICONTROL Change]** 钮以配置计划。

   计划配置与计划活动的配置相同。 请参阅 [计划程序](../../workflow/using/scheduler.md)。

1. **[!UICONTROL Expiration]**

   您可以通过选项卡定义过期延 **[!UICONTROL Expiration]** 迟。

   ![](assets/email_rec_edit_3.png)

   配置与计划活动的配置相同。 请参阅 [过期](../../workflow/using/executing-a-workflow.md#expirations)。

