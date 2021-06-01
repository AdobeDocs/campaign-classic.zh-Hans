---
product: campaign
title: 使用Campaign创建短信
description: 了解如何使用Campaign创建短信
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 2%

---

# 创建短信投放 {#creating-a-sms-delivery}

## 选择投放渠道{#selecting-the-delivery-channel}

要创建新的短信投放，请执行以下步骤：

>[!NOTE]
>
>有关投放创建的全局概念，请参见[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

1. 创建新投放，例如从投放仪表板创建。
1. 选择您之前创建的投放模板&#x200B;**发送到手机(SMPP)**。 有关更多信息，请参阅[更改投放模板](sms-set-up.md#changing-the-delivery-template)一节。

   ![](assets/s_user_mobile_wizard.png)

1. 使用标签、代码和描述标识投放。 如需详细信息，请参阅[此部分](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 单击&#x200B;**[!UICONTROL Continue]**&#x200B;确认此信息并显示消息配置窗口。

## 定义短信内容{#defining-the-sms-content}

要创建短信的内容，请执行以下步骤：

1. 在向导的&#x200B;**[!UICONTROL Text content]**&#x200B;部分中输入消息的内容。 利用工具栏按钮，可导入、保存或搜索内容。 最后一个按钮用于插入个性化字段。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   [关于个性化](../../delivery/using/about-personalization.md)部分中介绍了个性化字段的使用情况。

1. 单击页面底部的&#x200B;**[!UICONTROL Preview]**&#x200B;可查看消息的个性化呈现情况。 要启动预览，请使用工具栏中的&#x200B;**[!UICONTROL Test personalization]**&#x200B;按钮选择收件人。 您可以从定义的目标中选择收件人或选择其他收件人。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以批准短信消息。 您还可以在内容编辑器右侧显示的手机屏幕上查看短信的内容。 单击屏幕，然后使用鼠标滚动浏览内容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 单击&#x200B;**[!UICONTROL Data loaded]**&#x200B;链接可查看有关收件人的信息。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >如果使用Latin-1(ISO-8859-1)代码页面，则短信消息的长度限制为160个字符。 如果消息以Unicode写入，则不得超过70个字符。 某些特殊字符可能会影响消息长度。 有关消息长度的更多信息，请参阅[短信字符音译](#about-character-transliteration)一节。
   >
   >当存在个性化字段或条件内容字段时，消息的大小会因收件人而异。 执行个性化后，必须评估消息的长度。
   >
   >启动分析时，将检查消息的长度，并在发生溢出时显示警告。

1. 如果您使用NetSize连接器或SMPP连接器，则可以将投放发送者的名称个性化。 有关更多信息，请参阅[高级参数](#advanced-parameters)一节。

## 选择目标群体{#selecting-the-target-population}

选择投放的目标群体时的详细过程，请参见[此部分](../../delivery/using/steps-defining-the-target-population.md)。

有关个性化字段使用的更多信息，请参阅[此部分](../../delivery/using/about-personalization.md)。

有关包含种子列表的更多信息，请参见[本页](../../delivery/using/about-seed-addresses.md)。
