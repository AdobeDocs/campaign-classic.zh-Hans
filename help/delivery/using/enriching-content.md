---
product: campaign
title: 丰富内容
description: 丰富内容
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: a4472a7c-a16b-4d10-a8ca-f74ca5f62de4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# 丰富内容{#enriching-content}

![](../../assets/common.svg)

聚合器允许您使用外部数据扩充内容。 此数据来自通用查询或链接的表。

## 一般查询 {#generic-queries}

通过&#x200B;**[!UICONTROL Aggregator]**&#x200B;选项卡中的发布模板配置查询。

检索到的数据将通过其主元素扩充XML输出文档。

从收件人模式查询返回的示例(**nms:recipient**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

**`<collection-recipient>`**&#x200B;元素表示由查询生成的文档的输入元素。 检索到的数据将在此元素下返回；在本例中，为收件人列表。

### 添加查询 {#adding-a-query}

可使用向导编辑查询参数。

1. 在第一页中，指定标签和包含要检索数据的架构。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >编辑字段&#x200B;**Path**&#x200B;用于重命名查询输出元素。

1. 下一页允许您选择要检索的数据。

   ![](assets/d_ncs_content_query2.png)

1. 下一页定义过滤条件。

   ![](assets/d_ncs_content_query3.png)

1. 最后一页将启动查询返回的数据预览。

   ![](assets/d_ncs_content_query4.png)

## 链接的表 {#linked-tables}

利用链接，可检索链接到内容的外部数据。

链接数据有两种类型：

* 内容链接：这是本机内容管理模式。 链接的内容会自动集成到XML输出文档中。
* 指向外部表的链接允许访问数据库中的所有其他表，但约束是使用聚合器检索所选链接的数据。

### 链接到内容架构 {#link-to-a-content-schema}

在数据架构中声明内容链接，如下所示：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

链接的定义填充在&#x200B;**string**-type **`<element>`**&#x200B;上，并且&#x200B;**expandSchemaTarget**&#x200B;属性引用目标架构（在我们的示例中为“cus:chapter”）。 引用的架构必须是内容架构。

目标元素的内容丰富了链接元素，即我们示例架构中的&#x200B;**`<chapter>`**&#x200B;元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>链接的&#x200B;**计算字符串**&#x200B;是从&#x200B;**computeString**&#x200B;属性中显示的。

在输入表单中，链接的编辑控件声明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

使用&#x200B;**[!UICONTROL Magnifier]**&#x200B;图标可打开链接元素的编辑表单。

#### 链接集合 {#link-collection}

要填充链接集合，请将&#x200B;**unbound=&quot;true&quot;**&#x200B;属性添加到数据架构中链接元素的定义中：

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

目标元素的内容丰富了每个收集元素：

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

在输入表单中，列表控件声明如下：

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

显示默认列，以查看目标元素的&#x200B;**计算字符串**。

### 指向外部表的链接 {#links-to-external-tables}

在数据架构中声明指向外部表的链接，如下所示：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

链接的定义填充在&#x200B;**link**-type **`<element>`**&#x200B;上，并且&#x200B;**target**&#x200B;属性引用目标模式（在我们的示例中为“nms:recipient”）。

按照惯例，必须从数据架构的主要元素中声明链接。

**计算字符串**&#x200B;和目标元素的键将丰富主元素上的&#x200B;**`<name>-id`**&#x200B;和&#x200B;**`<name>-cs`**&#x200B;属性。

在我们的示例中，链接以“cus:book”模式填充，链接数据的内容包含在“mainContact-id”和“mainContact-cs”属性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

链接编辑控件声明如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以通过输入表单中的链接定义添加&#x200B;**`<sysfilter>`**&#x200B;元素，从而限制目标元素的选择：

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

集合的定义与集合元素上列表的定义相同：

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

在输入表单中，列表控件声明如下：

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>该列表是可编辑的，允许您从上面显示的“链接”类型控件中选择链接。

目标元素的内容丰富了输出文档中的每个收集元素：

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### 链接聚合 {#link-aggregation}

引用的每个链接的内容仅限于目标元素的内部键和&#x200B;**计算字符串**。

JavaScript脚本用于通过SOAP查询扩充链接的内容。

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

执行脚本后获得的结果：

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

JavaScript代码的内容通过&#x200B;**[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]**&#x200B;文件夹添加，并且必须在每个转换的发布模板中填充。

![](assets/d_ncs_content_link5.png)
