---
product: campaign
title: 挂钩
description: 挂钩
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---

# 挂钩{#hooks}

通过交互中的挂接，可以修改&#x200B;**标准引擎行为**。

**[!UICONTROL Target loading]**&#x200B;和&#x200B;**[!UICONTROL Proposition post-processing]**&#x200B;挂钩在Adobe Campaign的选件空间中配置：

![](assets/interaction_hooks_1.png)

**[!UICONTROL Dynamic offer]**&#x200B;挂接在Adobe Campaign中配置了选件权重：

![](assets/interaction_hooks_2.png)

## 目标正在加载{#target-loading}

此挂接允许您使用来自外部系统的附加数据扩充联系人（由即装即用查询加载）的用户档案。

收集的数据必须插入到呼叫数据节点（交互节点）中。 集成商必须预先扩展了呼叫数据模式，以定义所收集数据的结构。 用户可以以与标准调用数据相同的方式（在资格规则和个性化级别）访问此数据。

**输入参数：**

* xmlInteraction（xml类型）：交互节点
* aTargetId（表类型）：目标标识符
* sUuid230（字符串类型）：uuid230永久cookie的值
* 名称（字符串类型）：nlid会话cookie的值

**返回参数：**

* 扩充了交互节点（此挂接的第一个参数）

>[!NOTE]
>
>**xmlInteraction**&#x200B;参数包含现成查询加载的联系人的呼叫数据和用户档案。

**示例:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 命题后处理{#proposition-post-processing-}

此挂接允许您检查给定交互中合格命题的一致性和兼容性。 它还允许您定义新的评分或概率计算功能。

使用一致性规则的示例：

* 限制同一呼叫中与同一产品或同一类别关联的命题的数量。
* 仅在同一交互中显示与产品相关的选件。

后处理在分类规则应用和合格命题排序之后以及优先级步骤之前执行。

**输入参数：**

* 建议：合格建议表。 下面是此表中元素结构的示例

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer（xml类型）：符合条件的选件的所有属性的字典（选件代码、类别id、类别全名、开始日期、结束日期、标签、内部名称、选件id、其他选件字段）。 例如

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget（xml类型）：配置文件数据节点
* xmlInteraction（xml类型）：呼叫数据节点
* iPropNumber（整数类型）：预期选件数量

**返回参数：**

* 修正命题列表（挂钩的第一个参数）
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

## 动态选件{#dynamic-offer}

此挂接允许您调用外部引擎以选择链接到选件的产品列表。 该选件在资格规则之后和分类规则应用程序之前的选件中进行配置。

预先，集成商应扩展命题&#x200B;**CompestationRcp**&#x200B;架构，并附加产品信息。 要指定此数据的存储位置，空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡中会显示一个&#x200B;**[!UICONTROL Proposition being processed]**&#x200B;链接

![](assets/interaction_hooks_3.png)

**输入参数：**

* xmlOffer（xml类型）：选件（选件代码、类别id、类别全名、开始日期、结束日期、标签、内部名称、选件id、其他选件字段）
* 权重：上下文权重（双重类型）
* xmlTarget（xml类型）：配置文件数据节点
* xmlInteraction（xml类型）：呼叫数据节点

**返回参数：**

将返回要生成的命题表。 此表的每个元素都由以下信息组成：

* 优惠标识符
* 其他产品数据（例如，产品代码）
* 权重

>[!NOTE]
>
>系统会检查输入参数和返回参数的选件ID是否相同。

**示例:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
