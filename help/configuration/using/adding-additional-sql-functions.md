---
product: campaign
title: 添加其他 SQL 函数
description: 添加其他 SQL 函数
audience: configuration
content-type: reference
topic-tags: api
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---

# 添加其他 SQL 函数{#adding-additional-sql-functions}

![](../../assets/v7-only.svg)

## 简介 {#introduction}

Adobe Campaign允许用户定义 **自己的功能** 可以访问SQL函数的SQL函数，包括数据库提供的函数和控制台中尚未提供的函数。 例如，这对于聚合函数（平均、最大、总和）非常有用，这些函数只能在服务器上计算，或者当数据库提供了一种实施某些函数的更简单方法时，也不能“手动”在控制台中写入表达式（例如，日期管理）时。

如果您想使用Adobe Campaign控制台尚未提供的最近或不常见的数据库引擎SQL函数，则也可以使用此机制。

添加这些函数后，它们将像其他预定义函数一样显示在表达式编辑器中。

>[!IMPORTANT]
>
>控制台中的SQL函数调用不再自然地发送到服务器。 因此，此处描述的机制将 **唯一的方法** 意外SQL函数服务器上。

## 安装 {#installation}

要添加的函数位于 **XML格式的&quot;package&quot;文件**，其结构详见下段。

要从控制台安装它，请选择 **工具/高级/导入包** 选项，然后 **[!UICONTROL Install from file]** ，并按照导入向导中的说明操作。

>[!IMPORTANT]
>
>警告：即使导入的函数列表直接显示在函数编辑器中，但在重新启动Adobe Campaign之前，它们将不可用。

## 要导入的包的一般结构 {#general-structure-of-package-to-import}

要添加的函数可在 **&quot;package&quot;文件** 格式。 示例如下：

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* 的 **name**, **命名空间** 和 **标签** 仅供参考。 它们允许您在已安装的资源包列表（资源管理器/管理/资源包管理/已安装的资源包）中查看资源包的摘要。
* 的 **buildVersion** 和 **buildNumber** 字段为必填字段。 它们必须对应于控制台所连接的服务器号。 此信息可在“Help/About”框中找到。
* 以下几块， **实体** 和 **丧葬** 为必填项。 在funcList中，字段“name”和“namespace”是必填字段，但其名称由用户自行决定，并且它们唯一地指定函数列表。

   这意味着如果导入了具有相同命名空间/名称对的其他函数列表（此处为“cus::myList”），则之前导入的函数将被删除。 相反，如果更改此命名空间/名称对，则会将新导入的一系列函数添加到前一个函数中。

* 的 **群组** 元素允许您指定导入函数在函数编辑器中显示的函数组。 @name属性可以是已存在的名称（在这种情况下，函数将添加到考虑的组），也可以是新名称（在这种情况下，它将显示在新组中）。
* 提醒：@name属性在 `<group>` 元素包括：

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>确保完成@label属性：这是将在可用函数列表中显示的名称。 如果未输入任何内容，则组将没有名称。 但是，如果您输入的名称不是现有名称，则整个组的名称将发生更改。

如果要将函数添加到多个不同的组，可以创建多个 `<group>`  在同一列表中跟踪元素。

最后， `<group>` 元素可以包含一个或多个函数的定义，这些函数是包文件的用途。 的  `<function>`   元素在以下段落中进行了详细说明。

## 函数描述符 &lt;function>&lt;/function> {#function-descriptor--function-}

本案是我们希望提供 **函数实现**.

以下是“相对成熟度”函数的示例，该函数使用年龄来指示该人被视为成熟的年份。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

的 **@name** 字段引用函数的名称，而“args”是将在描述中显示的参数列表。 在这种情况下，函数将显示为“relativeMaturity( `<age>` )”。

* **帮助** 是表达式编辑器窗口底部显示的字段。
* **@display** 是一条信息丰富的信息。

   >[!NOTE]
   >
   >在@help和@display属性中，字符串“$1”表示在第一个函数参数（此处为“Age”）中给定的名称。 $2、$3..表示以下参数。 在下面详@body的属性中， $1指定在调用期间传递到函数的参数值。

   >[!NOTE]
   >
   >描述必须是包含有效XML字符的字符串：请注意使用“&lt;”和“>”，而不是&lt;和>。

* **@type** 是函数返回类型，是标准值(long、string、byte、datetime..)。 如果忽略该函数，则服务器会在实现函数的表达式中确定可用类型中的最佳类型。
* **@minArgs** 和 **maxArgs** 指定参数的参数数（最小和最大）。 例如，对于具有2个参数的函数，minArgs和maxArgs将分别为2和2。 对于3个参数加上1个可选参数，它们将分别为3和4个。
* 最后， **providerPart** 元素提供函数实施。

   * 的 **提供程序** 属性是强制性的，它指定为其提供实施的数据库系统。 如示例所示，当表达式语法或基础函数不同时，可以根据数据库提供替代实施。
   * 的 **@body** 属性包含函数实现。 请注意：此实施必须是数据库语言（而非代码块）的表达式。 根据数据库的不同，表达式可以是仅返回单个值的子查询(“（从表中选择列，其中……）”)。 例如，Oracle中就是这种情况（查询必须用方括号写入）。

   >[!NOTE]
   >
   >如果定义的函数可能只查询一个或两个数据库，则我们始终只能提供与这些数据库对应的定义。

## “传递”函数描述符 {#pass-through--function-descriptor}

特殊函数描述符为 **&quot;传递&quot;** 块，具有未指定的“提供程序”数据库系统。 在这种情况下，“body”实施只能包含单个函数调用，其语法与所使用的数据库无关。 同时，“ProviderPart”块是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在这种情况下，添加函数仅用于使数据库函数（默认情况下不可用）现在对客户端可见。

## 示例 {#examples}

在预定义的包“xtkdatakitfuncList.xml”中可以找到更多函数示例。
