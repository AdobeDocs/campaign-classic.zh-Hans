---
solution: Campaign Classic
product: campaign
title: SpamAssassin
description: 了解如何使用SpamAssassin设置电子邮件垃圾邮件检测
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---


# SpamAssassin{#spamassassin}

## 关于SpamAssassin {#about-spamassassin}

Adobe Campaign可以配置为与用于电子邮件垃圾邮件过滤的第三方服务[SpamAssassin](https://spamassassin.apache.org)一起使用。 这样，您就可以对电子邮件进行评分，以确定邮件是否存在被接收时使用的防垃圾邮件工具视为垃圾邮件的风险。

SpamAssassin利用各种垃圾邮件检测技术，包括：

* 基于DNS和模糊校验和的垃圾邮件检测
* 贝叶斯滤波
* 外部项目
* 阻止列表
* 在线数据库

>[!NOTE]
>
>必须在Adobe Campaign应用程序服务器上安装和配置SpamAssan。 如需详细信息，请参阅[此部分](../../installation/using/configuring-spamassassin.md)。
>
>管理元素是否是垃圾信息的规则通过SpamAssassin进行管理，管理员可以使用权限编辑。

## 使用SpamAssans{#using-spamassassin}

创建电子邮件投放并定义其内容后，请按照以下步骤评估风险。

有关创建和设计投放的详细信息，请参阅[本节](../../delivery/using/about-email-channel.md)。

1. 转到 **[!UICONTROL Preview]** 选项卡。
1. 选择收件人以预览投放。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果不选择收件人，则无法执行反垃圾邮件检查。

1. 将显示一条警告消息，提示测试结果。 如果检测到高风险，将显示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 单击警告旁的&#x200B;**[!UICONTROL More...]**&#x200B;链接。
1. 选择 **[!UICONTROL Anti-spam checking]** 选项卡。
1. 转到&#x200B;**[!UICONTROL Points / Rule / Description]**&#x200B;部分以视图此风险的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次单击&#x200B;**[!UICONTROL Anti-spam checking]**&#x200B;时，都会调用SpamAssassin服务，并再次分析消息以检测垃圾邮件。 请确保在再次运行防垃圾邮件分析之前更改了内容。
