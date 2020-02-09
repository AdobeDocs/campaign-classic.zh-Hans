---
title: 其他数据
seo-title: 其他数据
description: 其他数据
seo-description: null
page-status-flag: never-activated
uuid: 81a889ce-b02d-4593-95fa-1de5601182e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 29339aad-fd8e-4dae-8f6e-2db87221ad04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 其他数据{#additional-data}

在调用交互引擎期间，您可以传输上下文附加信息。 该数据可以来自存储在工作流（出站通道）的工作表中的目标数据或在呼叫（入站通道）期间由网站发送的呼叫数据。 您可以在资格规则和选件个性化中使用此附加数据，还可以将其存储在命题表中。

对于入站渠道，恢复信息（例如，咨询选件的人员的浏览器语言或呼叫中心代理的名称）可能很有用。 然后，您可以在资格规则中使用此呼叫数据，以仅向那些使用法语或英语查看网页的人提供选件。

在定位工作流（出站渠道）中，您可以在调用引擎期间使用目标数据。 例如，您可以通过FDA从收件人链接的事务或外部数据库获取数据来丰富目标。

## 其他数据配置 {#additional-data-configuration}

必须扩展链 **接到该环境的nms:interaction** 架构，并声明将在调用交互引擎期间使用的其他字段列表。 在创建资格规则或个性化选件时，这些字段将从“交互”节点 **访问** (请参阅使 [用其他数据](#using-additional-data))。

对于入站渠道，必须将调用数据字段添加到“交互 **”节点** 。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>入站渠道支持XML集合，但到其他架构的链接不支持。

对于出站渠道，必须向“交互”节 **点中添加包含其他字段的** targetData **** 元素。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>出站渠道不支持集合。 但是，您可以创建指向其他架构的链接。

如果要将此数据存储在命题表中，则还必须扩展 **nms:postitionRcp** schema并声明这些字段。

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 其他数据实施 {#additional-data-implementation}

### 输入渠道（网页） {#input-channel--web-page-}

要在调用引擎时传输其他数据，必须将 **interactionGlobalCtx** 变量添加到网页的JavaScript代码中。 将包含调 **用数据的** Interaction节点插入此变量。 您必须遵循nms:interaction架构中的相 **同xml结构** 。 请参阅：其 [他数据配置](#additional-data-configuration)。

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 输出通道 {#output-channel}

必须创建一个定位工作流，通过遵循与 **nms:interaction架构相同的xml结构和内部名称在工作表中加载其他数据** 。 请参阅：其 [他数据配置](#additional-data-configuration)。

## 使用其他数据 {#using-additional-data}

### 资格规则 {#eligibility-rules}

您可以在资格规则中使用其他数据，包括选件、类别和权重。

例如，您可以选择仅向查看页面的人员显示选件（英文）。

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>您必须限制定义数据的渠道的规则。 在我们的示例中，我们将限制入站Web渠道（字段）**[!UICONTROL Taken into account if]** 上的规则。

### 个性化 {#personalization}

在个性化选件时，您还可以使用此附加数据。 例如，您可以为导航语言添加条件

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>您必须限制定义数据的渠道的个性化。 在我们的示例中，我们将限制入站Web渠道上的规则。

如果您使用其他数据个性化了优惠信息，则此数据在默认情况下不会显示在预览中，因为数据库中不提供此数据。 在环境的选项卡 **[!UICONTROL Example of call data]** 中，必须添加值范例才能在预览中使用。 请遵循nms:interaction架构扩展中的相 **同xml结构** 。 有关详细信息，请参阅其 [他数据配置](#additional-data-configuration)。

![](assets/ita_calldata_preview.png)

预览时，单 **[!UICONTROL Content personalization options for the preview]** 击并在字段中选择一个 **[!UICONTROL Call data]** 值。

![](assets/ita_calldata_preview2.png)

### 存储 {#storage}

在调用引擎期间，您可以在命题表中存储其他数据以丰富数据库。 这些数据可用于报告、ROI计算或后续流程。

>[!NOTE]
>
>您必须已扩展 **nms:compationRcp** schema，并声明将包含要存储的数据的字段。 有关此方面的更多信息：其 [他数据配置](#additional-data-configuration)。

在选件空间中，转到选项卡， **[!UICONTROL Storage]** 然后单击按 **[!UICONTROL Add]** 钮。

在列中， **[!UICONTROL Storage path]** 选择命题表中的存储字段。 在列中， **[!UICONTROL Expression]** 选择节点中的其他字 **[!UICONTROL Interaction]** 段。

在生成建议或接受建议时（当用户单击该建议时），您可以检索呼叫数据。

![](assets/ita_calldata_storage.png)

