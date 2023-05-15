---
product: campaign
title: 选择禁用个人信息销售
description: 了解个人数据销售的选择禁用
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---

# 个人数据销售的选择退出 (CCPA) {#sale-of-personal-information-ccpa}



**加州消费者隐私法案** (CCPA) 为加利福尼亚州居民提供了与其个人信息有关的新权利，并要求在加利福尼亚开展业务的特定实体承担数据保护责任。

访问和删除请求的配置和使用对于 GDPR 和 CCPA 均通用。此部分介绍特定于 CCPA 的个人数据销售的选择退出。

除了 Adobe Campaign 提供的[同意管理](privacy-management.md#consent-management)工具外，您还可以跟踪消费者是否已选择退出个人信息销售。

联系人可以决定不允许通过您的系统将其个人信息出售给第三方。在 Adobe Campaign 中，您将能够存储和跟踪此信息。

为使此功能正常工作，您需要扩展用户档案表并添加 **[!UICONTROL Opt-Out for CCPA]** 字段。

>[!IMPORTANT]
>
>作为数据控制者，您负责接收数据主体的请求并跟踪 CCPA 的请求日期。作为技术提供商，我们仅提供选择退出的方式。有关您作为数据控制者的角色的更多信息，请参阅[个人数据和角色](privacy-and-recommendations.md#personal-data)。

## 先决条件 {#ccpa-prerequisite}

要利用此信息，您需要在 Adobe Campaign Classic 中创建此字段。为此，您将向 **[!UICONTROL Recipient]** 表添加一个布尔字段。创建新字段后，Campaign API 会自动支持该字段。

如果您使用自定义收件人表，也需要执行此操作。

有关如何创建新字段的更多详细信息，请参阅[模式版文档](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>修改模式是一项敏感操作，必须仅由专家用户执行。

1. 转至&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**，选择 **[!UICONTROL Recipients]** 作为 **[!UICONTROL Document type]** 并单击 **[!UICONTROL Next]**。有关向表单添加字段的更多信息，请参阅[此小节](../../configuration/using/new-field-wizard.md)。

   ![](assets/privacy-ccpa-1.png)

1. 对于 **[!UICONTROL Field type]**，选择 **[!UICONTROL SQL field]**。对于“标签”，请使用 **[!UICONTROL Opt-Out for CCPA]**。选择 **[!UICONTROL 8-bit integer (boolean)]** 类型并定义以下唯一 **[!UICONTROL Relative path]**：@OPTOUTCCPA。单击 **[!UICONTROL Finish]**。

   ![](assets/privacy-ccpa-2.png)

   这将扩展或创建 **[!UICONTROL Recipient (cus)]** 模式。单击它可验证该字段是否已正确添加。

   ![](assets/privacy-ccpa-3.png)

1. 单击资源管理器的 **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** 节点。在“通用包” **[!UICONTROL Recipient (nms)]** 下，添加一个 `<input>` 元素，并使用步骤 2 中定义的相对路径作为 xpath 值。有关识别表单的更多信息，请参阅[此小节](../../configuration/using/identifying-a-form.md)。

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. 断开并重新连接。按照下一节中描述的步骤，验证字段在收件人的详细信息中是否可用。

## 使用情况 {#usage}

数据控制者负责填写字段值，并遵循关于数据销售的 CCPA 准则和规则。

要填写值，可以使用以下几种方法：

* 通过编辑收件人的详细信息，使用 Campaign 的界面
* 使用 API
* 通过数据导入工作流

然后，您应确保永远不要向已选择退出的任何第三方销售用户档案的个人信息。

1. 要更改选择退出状态，请转到 **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** 并选择收件人。在 **[!UICONTROL General]** 选项卡中，您会看到在上一节中配置的字段。

   ![](assets/privacy-ccpa-5.png)

1. 配置收件人列表以显示选择退出列。要了解如何配置列表，请参阅[有详细说明的文档](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

   ![](assets/privacy-ccpa-6.png)

1. 您可以单击该列，以根据选择退出信息对收件人进行排序。您还可以创建一个筛选器以仅显示已选择退出的收件人。有关创建筛选器的更多信息，请参阅[此小节](../../platform/using/creating-filters.md)。

   ![](assets/privacy-ccpa-7.png)
