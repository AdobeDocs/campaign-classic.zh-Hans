---
title: 限制PII视图
seo-title: 限制PII视图
description: 限制PII视图
seo-description: null
page-status-flag: never-activated
uuid: 4dddc7f5-dac3-47b3-b3cb-92b47eb595fa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 550439c1-978c-414e-be5b-a9e1a202c4cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 限制PII视图{#restricting-pii-view}

## 概述 {#overview}

一些客户需要营销用户才能访问数据记录，但不希望他们查看个人身份信息(PII)，如名字、姓或电子邮件地址。 Adobe Campaign提出了一种保护隐私、防止数据被常规营销活动运营商滥用的方法。

## 实施 {#implementation}

可以应用于任何元素或属性的新属性已添加到架构中，它补充了现有属性 **[!UICONTROL visibleIf]** 。 此属性为： **[!UICONTROL accessibleIf]** . 当包含与当前用户上下文相关的XTK表达式时，它可以利用或( **[!UICONTROL HasNamedRight]** 例 **[!UICONTROL $(login)]** 如)。

您可以找到以下显示了此用法的收件人架构扩展示例：

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

* **[!UICONTROL visibleIf]** :隐藏元数据中的字段，因此无法在架构视图、列选择或表达式构建器中访问它们。 但这不会隐藏任何数据，如果字段名称是在表达式中手动输入的，则值将显示出来。
* **[!UICONTROL accessibleIf]** :从生成的查询中隐藏数据（用空值替换它）。 如果visibleIf为空，则其表达式与相同 **[!UICONTROL accessibleIf]** 。

下面是在Campaign中使用此属性的后果：

* 数据不会使用控制台中的通用查询编辑器显示，
* 数据将不会显示在概述列表和记录列表（控制台）中。
* 在详细视图中，数据将变为只读。
* 数据只能在过滤器中使用（这意味着使用某些二分法策略，您仍可以猜测值）。
* 使用受限字段构建的任何表达式也会受到限制：lower(@email)与@email一样具有辅助功能。
* 在工作流中，您可以将受限列作为过渡的额外列添加到目标人群，但Adobe Campaign用户仍无法访问该列。
* 当将目标群体存储在组（列表）中时，所存储字段的特性与数据源相同。
* 默认情况下，JS代码无法访问数据。

## 建议 {#recommendations}

在每个分发中，电子邮件地址都会被复制到 **[!UICONTROL broadLog]** 和表中 **[!UICONTROL forecastLog]** :因此，这些字段也需要得到保护。

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

