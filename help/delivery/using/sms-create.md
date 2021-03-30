---
solution: Campaign Classic
product: campaign
title: 使用活动创建短信
description: 了解如何使用活动创建SMS
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 5a084ebe5295d19de24cf92c721d4692f0f5deb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 2%

---


# 创建短信投放 {#creating-a-sms-delivery}

## 选择投放渠道{#selecting-the-delivery-channel}

要创建新的SMS投放，请按照以下步骤操作：

>[!NOTE]
>
>[本节](../../delivery/using/steps-about-delivery-creation-steps.md)介绍了有关创建投放的全局概念。

1. 创建新投放，例如从投放仪表板创建。
1. 选择您之前创建的投放模板&#x200B;**发送到移动设备(SMPP)**。 有关详细信息，请参阅[更改投放模板](sms-set-up.md#changing-the-delivery-template)部分。

   ![](assets/s_user_mobile_wizard.png)

1. 用标签、代码和说明识别投放。 如需详细信息，请参阅[此部分](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 单击&#x200B;**[!UICONTROL Continue]**&#x200B;确认此信息并显示消息配置窗口。

## 定义SMS内容{#defining-the-sms-content}

要创建SMS内容，请执行以下步骤：

1. 在向导的&#x200B;**[!UICONTROL Text content]**&#x200B;部分输入消息的内容。 工具栏按钮允许您导入、保存或搜索内容。 最后一个按钮用于插入个性化字段。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   [关于个性化](../../delivery/using/about-personalization.md)部分介绍了个性化字段的使用。

1. 单击页面底部的&#x200B;**[!UICONTROL Preview]**&#x200B;以视图消息的呈现及其个性化。 要启动预览，请使用工具栏中的&#x200B;**[!UICONTROL Test personalization]**&#x200B;按钮选择收件人。 您可以从定义的收件人中选择一个目标或选择其他收件人。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以批准SMS消息。 您还可以视图内容编辑器右侧显示的手机屏幕上SMS的内容。 单击屏幕，然后使用鼠标滚动浏览内容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 单击&#x200B;**[!UICONTROL Data loaded]**&#x200B;链接以视图有关收件人的信息。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >如果使用拉丁文–1(ISO-8859-1)代码页，则SMS消息的长度限制为160个字符。 如果消息以Unicode编写，则不得超过70个字符。 某些特殊字符会影响消息长度。 有关消息长度的详细信息，请参阅[SMS字符音译](#about-character-transliteration)部分。
   >
   >当存在个性化字段或条件内容字段时，消息的大小因收件人而异。 在进行个性化时，必须评估消息的长度。
   >
   >启动分析时，将检查消息的长度，并在溢出事件中显示警告。

1. 如果您使用NetSize连接器或SMPP连接器，则可以个性化投放发送者的名称。 有关详细信息，请参阅[高级参数](#advanced-parameters)部分。

## 选择目标填充{#selecting-the-target-population}

在[本节](../../delivery/using/steps-defining-the-target-population.md)中显示了选择投放的目标种群的详细过程。

有关使用个性化字段的详细信息，请参阅[本节](../../delivery/using/about-personalization.md)。

有关包含种子列表的详细信息，请参阅[此页](../../delivery/using/about-seed-addresses.md)。

