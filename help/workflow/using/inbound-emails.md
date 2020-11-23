---
solution: Campaign Classic
product: campaign
title: 入站电子邮件
description: 进一步了解入站电子邮件工作流活动
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---


# 入站电子邮件{#inbound-emails}

“入站 **电子邮件** ”活动允许您从POP3邮件服务器下载和处理电子邮件。

![](assets/email_rec_edit_1.png)

在“入站电子邮件 **”活动的第一个选项卡** ，您可以输入POP3服务器的参数，并输入在收到每条消息后要执行的脚本。 第二个选项卡允许您为计划分配活动，第三个选项卡定义活动到期条件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      激活此选项后，您可以选择外部POP3帐户，而不是输入连接参数。 该 **[!UICONTROL External account]** 字段指定用于连接到电子邮件服务的外部POP3帐户。 仅当启用“使用外部帐户”选项时，此字段才可见。

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

      通过此选项，您可以逐个处理电子邮件。 活动仅激活其过渡一次，然后完成处理，在服务器上留下未处理的消息。


1. **[!UICONTROL Script]**

   该脚本允许您处理消息并执行取决于消息内容的各种操作。 脚本针对每条消息执行，并可确定要对消息（离开或删除消息）和出站过渡的激活执行的操作。

   返回代码必须是以下值之一：

   * 1 —— 从服务器删除消息并激活出站过渡。
   * 2 —— 将消息保留在服务器上并激活出站过渡。
   * 3 —— 从服务器删除消息。
   * 4 —— 将消息保留在服务器上。

   消息内容可通过全局变量访 **[!UICONTROL mailMessage]** 问。

1. **[!UICONTROL Schedule]**

   要为计划定义活动，请单击选 **[!UICONTROL Scheduling]** 项卡并选中 **[!UICONTROL Plan execution]**。 单击按 **[!UICONTROL Change]** 钮以配置计划。

   计划配置与计划活动的配置相同。 请参阅 [调度程序](../../workflow/using/scheduler.md)。

1. **[!UICONTROL Expiration]**

   您可以通过选项卡定义到期 **[!UICONTROL Expiration]** 延迟。

   ![](assets/email_rec_edit_3.png)

   配置与计划活动相同。 请参阅 [过期](../../workflow/using/defining-approvals.md)。

