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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# SpamAssassin{#spamassassin}

## 关于SpamAssassin {#about-spamassassin}

可以将Adobe Campaign配置为与 [SpamAssassin](https://spamassassin.apache.org)（用于电子邮件垃圾邮件过滤的第三方服务）结合使用。 这允许您对电子邮件进行评分，以确定邮件是否存在被收到时使用的防垃圾邮件工具视为垃圾邮件的风险。

SpamAssassin利用各种垃圾邮件检测技术，包括：

* 基于DNS和基于模糊校验和的垃圾邮件检测
* 贝叶斯滤波
* 外部计划
* 黑名单
* 联机数据库

>[!NOTE]
>
>必须在Adobe Campaign应用程序服务器上安装和配置SpamAssassin。 如需详细信息，请参阅[此部分](../../installation/using/configuring-spamassassin.md)。
>
>管理元素是否为垃圾信息的规则通过SpamAssassin进行管理，并由具有权限的管理员编辑。

## 使用SpamAssassin {#using-spamassassin}

创建电子邮件分发并定义其内容后，请按照以下步骤评估风险。

有关创建和设计分发的详细信息，请参 [阅此部分](../../delivery/using/about-email-channel.md)。

1. 转到选 **[!UICONTROL Preview]** 项卡。
1. 选择收件人以预览您的分发。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果不选择收件人，则无法执行反垃圾邮件检查。

1. 将显示一条警告消息，提示测试结果。 如果检测到高风险，将显示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 单击警 **[!UICONTROL More...]** 告旁边的链接。
1. 选择选 **[!UICONTROL Anti-spam checking]** 项卡。
1. 转到部 **[!UICONTROL Points / Rule / Description]** 分查看此风险的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次单击时， **[!UICONTROL Anti-spam checking]**&#x200B;都会调用SpamAssassin服务并再次分析消息以检测垃圾邮件。 请确保在再次运行防垃圾邮件分析之前更改了内容。
