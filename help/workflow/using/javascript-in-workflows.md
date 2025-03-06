---
product: campaign
title: 工作流中的 JavaScript 代码示例
description: 这些示例说明如何在工作流中使用JavaScript代码
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 3%

---

# 工作流中的 JavaScript 代码示例{#javascript-in-workflows}



以下示例说明如何在工作流中使用JavaScript代码：

* [写入数据库](#write-example)
* [查询数据库](#read-example)
* [使用静态SOAP方法触发工作流](#trigger-example)
* [使用非静态SOAP方法与数据库交互](#interact-example)

[了解关于静态和非静态SOAP方法的更多信息](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)。

在这些示例中，使用ECMAScript for XML (E4X)扩展。 使用此扩展，您可以在同一个脚本中组合JavaScript调用和XML基元。

要尝试这些示例，请执行以下步骤：

1. 创建工作流并将以下活动添加到工作流中：
   1. 开始活动
   1. JavaScript代码活动
   1. 结束活动

   [了解关于生成工作流的详细信息](building-a-workflow.md)。

1. 将JavaScript代码添加到活动中。 [了解详情](advanced-parameters.md)。
1. 保存工作流。
1. 测试示例：
   1. 启动工作流。 [了解详情](starting-a-workflow.md)。
   1. 打开日记帐。 [了解详情](monitoring-workflow-execution.md#displaying-logs)。

## 示例1：写入数据库{#write-example}

要写入数据库，可以在`xtk:session`架构上使用静态`Write`方法：

1. 以XML撰写写入请求。

1. 写入记录：

   1. 在`xtk:session`架构中调用`Write`方法。

      >[!IMPORTANT]
      > 如果您使用Adobe Campaign v8，我们建议您在Snowflake表中对`Write`方法的&#x200B;**摄取**&#x200B;和&#x200B;**数据更新/删除** API使用暂存机制。 [了解更多信息](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}。

   1. 将XML代码作为写入请求的参数传递。

### 步骤1：编写写入请求

您可以添加、更新和删除记录。

#### 插入记录

由于`insert`操作是默认操作，因此无需指定。

将此信息指定为XML属性：

* 要修改的表的模式
* 要填充的表字段

例如：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### 更新记录

使用`_update`操作。 [了解详情](../../configuration/using/data-oriented-apis.md)。

将此信息指定为XML属性：

* 要修改的表的模式
* 要更新的表字段
* 标识要更新的记录所需的关键参数

例如：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### 删除记录

使用`DeleteCollection`方法。 [了解详情](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)。

指定以下信息：

* 要修改的表的模式
* 以XML元素的形式标识要更新的记录所需的`where`子句

例如：

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### 第2步：写入记录

在`xtk:session`架构上调用非静态`Write`方法：

```javascript
xtk.session.Write(myXML)
```

此方法未返回任何值。

将完整代码添加到工作流中的JavaScript代码活动：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

本视频说明如何写入数据库：
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## 示例2：查询数据库{#read-example}

要查询数据库，可以使用非静态`xtk:queryDef`实例方法：

1. 以XML格式编写查询。
1. 创建查询对象。
1. 运行查询。

### 步骤1：撰写查询

指定`queryDef`实体的XML代码。

语法：

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

指定以下信息：

* 要读取的表的模式
* 操作
* 在`select`子句中要返回的列
* `where`子句中的条件
* `orderBy`子句中的筛选条件

您可以使用以下操作：

| 操作 | 结果 |
| --- | --- |
| `select` | 零个或多个元素将作为集合返回。 |
| `getIfExists` | 返回一个元素。 如果不存在匹配元素，则会返回空元素。 |
| `get` | 返回一个元素。 如果不存在匹配元素，则会返回错误。 |
| `count` | 以具有`count`属性的元素形式返回了匹配记录数。 |

将`select`、`where`和`orderBy`子句编写为XML元素：

* `select`子句

  指定要返回的列。 例如，要选择人员的名字和姓氏，请编写以下代码：

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  使用`nms:recipient`架构时，元素将以下列形式返回：

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* `where`子句

  要指定条件，请使用`where`子句。 例如，要选择位于&#x200B;**Training**&#x200B;文件夹中的记录，您可以编写以下代码：

  ```xml
  <where>
      <condition expr="[folder/@label]='Training'"/>
  </where>
  ```

  组合多个表达式时，在第一个表达式中使用布尔运算符。 例如，要选择名为Isabel Garcia的所有人员，您可以编写以下代码：

  ```xml
  <condition boolOperator="AND" expr="@firstName='Isabel'"/>
  <condition expr="@lastName='Garcia'"/>
  ```

* `orderBy`子句

  要对结果集进行排序，请将`orderBy`子句指定为具有`sortDesc`特性的XML元素。 例如，要按升序对姓氏进行排序，您可以编写以下代码：

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### 步骤2：创建查询对象

要从XML代码创建实体，请使用`create(`*`content`*`)`方法：

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

为`create(`*`content`*`)`方法添加要创建的实体的架构前缀。

*`content`*&#x200B;参数是字符串参数，是可选的。 此参数包含描述实体的XML代码。

### 步骤3：运行查询

执行以下步骤：

1. 在`queryDef`实体上调用`ExecuteQuery`方法：

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. 处理结果：
   1. 使用循环构造对`select`操作的结果进行迭代。
   1. 使用`getIfExists`操作测试结果。
   1. 使用`count`操作对结果进行计数。

#### `select`操作的结果

所有匹配项都将作为集合返回：

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

要循环遍历结果，请使用`for each`循环：

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

循环包括一个本地收件人变量。 对于收件人集合中返回的每个收件人，都会打印出收件人的电子邮件。 [了解有关`logInfo`函数的更多信息](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)。

#### `getIfExists`操作的结果

每个匹配都作为元素返回：

```xml
<recipient id="52,378,079">
```

如果没有匹配项，则返回空元素：

```xml
<recipient/>
```

您可以引用主键节点，例如`@id`属性：

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### `get`操作的结果

一个匹配项作为元素返回：

```xml
<recipient id="52,378,079">
```

如果没有匹配项，则会返回错误。

>[!TIP]
>
>如果您知道存在匹配项，请使用`get`操作。 否则，请使用`getIfExists`操作。 如果使用此最佳实践，则错误会显示意外问题。 如果您使用`get`操作，请不要使用`try…catch`语句。 该问题由工作流的错误处理过程处理。

#### `count`操作的结果

返回具有`count`属性的元素：

```xml
<recipient count="200">
```

要使用结果，请参阅`@count`属性：

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

对于`select`操作，请将此代码添加到工作流中的JavaScript代码活动：

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

由于`select`操作是默认操作，因此无需指定。

本视频说明如何从数据库读取：
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## 触发工作流 {#trigger-example}

例如，您可以在技术工作流中以编程方式触发工作流，或处理用户在Web应用程序页面上输入的信息。

工作流触发通过使用事件起作用。 您可以将这些功能用于事件：

* 若要发布事件，您可以使用静态`PostEvent`方法。 [了解详情](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)。
* 若要接收事件，您可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活动。 [了解详情](external-signal.md)。

您可以通过不同方式触发工作流：

* 您可以内联触发工作流，即从&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动的主脚本中触发。
* 另一个工作流完成后，您可以触发该工作流：
   * 向初始工作流的&#x200B;**[!UICONTROL End]**&#x200B;活动添加初始化脚本。
   * 在目标工作流的开头添加&#x200B;**[!UICONTROL External signal]**&#x200B;活动。

     完成初始工作流后，将发布事件。 将激活传出过渡并填充事件变量。 然后，目标工作流接收该事件。

     >[!TIP]
     >
     >作为最佳实践，在向活动添加脚本时，请用双连字符将活动名称括起来，例如`-- end --`。 [了解更多](workflow-best-practices.md)工作流最佳实践。

`PostEvent`方法的语法：

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

在此示例中，工作流完成后，会向&#x200B;**wkfExampleReceiver**&#x200B;工作流的&#x200B;**信号**&#x200B;活动传递一个简短文本：

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

由于最后一个参数设置为`false`，每次完成初始工作流时，都会触发&#x200B;**wkfExampleReceiver**&#x200B;工作流。

在触发工作流时，请牢记以下原则：

* `PostEvent`命令异步运行。 命令位于服务器队列中。 方法会在事件发布后返回。
* 必须启动目标工作流。 否则，错误将写入日志文件。
* 如果目标工作流已暂停，则`PostEvent`命令将排入队列，直到工作流恢复为止。
* 触发的活动不要求任务正在执行。

本视频说明如何使用静态API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

本视频说明如何触发工作流：
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## 与数据库交互 {#interact-example}

以下示例显示如何执行这些操作：

* 在架构上使用`get`和`create`方法以使用非静态SOAP方法
* 创建执行SQL查询的方法
* 使用`write`方法插入、更新和删除记录

执行以下步骤：

1. 定义查询：

   * 在对应的架构上使用`create`方法检索实体，例如`xtk:workflow`架构。 [了解详情](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)。
   * 使用`queryDef`方法发出SQL查询。

1. 使用`ExecuteQuery`方法运行查询。 [了解详情](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)。

   使用`for each`循环检索结果。

### 带有`select`子句的`queryDef`方法的语法

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create`方法

#### 示例1：选择记录并写入日记帐

已选择位于&#x200B;**wfExamples**&#x200B;文件夹中的工作流的内部名称。 结果按内部名称升序排序，并写入日志。

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### 示例2：删除记录

将选择名为Chris Smith的所有收件人的名字、姓氏、电子邮件和ID。 结果按电子邮件升序排序，并写入日志。 使用`delete`操作删除所选记录。

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### 示例3：选择记录并写入日记帐

在此示例中，使用非静态方法。 已选择其信息存储在&#x200B;**1234**&#x200B;文件夹中且其电子邮件域名以“adobe”开头的所有收件人的电子邮件和出生年份。 结果按出生日期降序排序。 收件人的电子邮件将写入日志。

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write`方法

您可以插入、更新和删除记录。 您可以在Adobe Campaign中的任何架构上使用`Write`方法。 由于此方法为静态方法，因此您无需创建对象。 您可以使用以下操作：

* `update`操作
* `insertOrUpdate`操作，带有`_key`参数以标识要更新的记录

  如果未指定&#x200B;**收件人**&#x200B;文件夹，则如果存在匹配项，则会在任何子文件夹中更新记录。 否则，将在根&#x200B;**收件人**&#x200B;文件夹中创建记录。

* `delete`操作

>[!IMPORTANT]
> 如果您使用Adobe Campaign v8，我们建议您在Snowflake表中对`Write`方法的&#x200B;**摄取**&#x200B;和&#x200B;**数据更新/删除** API使用暂存机制。 [了解更多信息](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target="_blank"}。

#### 示例1：插入或更新记录

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### 示例2：删除记录

此示例将静态方法与非静态方法结合使用。

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

本视频说明如何使用非静态API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

本视频演示了在工作流中使用非静态API方法的示例：
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## 相关主题

* [面向数据的API](../../configuration/using/data-oriented-apis.md)
* [JavaScript 脚本和模板](javascript-scripts-and-templates.md)
* [JavaScript 中的 SOAP 方法](../../configuration/using/soap-methods-in-javascript.md)

### API文档

* [SOAP调用示例](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* 方法：
   * [创建](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [写入](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo函数](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)
