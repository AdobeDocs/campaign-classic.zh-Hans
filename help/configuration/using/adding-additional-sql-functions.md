---
solution: Campaign Classic
product: campaign
title: 添加其他 SQL 函数
description: 添加其他 SQL 函数
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---


# 添加其他 SQL 函数{#adding-additional-sql-functions}

## 简介 {#introduction}

Adobe Campaign允许用户定义&#x200B;**其自己的函数**，这些函数可以访问SQL函数，包括数据库提供的函数和控制台中尚未提供的函数。 这对聚合函数（平均、最大、和）很有用，例如，只有在服务器上或当表达式库提供一种实现某些函数的更简单的方法时，才能计算这些函数，而不是在控制台中“手动”写入（如数据管理）。

如果您想使用Adobe Campaign控制台尚未提供的最近或不常见的数据库引擎SQL函数，也可以使用此机制。

添加这些函数后，它们将像其他预定义函数一样显示在表达式编辑器中。

>[!IMPORTANT]
>
>控制台中的SQL函数调用不再自然地发送到服务器。 因此，此处描述的机制成为在计划外SQL函数服务器上调用&#x200B;**的唯一方法。**

## 安装{#installation}

要添加的函数位于&#x200B;**&quot;package&quot;文件中，XML格式为**，其结构在以下段落中有详细介绍。

要从控制台进行安装，请从菜单中选择&#x200B;**工具／高级／导入包**&#x200B;选项，然后选择&#x200B;**[!UICONTROL Install from file]**，然后按照导入向导中的说明进行安装。

>[!IMPORTANT]
>
>警告：即使导入的函数的列表直接出现在函数编辑器中，它们也直到重新启动Adobe Campaign后才可用。

## 要导入{#general-structure-of-package-to-import}的包的常规结构

要添加的函数可在&#x200B;**&quot;package&quot; file**&#x200B;中以XML格式找到。 以下是一个示例：

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

* **名称**、**命名空间**&#x200B;和&#x200B;**标签**&#x200B;仅供参考。 它们允许您在已安装的包列表（Explorer/Administration/Package management/Installed包）中视图包的摘要。
* **buildVersion**&#x200B;和&#x200B;**buildNumber**&#x200B;字段为必填字段。 它们必须与控制台所连接的服务器号相对应。 此信息可在“帮助／关于”框中找到。
* 以下块（**entities**&#x200B;和&#x200B;**funclist**）是必填的。 在funcList中，字段“name”和“命名空间”是必填字段，但其名称由用户决定，并且它们以唯一方式指定函数列表。

   这意味着，如果导入了具有相同列表/名称对（此处为“cus::myList”）的其他函数命名空间，则将删除以前导入的函数。 反之，如果更改此命名空间/名称对，则新导入的一系列函数将添加到前一个函数。

* 通过&#x200B;**group**&#x200B;元素，可指定在函数编辑器中显示导入函数的函数组。 @name属性可以是已存在的名称（在这种情况下，函数将添加到被考虑的组），也可以是新名称（在这种情况下，它将显示在新组中）。
* 提醒：`<group>`元素中@name属性的可能值为：

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
>确保完成@label属性：这是将在可用函数列表中显示的名称。 如果不输入任何内容，则组将没有名称。 但是，如果输入的名称不是现有名称，则整个组的名称将发生更改。

如果要向多个不同组添加函数，可以在同一列表跟踪多个`<group>`元素。

最后，`<group>`元素可以包含一个或多个函数的定义，即包文件的用途。 `<function>`   元素在以下段落中详细介绍。

## 函数描述符&lt;function>&lt;/function> {#function-descriptor--function-}

此处介绍的案例是一个一般案例，我们希望提供&#x200B;**函数实现**。

下面是一个&quot;相对成熟度&quot;函数的示例，该函数使用年龄来表示该人被认为成熟的年份。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

**@name**&#x200B;字段引用函数的名称，而“args”是将在说明中显示的参数的列表。 在这种情况下，函数在函数选择窗口中将显示为“relativeMaturity(`<age>`)”。

* **帮** 助是表达式编辑器窗口底部显示的字段。
* **@** display是一条信息性消息。

   >[!NOTE]
   >
   >在@help和@display属性中，字符串“$1”表示在第一个函数参数（此处为“年龄”）中指定的名称。 $2, $3...表示以下参数。 在下面详细描述的@body属性中，$1指定在调用过程中传递给函数的参数值。

   >[!NOTE]
   >
   >说明必须是包含有效XML字符的字符串：请注意使用“&lt;”和“>”而不是&lt;和>。

* **@** typeis是函数返回类型，是标准值(long、string、byte、datetime...)。如果忽略，则服务器在实现该功能的表达式内确定可用类型中的最佳类型。
* **@** minArgs **** 和maxArgs指定参数的参数数（最小和最大）。例如，对于具有2个参数的函数，minArgs和maxArgs将分别为2和2。 对于3个参数，加1个可选参数，它们分别为3和4。
* 最后，**providerPart**&#x200B;元素提供函数实现。

   * **provider**&#x200B;属性是必需的，它指定为其提供实现的数据库系统。 如示例所示，当表达式语法或基础函数不同时，可以根据数据库提供替代实现。
   * **@body**&#x200B;属性包含函数实现。 请注意：此实现必须是表达式库语言（不是代码块）。 根据表达式库，查询可以是仅返回单个值的子(“（从表中选择列，其中……）”)。 例如，在Oracle就是如此(查询必须写在括号中)。

   >[!NOTE]
   >
   >如果定义的函数可能只查询一个或两个数据库，我们始终只能提供与这些数据库对应的定义。

## “传递”函数描述符{#pass-through--function-descriptor}

特殊的函数描述符是&#x200B;**&quot;pass-through&quot;**&#x200B;块，具有未指定的&quot;provider&quot;数据库系统。 在这种情况下，“body”实现只能包含一个语法不依赖于所使用的数据库的函数调用。 同时，“ProviderPart”块是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在这种情况下，添加函数仅用于使数据库函数成为默认不可用的函数，现在客户端可以看到它。

## 示例{#examples}

在预定义的包“xtkdatakitfuncList.xml”中可以找到更多函数示例。
