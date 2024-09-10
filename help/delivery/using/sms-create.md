---
product: campaign
title: 使用Campaign创建短信
description: 了解如何使用Campaign创建短信
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: SMS
role: User
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# 创建短信投放 {#creating-a-sms-delivery}

## 选择投放渠道 {#selecting-the-delivery-channel}

要创建新的短信投放，请执行以下步骤：

>[!NOTE]
>
>有关投放创建的全局概念在[此部分](steps-about-delivery-creation-steps.md)中介绍。

1. 创建新投放，例如从投放仪表板。
1. 选择您之前创建的投放模板&#x200B;**Sent to mobiles (SMPP)**。 有关更多信息，请参阅[更改投放模板](sms-set-up.md#changing-the-delivery-template)部分。

   ![](assets/s_user_mobile_wizard.png)

1. 使用标签、代码和描述标识投放。 如需详细信息，请参阅[此小节](steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 单击&#x200B;**[!UICONTROL Continue]**&#x200B;以确认此信息并显示消息配置窗口。

## 定义短信内容 {#defining-the-sms-content}

要创建短信的内容，请执行以下步骤：

1. 在助理的&#x200B;**[!UICONTROL Text content]**&#x200B;部分输入消息的内容。 使用工具栏按钮可以在内容中导入、保存或搜索。 最后按钮用于插入个性化字段。

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   个性化字段的使用显示在[关于个性化](about-personalization.md)部分。

1. 单击页面底部的&#x200B;**[!UICONTROL Preview]**&#x200B;以查看消息的呈现及其个性化设置。 要启动预览，请使用工具栏中的&#x200B;**[!UICONTROL Test personalization]**&#x200B;按钮选择一个收件人。 您可以从定义的目标中选择收件人，也可以选择其他收件人。

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   您可以批准短信消息。 您还可以在内容编辑器右侧显示的手机屏幕上查看短信的内容。 单击屏幕并使用鼠标滚动内容。

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 单击&#x200B;**[!UICONTROL Data loaded]**&#x200B;链接可查看有关收件人的信息。

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >如果使用Latin-1 (ISO-8859-1)代码页，SMS消息长度限制为160个字符。 如果消息使用Unicode编写，则不能超过70个字符。 某些特殊字符可能会影响消息长度。 有关消息长度的更多信息，请参阅[短信字符音译](#about-character-transliteration)部分。
   >
   >当存在个性化字段或条件内容字段时，消息的大小因收件人而异。 进行个性化时必须评估消息的长度。
   >
   >启动分析时，将检查消息长度，并在发生溢出时显示警告。

1. 如果您使用NetSize连接器或SMPP连接器，则可以个性化投放发件人的名称。 有关详细信息，请参阅[高级参数](#advanced-parameters)部分。

## 选择目标群体 {#selecting-the-target-population}

[此部分](steps-defining-the-target-population.md)中显示了选择投放目标群体的详细过程。

有关个性化字段用法的详细信息，请参阅[本节](about-personalization.md)。

有关包含种子列表的详细信息，请参阅[此页面](about-seed-addresses.md)。
