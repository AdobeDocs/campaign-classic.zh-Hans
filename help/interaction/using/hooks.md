---
title: 挂钩
seo-title: 挂钩
description: 挂钩
seo-description: null
page-status-flag: never-activated
uuid: 4394717e-8625-4e2f-9492-3fd9b444a732
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 2b799ad7-b729-4b3e-9adc-1df13259f2a9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 挂钩{#hooks}

“交互”中的挂接允许您修改标 **准引擎行为**。

在Adobe **[!UICONTROL Target loading]** Campaign中 **[!UICONTROL Proposition post-processing]** 的选件空间中配置了这些和挂钩：

![](assets/interaction_hooks_1.png)

此挂 **[!UICONTROL Dynamic offer]** 钩在Adobe Campaign中配置了选件权重：

![](assets/interaction_hooks_2.png)

## 目标加载 {#target-loading}

通过此挂钩，您可以使用来自外部系统的其他数据来丰富联系人（由现成查询加载）的配置文件。

收集的数据必须插入到调用数据节点（交互节点）中。 集成商必须事先扩展了呼叫数据架构以定义所收集数据的结构。 用户可以以与标准呼叫数据相同的方式访问这些数据（在资格规则和个性化级别）。

**输入参数：**

* xmlInteraction（xml类型）:交互节点
* aTargetId（表类型）:目标标识符
* sUuid230（字符串类型）:uuid230永久cookie的值
* sNlid（字符串类型）:内部会话Cookie的值

**返回参数：**

* 富集交互节点（此挂钩的第一个参数）

>[!NOTE]
>
>xmlInteraction **** 参数包含调用数据和现成查询加载的联系人的配置文件。

**例如：**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 命题后处理 {#proposition-post-processing-}

通过此挂钩，您可以检查给定交互中合格命题的一致性和兼容性。 它还允许您定义新的评分或概率计算功能。

使用一致性规则的示例：

* 限制同一调用中、链接到同一产品或同一类别的命题数。
* 仅在同一交互中展示与产品相关的推广信息。

在排版规则应用和合格命题排序之后以及在优先化步骤之前执行后处理。

**输入参数：**

* 主张：符合条件的建议表。 下面是此表中元素结构的示例

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer（xml类型）:符合条件的选件的所有属性的词典（选件代码、类别ID、类别全名、开始日期、结束日期、标签、内部名称、选件ID、其他选件字段）。 例如

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget（xml类型）:配置数据节点
* xmlInteraction（xml类型）:呼叫数据节点
* iPropNumber（整数类型）:预期优惠数量

**返回参数：**

* 修改的命题列表（挂钩的第一个参数）
* 修改的交互节点

**例如：**

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

此挂钩允许您调用外部引擎以选择链接到选件的产品列表。 它在选件中配置的资格规则之后，以及在类型学规则应用程序之前。

在此之前，集成商应扩展命题 **CompationRcp** schema，并附加产品信息。 要指定存储此数据的位置，请 **[!UICONTROL Proposition being processed]** 在空间的选项卡 **[!UICONTROL Storage]** 中提供链接

![](assets/interaction_hooks_3.png)

**输入参数：**

* xmlOffer（xml类型）:选件（选件代码、类别ID、类别全名、开始日期、结束日期、标签、内部名称、选件ID、其他选件字段）
* 重量：上下文粗细（双重类型）
* xmlTarget（xml类型）:配置数据节点
* xmlInteraction（xml类型）:呼叫数据节点

**返回参数：**

将返回要生成的命题表。 此表的每个元素都由以下信息组成：

* 选件标识符
* 其他产品数据（例如，产品代码）
* 重量

>[!NOTE]
>
>系统检查输入和返回参数的选件ID是否相同。

**例如：**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```

