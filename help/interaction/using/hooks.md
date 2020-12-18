---
solution: Campaign Classic
product: campaign
title: 挂钩
description: 挂钩
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# 挂钩{#hooks}

“交互”中的挂接允许您修改&#x200B;**标准引擎行为**。

**[!UICONTROL Target loading]**&#x200B;和&#x200B;**[!UICONTROL Proposition post-processing]**&#x200B;挂钩以Adobe Campaign配置在优惠空间中：

![](assets/interaction_hooks_1.png)

**[!UICONTROL Dynamic offer]**&#x200B;挂接配置了优惠权重:

![](assets/interaction_hooks_2.png)

## 目标加载{#target-loading}

此挂接允许您使用外部系统的额外用户档案来丰富联系人的(即现成查询加载的联系人)。

收集的数据必须插入到调用数据节点（交互节点）中。 集成商必须事先扩展了呼叫数据模式以定义所收集数据的结构。 用户可以以与标准呼叫数据相同的方式访问此数据(在合格规则和个性化级别)。

**输入参数：**

* xmlInteraction（xml类型）:交互节点
* aTargetId（表类型）:目标标识符
* sUuid230（字符串类型）:uuid230永久cookie的值
* sNid（字符串类型）:nid会话cookie的值

**返回参数：**

* 富集交互节点（此挂接的第一个参数）

>[!NOTE]
>
>**xmlInteraction**&#x200B;参数既包含呼叫数据，又包含现成查询加载的联系人用户档案。

**示例:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 后处理命题{#proposition-post-processing-}

通过此挂接，您可以检查给定交互中符合条件的主张的一致性和兼容性。 它还允许您定义新的评分或概率计算功能。

使用一致性规则的示例：

* 限制同一呼叫中、链接到同一产品或同一类别的建议数。
* 仅在同一交互中展示与产品相关的优惠。

在类型规则应用和合格命题排序之后以及在优先级步骤之前执行后处理。

**输入参数：**

* 建议：合格建议表。 下面是此表中元素结构的示例

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer（xml类型）:符合条件优惠的所有属性的字典(优惠代码、类别id、类别全名、开始日期、结束日期、标签、内部名称、优惠id、其他优惠字段)。 例如

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget（xml类型）:用户档案数据节点
* xmlInteraction（xml类型）:调用数据节点
* iPropNumber（整数类型）:预期优惠数

**返回参数：**

* 修改命题的列表（钩的第一个参数）
* 修改的交互节点

**示例:**

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

## 动态优惠{#dynamic-offer}

此挂接允许您调用外部引擎以选择链接到列表的产品优惠。 它是在合格规则之后和优惠应用程序之前的类型规则中配置的。

事先，集成商应使用产品上的附加信息扩展命题&#x200B;**CompationRcp**&#x200B;模式。 要指定此数据的存储位置，在空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡中有一个&#x200B;**[!UICONTROL Proposition being processed]**&#x200B;链接

![](assets/interaction_hooks_3.png)

**输入参数：**

* xmlOffer（xml类型）:优惠(优惠代码、类别id、类别全名、开始日期、结束日期、标签、内部名称、优惠id、其他优惠字段)
* 重量：上下文权重(多次类型)
* xmlTarget（xml类型）:用户档案数据节点
* xmlInteraction（xml类型）:调用数据节点

**返回参数：**

将返回要生成的命题表。 此表的每个元素都包含以下信息：

* 优惠标识符
* 其他产品数据（例如，产品代码）
* 权重

>[!NOTE]
>
>系统检查输入和返回参数的优惠id是否相同。

**示例:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```

