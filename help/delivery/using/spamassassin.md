---
title: SpamAssassin
seo-title: SpamAssassin
description: SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 7%

---


# SpamAssassin{#spamassassin}

## 关于SpamAssassin {#about-spamassassin}

Adobe Campaign可以配置为与 [SpamAssassin一起使用](https://spamassassin.apache.org)，这是用于电子邮件垃圾邮件过滤的第三方服务。 这使您能够对电子邮件进行评分以确定邮件是否存在被收到时使用的防垃圾邮件工具视为垃圾邮件的风险。

SpamAssassin利用各种垃圾邮件检测技术，包括：

* 基于DNS和模糊校验的垃圾邮件检测
* 贝叶斯滤波
* 外部项目
* 阻止列表
* 在线数据库

>[!NOTE]
>
>必须在Adobe Campaign应用程序服务器上安装并配置SpamAssassin。 如需详细信息，请参阅[此部分](../../installation/using/configuring-spamassassin.md)。
>
>管理元素是否是垃圾信息的规则通过SpamAssassin进行管理，并可由管理员以特权进行编辑。

## 使用SpamAssassin {#using-spamassassin}

创建电子邮件投放并定义其内容后，请按照以下步骤评估风险。

有关创建和设计投放的详细信息，请参 [阅本节](../../delivery/using/about-email-channel.md)。

1. 转到 **[!UICONTROL Preview]** 选项卡。
1. 选择收件人以预览投放。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果不选择收件人，则无法执行防垃圾邮件检查。

1. 将显示一条警告消息，显示测试结果。 如果检测到高风险，将显示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 单击警 **[!UICONTROL More...]** 告旁的链接。
1. 选择 **[!UICONTROL Anti-spam checking]** 选项卡。
1. 转到部分 **[!UICONTROL Points / Rule / Description]** 以视图产生此风险的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次单击时， **[!UICONTROL Anti-spam checking]**&#x200B;都会调用SpamAssassin服务，并再次分析该消息以检测垃圾邮件。 确保在再次运行防垃圾邮件分析之前更改了内容。
