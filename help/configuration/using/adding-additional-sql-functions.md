---
title: 添加其他SQL函数
seo-title: 添加其他SQL函数
description: 添加其他SQL函数
seo-description: null
page-status-flag: never-activated
uuid: d66b5ca2-ac7d-4654-9f0e-9bfe56490c19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 728a95f8-46fe-49a8-a645-a0dd6eeb6615
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 添加其他SQL函数{#adding-additional-sql-functions}

## 简介 {#introduction}

Adobe Campaign允许用户定义自己 **的函数** ，这些函数可以访问SQL函数，包括数据库提供的函数和控制台中尚未提供的函数。 这对聚合函数（平均、最大、和）很有用，例如，只能在服务器上计算该函数，或者当数据库提供一种实现某些函数的更简单的方法时，而不是在控制台中“手动”编写表达式（例如，日期管理）时。

如果您希望使用Adobe Campaign控制台尚未提供的最近或不常见的数据库引擎SQL函数，也可以使用此机制。

添加这些函数后，它们将像其他预定义函数一样显示在表达式编辑器中。

>[!IMPORTANT]
>
>控制台中的SQL函数调用不再自然地发送到服务器。 因此，此处介绍的机制 **成为调用计划外SQL函数服务器** 的唯一方式。

## 安装 {#installation}

要添加的函数以XML格式 **放入“包”文件中**，其结构在以下段落中详细介绍。

要从控制台中安装它，请从菜单中选择 **Tools/Advanced/Import包选项** ，然后选择 **[!UICONTROL Install from file]** ，并按照导入向导中的说明进行操作。

>[!IMPORTANT]
>
>警告：即使导入的函数列表直接显示在函数编辑器中，它们也直到Adobe Campaign重新启动后才可用。

## 要导入的包的常规结构 {#general-structure-of-package-to-import}

要添加的函数可在XML格式的“ **package”文件中找** 到。 以下是一个示例：

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

* 名 **称**、 **namespace****** 和标签仅供参考。 这些组件允许您在已安装的包列表中查看包的摘要（资源管理器／管理／包管理／已安装的包）。
* buildVersion **和buildNumber****** 字段是必填字段。 它们必须与控制台所连接的服务器号相对应。 此信息位于“帮助／关于”框中。
* 以下块、实 **体****和基** 础。 在funcList中，字段“name”和“namespace”是必填字段，但其名称由用户决定，并且它们以唯一方式指定函数列表。

   这意味着，如果导入另一个具有相同命名空间／名称对的函数列表（此处为“cus::myList”），则之前导入的函数将被删除。 相反，如果更改此命名空间／名称对，则新的导入函数系列将添加到上一个函数系列。

* 组 **元素** 允许您指定在函数编辑器中显示导入的函数的函数组。 @name属性可以是已存在的名称（在这种情况下，函数将添加到被考虑的组）或新名称（在这种情况下，它将显示在新组中）。
* 提醒：元素中@name属性的可能 `<group>` 值为：

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
>确保完成@label属性：这是将在可用函数列表中显示的名称。 如果未输入任何内容，则用户组将没有名称。 但是，如果输入的名称不是现有名称，则整个组的名称将发生更改。

如果要将函数添加到多个不同的组中，您可以在同一列 `<group>` 表中跟踪多个元素。

最后，元 `<group>` 素可以包含一个或多个函数的定义，即包文件的用途。 元 `<function>` 素在以下段落中详细介绍。

## 函数描述符&lt;function>&lt;/function> {#function-descriptor--function-}

这里介绍的情况是一个一般情况，我们希望提供功能 **实现**。

以下是“相对成熟度”函数的示例，该函数使用年龄来表示该人被认为成熟的年份。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

@name **** 字段引用函数的名称，“args”是将在描述中显示的参数列表。 在这种情况下，该函数将在函数选择窗口中显示为“ `<age>` relativeMaturity()”。

* **help** 是表达式编辑器窗口底部显示的字段。
* **@display** 是一条信息性消息。

   >[!NOTE]
   >
   >在@help和@display属性中，字符串“$1”表示在第一个函数参数（此处为“年龄”）中指定的名称。 $2,$3...表示以下参数。 在下面详细描述的@body属性中，$1指定在调用过程中传递给函数的参数值。

   >[!NOTE]
   >
   >说明必须是包含有效XML字符的字符串：请注意使用“&lt;”和“>”而不是&lt;和>。

* **@type** 是函数返回类型，是标准值（长、字符串、字节、日期时间……）。 如果忽略该函数，则服务器在实现该函数的表达式中确定可用类型中的最佳类型。
* **@minArgs** 和 **maxArgs** 指定参数的参数数（最小和最大）。 例如，对于具有2个参数的函数，minArgs和maxArgs将分别为2和2。 对于3个参数，加上1个可选参数，它们分别为3和4。
* 最后，providerPart元 **素提供功能实现** 。

   * provider **属性是必需的** ，它指定为其提供实现的数据库系统。 如示例所示，当表达式语法或基础函数不同时，可以根据数据库提供替代实现。
   * @body **属性包含函数实现** 。 请注意：此实现必须是数据库语言中的表达式（而不是代码块）。 根据数据库，表达式可以是仅返回单个值的子查询(“（从表中选择列，其中……）”)。 例如，Oracle中就是这种情况（查询必须用括号写入）。
   >[!NOTE]
   >
   >如果只有一个或两个数据库可能被定义的函数查询，我们始终只能提供与这些数据库对应的定义。

## “传递”函数描述符 {#pass-through--function-descriptor}

特殊的函数描述符是 **“传递”块** ，具有未指定的“提供者”数据库系统。 在这种情况下，“body”实现只能包含一个语法不依赖于所使用的数据库的函数调用。 同时，“ProviderPart”块是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在这种情况下，添加函数仅用于使数据库函数成为默认情况下不可用的函数，现在对客户端可见。

## 示例 {#examples}

在预定义的包“xtkdatakitfuncList.xml”中可找到更多函数示例。
