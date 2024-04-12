---
product: campaign
title: SpamAssassin
description: 了解如何使用SpamAssassin设置电子邮件垃圾邮件检测
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# SpamAssassin{#spamassassin}

Adobe Campaign可以配置为与 [SpamAssassin](https://spamassassin.apache.org)，用于电子邮件垃圾邮件过滤的第三方服务。 这允许您对电子邮件进行评分，以确定邮件在接收时是否会被反垃圾邮件工具视为垃圾邮件。

SpamAssassin利用多种垃圾邮件检测技术，包括：

* 基于DNS和基于模糊校验和的垃圾邮件检测
* 贝叶斯滤波
* 外部程序
* 阻止列表
* 在线数据库

>[!NOTE]
>
>必须在Adobe Campaign应用程序服务器上安装和配置SpamAssassin。 如需详细信息，请参阅[此小节](../../installation/using/configuring-spamassassin.md)。
>
>控制元素是否为垃圾邮件的规则通过SpamAssassin进行管理，并且可由具有权限的管理员编辑。

## 在营销活动中使用SpamAssassin {#using-spamassassin}

创建电子邮件投放并定义其内容后，请按照以下步骤评估风险。

有关创建和设计投放的更多信息，请参阅 [本节](about-email-channel.md).

1. 转到 **[!UICONTROL Preview]** 选项卡。
1. 选择一个收件人以预览您的投放。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果不选择收件人，则无法执行反垃圾邮件检查。

1. 出现警告消息，给出测试结果。 如果检测到高风险，将显示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 单击 **[!UICONTROL More...]** 警告旁边的链接。
1. 选择 **[!UICONTROL Anti-spam checking]** 选项卡。
1. 转到 **[!UICONTROL Points / Rule / Description]** 部分以查看此风险的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次单击 **[!UICONTROL Anti-spam checking]**，调用SpamAssassin服务并再次分析消息以进行反垃圾邮件检测。 在再次运行反垃圾邮件分析之前，请确保已更改您的内容。
