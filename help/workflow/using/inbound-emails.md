---
product: campaign
title: 入站电子邮件
description: 了解有关入站电子邮件工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# 入站电子邮件{#inbound-emails}



此 **入站电子邮件** 通过活动，可从POP3邮件服务器下载和处理电子邮件。

![](assets/email_rec_edit_1.png)

的第一个选项卡 **入站电子邮件** 通过活动，您可以输入POP3服务器的参数，并输入在收到每封邮件时要执行的脚本。 第二个选项卡让您可以为活动分配计划，第三个选项卡定义活动到期条件。

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      激活此选项后，您可以选择外部POP3帐户，而不是输入连接参数。 此 **[!UICONTROL External account]** 字段指定用于连接到电子邮件服务的外部POP3帐户。 仅当启用“使用外部帐户”选项时，此字段才可见。

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

      此选项允许您逐个处理电子邮件。 活动仅激活一次其过渡，然后完成处理，将未处理的消息留在服务器上。


1. **[!UICONTROL Script]**

   利用脚本，可处理消息并执行各种依赖于消息内容的操作。 该脚本针对每个消息执行，并可确定要对消息执行的操作（离开或删除消息）以及出站过渡的激活。

   返回代码必须是以下值之一：

   * 1 — 从服务器删除消息并激活出站过渡。
   * 2 — 将消息保留在服务器上并激活出站过渡。
   * 3 — 从服务器删除消息。
   * 4 — 在服务器上保留消息。

   可从全局访问消息的内容 **[!UICONTROL mailMessage]** 变量。

1. **[!UICONTROL Schedule]**

   要定义活动的计划，请单击 **[!UICONTROL Scheduling]** 制表符和勾选 **[!UICONTROL Plan execution]**. 单击 **[!UICONTROL Change]** 按钮以配置计划。

   计划配置与计划活动的配置相同。 请参阅 [调度程序](scheduler.md).

1. **[!UICONTROL Expiration]**

   您可以通过以下方式定义到期延迟 **[!UICONTROL Expiration]** 选项卡。

   ![](assets/email_rec_edit_3.png)

   配置与计划活动的配置相同。 请参阅 [过期时间](defining-approvals.md).
