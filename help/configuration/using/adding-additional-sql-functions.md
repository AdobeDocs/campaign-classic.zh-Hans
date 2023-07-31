---
product: campaign
title: 添加其他 SQL 函数
description: 了解如何定义其他SQL函数
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---

# 定义其他SQL函数{#adding-additional-sql-functions}

Adobe Campaign允许用户定义 **他们自己的功能** 可以访问SQL函数（包括数据库提供的函数和控制台中尚未提供的函数）的用户。 这对聚合函数(average、maximum、sum)非常有用，例如，只能在服务器上计算聚合函数，或者在数据库提供实现某些函数的更简单方法时，才可以计算聚合函数，而不是在控制台中“手动”写入表达式（例如日期管理）。

如果要使用最近或不常见的数据库引擎SQL函数(Adobe Campaign控制台尚未提供)，也可以使用此机制。

添加这些函数后，它们会像其他预定义函数一样显示在表达式编辑器中。

>[!IMPORTANT]
>
>控制台中的SQL函数调用不再自然发送到服务器。 因此，此处描述的机制变为 **致电的唯一方法** 在计划外的SQL函数服务器上。

## 安装 {#installation}

要添加的函数位于 **XML格式的“包”文件**，其结构详见下段。

要从控制台安装它，请选择 **Tools/Advanced/Import包** 选项，然后 **[!UICONTROL Install from file]** ，并按照导入向导中的说明操作。

>[!IMPORTANT]
>
>警告：即使导入的函数列表立即显示在函数编辑器中，这些函数在Adobe Campaign重新启动之后才能使用。

## 要导入的包的一般结构 {#general-structure-of-package-to-import}

要添加的函数位于 **“包”文件** XML格式。 示例如下：

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
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

* 此 **name**， **命名空间** 和 **标签** 仅供参考。 它们允许您在“已安装的包”列表（资源管理器/管理/包管理/已安装的包）中查看包的摘要。
* 此 **buildVersion** 和 **buildnumber** 字段为必填字段。 它们必须与控制台所连接的服务器号相对应。 此信息可在“帮助/关于”框中找到。
* 以下块， **实体** 和 **功能词表** 是必填项。 在funcList中，“name”和“namespace”字段是必填字段，但它们的名称由用户决定，并且它们唯一地指定函数列表。

  这意味着如果导入具有相同命名空间/名称对的其他函数列表（此处为“cus：：myList”），则将删除之前导入的函数。 相反，如果更改此命名空间/名称对，则新的一系列导入函数将添加到前一个函数中。

* 此 **组** element用于指定导入的函数将在函数编辑器中显示的函数组。 @name属性可以是已经存在的名称（这种情况下，函数将添加到考虑的组中）或新名称（这种情况下，它将显示在新组中）。
* 提醒：@name属性的可能值位于 `<group>` 元素为：

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
>确保完成@label属性：这是将显示在可用函数列表中的名称。 如果不输入任何内容，则组将没有名称。 但是，如果输入的名称不是现有名称，则整个组的名称将发生变化。

如果要将函数添加到多个不同的组中，可以添加多个 `<group>`  元素将在同一列表中受到跟踪。

最后， `<group>` 元素可以包含一个或多个函数的定义，这是包文件的用途。 此  `<function>`   下文中将详细介绍该元素。

## 函数描述符 &lt;function>&lt;/function> {#function-descriptor--function-}

这里介绍的案例是一个一般案例，我们在此希望提供 **函数实现**.

以下是“相对成熟”函数的示例，该函数使用年龄指示该人员被视为成熟的年数。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

此 **@name** 字段是指函数的名称，而“args”是将显示在描述中的参数列表。 在这种情况下，该函数将显示为“relativeMaturity ( `<age>` )”。

* **帮助** 是显示在表达式编辑器窗口底部的字段。
* **@display** 是一条信息性消息。

  >[!NOTE]
  >
  >在@help和@display属性中，字符串“$1”表示在第一个函数参数（此处为“Age”）中提供的名称。 $2、$3...将代表以下参数。 在下面详细介绍的@body属性中，$1指定调用期间传递到函数的参数值。

  >[!NOTE]
  >
  >描述必须是有效XML字符的字符串：请注意，使用的是“&lt;”和“>”而不是&lt;和>。

* **@type** 是函数返回类型，是一个标准值(long、string、byte、datetime...)。 如果省略，服务器将在实现函数的表达式中确定可用类型中的最佳类型。
* **@minArgs** 和 **maxArgs** 指定参数的参数数量（最小值和最大值）。 例如，对于带2个参数的函数，minArgs和maxArgs将分别为2和2。 对于3个参数加上1个可选参数，它们将分别为3个和4个。
* 最后， **providerPart** 元素提供函数实现。

   * 此 **提供程序** 属性是必需的，它指定提供实现的数据库系统。 如示例所示，当表达式语法或基础函数不同时，可以根据数据库提供替代实现。
   * 此 **@body** 属性包含函数实现。 请注意：此实现必须是数据库语言中的表达式（不是代码块）。 根据数据库的不同，表达式可以是只返回单个值的子查询(“（从表中选择列，其中……）”)。 例如，在Oracle中就是这种情况（查询必须用方括号编写）。

  >[!NOTE]
  >
  >如果定义的函数可能只查询一两个数据库，则我们始终只能提供与这些数据库对应的定义。

## “传递”函数描述符 {#pass-through--function-descriptor}

一个特殊的函数描述符是 **&quot;pass-through&quot;** 块，带有未指定的“provider”数据库系统。 在这种情况下，“body”实施只能包含单个函数调用，其语法与使用的数据库无关。 同时，“ProviderPart”块是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在这种情况下，添加函数仅用于使默认情况下不可用的数据库函数对客户端可见。

## 示例 {#examples}

在预定义包“xtkdatakitfuncList.xml”中可以找到进一步的函数示例。
