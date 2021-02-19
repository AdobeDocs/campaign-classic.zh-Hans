---
solution: Campaign Classic
product: campaign
title: 其他数据
description: 其他数据
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# 其他数据{#additional-data}

在调用交互引擎期间，您可以传输上下文附加信息。 此目标可以来自存储在工作流(出站渠道)的工作表中的数据，或来自网站在呼叫期间发送的呼叫数据(入站渠道)。 您可以在合格规则中、优惠个性化中使用此附加数据，还可以将其存储在命题表中。

对于入站渠道，可能有用于恢复诸如咨询优惠的人员的浏览器语言或呼叫中心代理的名称等信息。 然后，您可以使用合格规则中的此调用数据，仅向那些以法语或英语查看网页的用户演示优惠。

在定位工作流(出站渠道)中，您可以在调用引擎期间使用目标数据。 例如，您可以通过目标从收件人链接的事务或外部数据库中获取数据来丰富联合数据访问。

## 其他数据配置{#additional-data-configuration}

您必须扩展链接到环境的&#x200B;**nms:interaction**&#x200B;模式，并声明将在调用交互引擎期间使用的其他字段的列表。 创建合格规则或个性化优惠时，这些字段将可从&#x200B;**Interaction**&#x200B;节点访问（请参阅[使用其他数据](#using-additional-data)）。

对于入站渠道，必须将调用数据字段添加到&#x200B;**Interaction**&#x200B;节点中。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>入站渠道支持Xml集合，但指向其他模式的链接不支持。

对于出站渠道，必须向&#x200B;**Interaction**&#x200B;节点中添加包含附加字段的&#x200B;**targetData**&#x200B;元素。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>出站渠道不支持集合。 但是，您可以创建指向其他模式的链接。

如果要将此数据存储在命题表中，则还必须扩展&#x200B;**nms:compationRcp**&#x200B;模式并声明这些字段。

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 其他数据实现{#additional-data-implementation}

### 输入渠道（网页）{#input-channel--web-page-}

要在调用引擎时传输其他数据，必须将&#x200B;**interactionGlobalCtx**&#x200B;变量添加到网页的JavaScript代码中。 将包含调用数据的&#x200B;**Interaction**&#x200B;节点插入此变量。 您必须遵循&#x200B;**nms:interaction**&#x200B;模式中的相同xml结构。 请参阅：[其他数据配置](#additional-data-configuration)。

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 输出渠道{#output-channel}

必须创建一个定位工作流，通过遵循与&#x200B;**nms:interaction**&#x200B;模式相同的xml结构和相同的内部名称加载工作表中的其他数据。 请参阅：[其他数据配置](#additional-data-configuration)。

## 使用其他数据{#using-additional-data}

### 合格规则{#eligibility-rules}

您可以将合格规则中的其他数据用于优惠、类别和权重。

例如，您可以选择仅向查看页面的人显示优惠（英语）。

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>您必须对定义渠道的规则进行限制。 在我们的示例中，我们将限制入站Web渠道（**[!UICONTROL Taken into account if]**&#x200B;字段）上的规则。

### 个性化{#personalization}

在个性化优惠时，您还可以使用此附加数据。 例如，您可以为导航语言添加一个条件

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>您必须对定义数据的渠道限制个性化。 在我们的示例中，我们将限制入站Web渠道的规则。

如果您使用其他数据对优惠进行了个性化设置，则默认情况下，此数据不会显示在预览中，因为数据库中不提供此数据。 在环境的&#x200B;**[!UICONTROL Example of call data]**&#x200B;选项卡中，必须添加值示例才能在预览中使用。 请遵循&#x200B;**nms:interaction**&#x200B;模式扩展中的相同xml结构。 有关详细信息，请参阅[其他数据配置](#additional-data-configuration)。

![](assets/ita_calldata_preview.png)

预览时，单击&#x200B;**[!UICONTROL Content personalization options for the preview]**&#x200B;并在&#x200B;**[!UICONTROL Call data]**&#x200B;字段中选择一个值。

![](assets/ita_calldata_preview2.png)

### 存储{#storage}

在调用引擎期间，您可以在命题表中存储其他数据以丰富数据库。 此数据可用于报表、ROI计算或后续流程。

>[!NOTE]
>
>您必须已扩展&#x200B;**nms:compationRcp**&#x200B;模式并声明将包含要存储的数据的字段。 有关此内容的更多信息：[其他数据配置](#additional-data-configuration)。

在优惠空间中，转到&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡并单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

在&#x200B;**[!UICONTROL Storage path]**&#x200B;列中，选择命题表中的存储字段。 在&#x200B;**[!UICONTROL Expression]**&#x200B;列中，选择&#x200B;**[!UICONTROL Interaction]**&#x200B;节点中的其他字段。

在生成建议或接受建议时(当用户单击优惠时)，您可以检索呼叫数据。

![](assets/ita_calldata_storage.png)

