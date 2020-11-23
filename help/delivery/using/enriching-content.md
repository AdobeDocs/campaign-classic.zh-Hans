---
solution: Campaign Classic
product: campaign
title: 丰富内容
description: 丰富内容
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# 丰富内容{#enriching-content}

聚合器允许您使用外部数据丰富内容。 此数据来自通用查询或链接表。

## 通用查询 {#generic-queries}

查询通过选项卡中的发布模板进行 **[!UICONTROL Aggregator]** 配置。

检索到的数据将通过其主元素丰富XML输出文档。

从查询返回收件人模式(nms:**收件人**)的示例

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

元 **`<collection-recipient>`** 素表示由文档产生的查询的输入元素。 检索到的数据在此元素下返回；在我们的例子中，是收件人列表。

### 添加查询 {#adding-a-query}

查询参数是使用向导进行编辑的。

1. 在第一页中，指定标签和包含要检索的模式。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >编辑字段 **Path** （路径）用于重命名查询输出元素。

1. 在下一页中，您可以选择要检索的数据。

   ![](assets/d_ncs_content_query2.png)

1. 下一页定义筛选条件。

   ![](assets/d_ncs_content_query3.png)

1. 最后一页启动预览返回的查询。

   ![](assets/d_ncs_content_query4.png)

## 链接的表 {#linked-tables}

链接允许您检索链接到内容的外部数据。

链接数据有两种类型：

* 内容链接：这是本机内容管理模式。 链接的内容将自动集成到XML输出文档中。
* 指向外部表的链接允许访问数据库中的所有其他表，但约束是使用聚合器检索所选链接的数据。

### 链接到内容模式 {#link-to-a-content-schema}

在数据模式中声明内容链接，如下所示：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

链接的定义填充在字符串 **类型**&#x200B;上 **`<element>`**，并且 **expandSchemaTarget属性引** 用目标模式符（我们示例中的“cus:chapter”）。 引用的模式必须是内容模式。

目标元素的内容丰富了链接元素，即示例 **`<chapter>`** 模式中的元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>链 **接的** Compute字符串由computeString属 **性显** 示。

在输入表单中，链接的编辑控件声明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

该图 **[!UICONTROL Magnifier]** 标允许您打开链接元素的编辑表单。

#### 链接集合 {#link-collection}

要填充链接集合，请向数 **据模式中链接元素的定义中** 添加unboind=&quot;true&quot;属性：

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

目标元素的内容丰富了每个集合元素：

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

在输入形式中，列表控件声明如下：

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

将显示默认列，以视图目 **标元素的** “计算”字符串。

### 外部表的链接 {#links-to-external-tables}

在数据模式中将声明指向外部表的链接，如下所示：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

链接的定义填充在链 **接类型****`<element>`**&#x200B;上 **，并且** 目标属性引用目标模式(本例中的“nms:收件人”)。

根据惯例，链接必须从数据模式的主要元素中声明。

计 **算字符串** 和目标元素的键可丰富主 **`<name>-id`** 要元素的 **`<name>-cs`** 属性和属性。

在我们的示例中，链接填充在“cus:book”模式中，链接数据的内容包含在“mainContact-id”和“mainContact-cs”属性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

链接编辑控件声明如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以通过在输入表单中的链接定义 **`<sysfilter>`** 添加元素来限制目标元素的选择：

```
<input xpath="mainContact">
  <!-- Filter the selection of the link on the Adobe domain -->
  <sysFilter>
    <condition expr="@domain =  'adobe.com '"/>
  </sysFilter>
</input>
```

>[!NOTE]
>
>此限制也适用于内容链接。

#### 链接集合 {#link-collection-1}

集合的定义与对集合元素的列表的定义相同：

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

在输入形式中，列表控件声明如下：

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>该列表是可编辑的，允许您从上面显示的“链接”类型控件中选择链接。

目标元素的内容丰富了输出文档中的每个集合元素：

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### 链接聚合 {#link-aggregation}

引用的每个链接的内容仅限于目标元素的 **内部键** 和计算字符串。

JavaScript脚本用于通过SOAP查询丰富链接的内容。

**示例**:将收件人名称添加到“mainContact”链接和“contact”集合链接：

```
// Update <mainContact> link
var mainContactId = content.@['mainContact-id']
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+mainContactId}/>
      </where>
    </queryDef>)

var recipient = query.ExecuteQuery()
content.mainContact.@lastName = recipient.@lastName

// Update <contact> link collection
for each(var contact in content.contact)
{
  var contactId = contact.@['recipient-id']
  var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+contactId}/>
      </where>
    </queryDef>
  )
  
  var recipient = query.ExecuteQuery()
  contact.@lastName = recipient.@lastName
}
```

脚本执行后获得的结果：

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

JavaScript代码的内容通过文件夹添加 **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** ，并且必须在每个转换的发布模板中填充。

![](assets/d_ncs_content_link5.png)

