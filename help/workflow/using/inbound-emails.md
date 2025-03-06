---
product: campaign
title: 入站电子邮件
description: 了解有关入站电子邮件工作流活动的更多信息
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# 入站电子邮件{#inbound-emails}



通过&#x200B;**入站电子邮件**&#x200B;活动，可从POP3邮件服务器下载和处理电子邮件。

![](assets/email_rec_edit_1.png)

**入站电子邮件**&#x200B;活动的第一个选项卡允许您输入POP3服务器的参数，并输入在收到每封邮件时要执行的脚本。 第二个选项卡用于为活动分配计划，第三个选项卡用于定义活动到期条件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     激活此选项后，您可以选择外部POP3帐户，而不是输入连接参数。 **[!UICONTROL External account]**&#x200B;字段指定要用于连接到电子邮件服务的外部POP3帐户。 仅当“使用外部帐户”选项启用时，此字段才可见。

     如果未选择此选项，则必须指定以下参数：

     ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

        pop3服务器的名称。

      * **[!UICONTROL POP3 account]**

        用户的名称。

      * **[!UICONTROL Password]**

        用户帐户密码。

      * **[!UICONTROL Port]**

        POP3连接端口号。 默认端口为110。

   * **[!UICONTROL Stop as soon as email is processed]**

     利用此选项，可以逐个处理电子邮件。 活动仅会激活一次其过渡，然后完成处理，从而将未处理的消息留在服务器上。

1. **[!UICONTROL Script]**

   利用脚本，可处理消息并根据消息内容执行各种操作。 该脚本针对每个消息被执行，并且可确定要对消息执行的操作（离开或删除消息）以及出站转变的激活。

   返回代码必须是以下值之一：

   * 1 — 从服务器删除消息并激活出站过渡。
   * 2 — 在服务器上保留消息并激活叫客过渡。
   * 3 — 从服务器删除消息。
   * 4 — 在服务器上保留消息。

   可从全局&#x200B;**[!UICONTROL mailMessage]**&#x200B;变量访问消息的内容。

1. **[!UICONTROL Schedule]**

   要为活动定义计划，请单击&#x200B;**[!UICONTROL Scheduling]**&#x200B;选项卡并选中&#x200B;**[!UICONTROL Plan execution]**。 单击&#x200B;**[!UICONTROL Change]**&#x200B;按钮配置计划。

   计划配置与计划活动相同。 请参阅[计划程序](scheduler.md)。

1. **[!UICONTROL Expiration]**

   您可以通过&#x200B;**[!UICONTROL Expiration]**&#x200B;选项卡定义到期延迟。

   ![](assets/email_rec_edit_3.png)

   配置与计划活动相同。 请参阅[过期时间](defining-approvals.md)。
