---
solution: Campaign Classic
product: campaign
title: 限制 PII 视图
description: 限制 PII 视图
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---


# 限制PI视图{#restricting-pii-view}

## 概述 {#overview}

某些客户需要市场营销用户才能访问数据记录，但不希望他们查看个人身份信息(PII)，如名字、姓氏或电子邮件地址。 Adobe Campaign提出了一种保护隐私和防止活动运营商滥用数据的方法。

## 实现{#implementation}

可以应用于任何元素或属性的新属性已添加到模式中，它补充了现有属性&#x200B;**[!UICONTROL visibleIf]**。 此属性为：**[!UICONTROL accessibleIf]**。 当包含与当前用户上下文相关的XTK表达式时，它可以利用&#x200B;**[!UICONTROL HasNamedRight]**&#x200B;或&#x200B;**[!UICONTROL $(login)]**。

您可以找到一个显示以下用法的收件人模式扩展示例：

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

主要属性有：

* **[!UICONTROL visibleIf]** :从元数据中隐藏字段，因此无法在模式视图、列选择或表达式生成器中访问它们。但这不会隐藏任何数据，如果字段名称是在表达式中手动输入的，则值将显示。
* **[!UICONTROL accessibleIf]** :隐藏数据（用空值替换它），以避免产生查询。如果visibleIf为空，则它获得与&#x200B;**[!UICONTROL accessibleIf]**&#x200B;相同的表达式。

以下是在活动中使用此属性的后果：

* 控制台中不会使用通用查询编辑器显示数据，
* 在概述列表和记录列表（控制台）中，数据将不可见。
* 数据将在详细视图中变为只读。
* 数据只能在过滤器中使用（这意味着使用某些二分法策略，您仍可以猜测值）。
* 使用受限字段构建的任何表达式也会受到限制：lower(@email)与@email一样方便。
* 在工作流中，您可以将受限列作为过渡的额外列添加到目标人群中，但Adobe Campaign用户仍无法访问该列。
* 在组(列表)中存储目标群体时，存储字段的特性与数据源相同。
* 默认情况下，JS代码无法访问数据。

## 建议{#recommendations}

在每个投放中，电子邮件地址都会被复制到&#x200B;**[!UICONTROL broadLog]**&#x200B;和&#x200B;**[!UICONTROL forecastLog]**&#x200B;表中：因此，这些字段也需要得到保护。

以下是用于实现此功能的日志表扩展示例：

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>此限制适用于非技术用户：拥有相关权限的技术用户将能够检索数据。 因此，此方法不是100%安全。

