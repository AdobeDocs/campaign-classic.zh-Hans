---
product: campaign
title: 其他数据
description: 其他数据
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# 其他数据{#additional-data}

在调用交互引擎期间，您可以传输上下文附加信息。 此数据可以来自存储在工作流（出站渠道）工作表中的目标数据，或来自网站在调用（入站渠道）期间发送的调用数据。 您可以在资格规则中和选件个性化中使用此附加数据，还可以将其存储在建议表格中。

对于集客渠道，例如恢复咨询选件的人员的浏览器语言或呼叫中心代理的名称等信息可能非常有用。 然后，您可以在资格规则中使用此调用数据，以便仅向那些使用法语或英语查看网页的用户展示选件。

在定位工作流（出站渠道）中，您可以在调用引擎期间使用定位数据。 例如，您可以通过FDA使用收件人链接的交易或外部数据库中的数据扩充目标。

## 其他数据配置{#additional-data-configuration}

您必须扩展链接到环境的&#x200B;**nms:interaction**&#x200B;模式，并声明将在调用交互引擎期间使用的附加字段列表。 创建资格规则或个性化选件时，这些字段将可从&#x200B;**Interaction**&#x200B;节点访问（请参阅[Using adtical data](#using-additional-data)）。

对于集客渠道，必须将调用数据字段添加到&#x200B;**Interaction**&#x200B;节点中。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>集客渠道支持XML集合，但指向其他架构的链接则不支持。

对于出站渠道，必须将包含附加字段的&#x200B;**targetData**&#x200B;元素添加到&#x200B;**Interaction**&#x200B;节点中。

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

如果要在建议表中存储此数据，则还必须扩展&#x200B;**nms:compositionRcp**&#x200B;架构并声明这些字段。

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 其他数据实施{#additional-data-implementation}

### 输入渠道（网页）{#input-channel--web-page-}

要在调用引擎时传输其他数据，必须将&#x200B;**interactionGlobalCtx**&#x200B;变量添加到网页的JavaScript代码中。 将包含调用数据的&#x200B;**Interaction**&#x200B;节点插入此变量。 您必须遵循&#x200B;**nms:interaction**&#x200B;模式中的相同xml结构。 请参阅：[其他数据配置](#additional-data-configuration)。

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 输出通道{#output-channel}

您必须创建一个定向工作流，通过遵循与&#x200B;**nms:interaction**&#x200B;架构中相同的xml结构和相同的内部名称来加载工作表中的附加数据。 请参阅：[其他数据配置](#additional-data-configuration)。

## 使用附加数据{#using-additional-data}

### 资格规则{#eligibility-rules}

您可以在资格规则中对选件、类别和权重使用附加数据。

例如，您可以选择仅向查看页面的用户显示选件（英语）。

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>您必须在定义数据的渠道上限制规则。 在本例中，我们将限制入站Web渠道（**[!UICONTROL Taken into account if]**&#x200B;字段）上的规则。

### 个性化 {#personalization}

在个性化选件时，您还可以使用此附加数据。 例如，您可以为导航语言添加一个条件

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>您必须对定义数据的渠道限制个性化。 在本例中，我们将限制入站Web渠道上的规则。

如果您使用附加数据对选件进行了个性化，则默认情况下，此数据不会显示在预览中，因为它不在数据库中。 在环境的&#x200B;**[!UICONTROL Example of call data]**&#x200B;选项卡中，必须添加值示例才能在预览中使用。 请遵循&#x200B;**nms:interaction**&#x200B;模式扩展中的相同xml结构。 有关更多信息，请参阅[其他数据配置](#additional-data-configuration)。

![](assets/ita_calldata_preview.png)

预览时，单击&#x200B;**[!UICONTROL Content personalization options for the preview]**&#x200B;并在&#x200B;**[!UICONTROL Call data]**&#x200B;字段中选择一个值。

![](assets/ita_calldata_preview2.png)

### 存储 {#storage}

在调用引擎期间，您可以在建议表中存储附加数据以扩充数据库。 例如，这些数据可用于报表、ROI计算或后续流程中。

>[!NOTE]
>
>您必须扩展了&#x200B;**nms:compationRcp**&#x200B;模式并声明了将包含要存储的数据的字段。 有关此内容的更多信息：[其他数据配置](#additional-data-configuration)。

在选件空间中，转到&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

在&#x200B;**[!UICONTROL Storage path]**&#x200B;列中，选择命题表中的存储字段。 在&#x200B;**[!UICONTROL Expression]**&#x200B;列中，选择&#x200B;**[!UICONTROL Interaction]**&#x200B;节点中的附加字段。

在生成建议或接受建议时（当用户点击选件时），您可以检索呼叫数据。

![](assets/ita_calldata_storage.png)
