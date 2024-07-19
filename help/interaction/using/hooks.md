---
product: campaign
title: 挂钩
description: 挂钩
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 1%

---

# 修改标准引擎行为{#hooks}



交互中的挂接允许您修改&#x200B;**标准引擎行为**。

在Adobe Campaign的选件空间中配置了&#x200B;**[!UICONTROL Target loading]**&#x200B;和&#x200B;**[!UICONTROL Proposition post-processing]**&#x200B;挂钩：

![](assets/interaction_hooks_1.png)

在Adobe Campaign中，**[!UICONTROL Dynamic offer]**&#x200B;挂接配置了选件权重：

![](assets/interaction_hooks_2.png)

## 正在加载目标 {#target-loading}

此挂接允许您使用来自外部系统的附加数据扩充联系人的用户档案（由现成查询加载）。

收集的数据必须插入到调用数据节点（交互节点）中。 集成商必须预先扩展了调用数据模式才能定义所收集数据的结构。 用户可以按与标准呼叫数据相同的方式访问此数据（在资格规则和个性化级别）。

**输入参数：**

* xmlInteraction （xml类型）：交互节点
* aTargetId（表类型）：目标标识符
* sUuid230（字符串类型）： uuid230永久cookie的值
* sNlid（字符串类型）： nlid会话Cookie的值

**返回参数：**

* 扩充了交互节点（此挂接的第一个参数）

>[!NOTE]
>
>**xmlInteraction**&#x200B;参数包含调用数据和由现成查询加载的联系人的配置文件。

**示例：**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 建议后处理 {#proposition-post-processing-}

通过此挂接，您可以检查给定交互中符合条件的建议的一致性和兼容性。 它还允许您定义新的评分或概率计算功能。

使用一致性规则的示例：

* 限制同一调用中、链接到相同产品或相同类别的建议数量。
* 在同一交互中仅显示与产品相关的优惠。

后处理在分类规则应用和合格建议排序之后，在优先级划分步骤之前执行。

**输入参数：**

* a建议：合格建议的表。 以下是此表中元素结构的示例

  ```
  { offer_id:1234,
    weight:2}
  ```

* dicOffer（xml类型）：符合条件的优惠的所有属性（优惠代码、类别ID、类别全名、开始日期、结束日期、标签、内部名称、优惠ID、其他优惠字段）的字典。 例如

  ```
  { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
    "1243": ...}
  ```

* xmlTarget （xml类型）：配置文件数据节点
* xmlInteraction （xml类型）：调用数据节点
* iPropNumber （整数类型）：预期选件的数量

**返回参数：**

* 已修改建议列表（挂接的第一个参数）
* 已修改的交互节点

**示例：**

```
var aReturnedProps = [];

if( aProposition.length > 0 )
{
  var iReturnedProps = 0;
  for( var iPropIdx = 0; iPropIdx < aProposition.length && iReturnedProps < iPropNumber; iPropIdx ++ )
  {
    // Check a consistency rule for instance
    if( true )
    {
      aReturnedProps.push(aProposition[iPropIdx]);
      iReturnedProps++;
    }
  }
}

return aReturnedProps;
```

## 动态选件 {#dynamic-offer}

此挂接允许您调用外部引擎以选择链接到优惠的产品列表。 它是在资格规则之后、类型规则应用程序之前在选件中配置的。

之前，集成商应使用产品上的附加信息来扩展建议&#x200B;**PropositionRcp**&#x200B;架构。 要指定此数据的存储位置，可在空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡中使用&#x200B;**[!UICONTROL Proposition being processed]**&#x200B;链接

![](assets/interaction_hooks_3.png)

**输入参数：**

* xmlOffer （xml类型）：选件（选件代码、类别ID、类别全名、开始日期、结束日期、标签、内部名称、选件ID、其他选件字段）
* dWeight：上下文权重（双类型）
* xmlTarget （xml类型）：配置文件数据节点
* xmlInteraction （xml类型）：调用数据节点

**返回参数：**

返回要生成的建议表。 此表的每个元素均由以下信息组成：

* 优惠标识符
* 其他产品数据（例如产品代码）
* 粗细

>[!NOTE]
>
>系统会检查输入参数和返回参数的选件ID是否相同。

**示例：**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
