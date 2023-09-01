---
product: campaign
title: 丰富内容
description: 丰富内容
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Data Management
role: User, Developer, Data Engineer
exl-id: a4472a7c-a16b-4d10-a8ca-f74ca5f62de4
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 1%

---

# 丰富内容{#enriching-content}

通过汇总，您可以使用外部数据扩充内容。 此数据来自通用查询或链接表。

## 常规查询 {#generic-queries}

可通过中的发布模板配置查询 **[!UICONTROL Aggregator]** 选项卡。

检索的数据将通过其主元素扩充XML输出文档。

从查询返回收件人模式的示例(**nms：recipient**)：

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

此 **`<collection-recipient>`** 元素表示从查询生成的文档的输入元素。 检索的数据将在此元素下返回；在我们的示例中，是收件人列表。

### 添加查询 {#adding-a-query}

使用向导编辑查询参数。

1. 在第一页中，指定标签和包含要检索的数据的架构。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >编辑字段 **路径** 用于重命名查询输出元素。

1. 下一页允许您选择要检索的数据。

   ![](assets/d_ncs_content_query2.png)

1. 下一页定义筛选条件。

   ![](assets/d_ncs_content_query3.png)

1. 最后一页启动查询返回的数据的预览。

   ![](assets/d_ncs_content_query4.png)

## 链接表 {#linked-tables}

利用链接，可检索链接到内容的外部数据。

链接数据有两种类型：

* 内容链接：这是本机内容管理模式。 链接的内容会自动集成到XML输出文档中。
* 指向外部表的链接允许访问数据库中的所有其他表，但限制使用聚合器检索所选链接的数据。

### 链接到内容架构 {#link-to-a-content-schema}

内容链接在数据架构中声明，如下所示：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

链接的定义填充在 **字符串**-type **`<element>`**，和 **expandschematarget** 属性引用目标架构（在我们的示例中为“cus：chapter”）。 引用的架构必须是内容架构。

目标元素的内容丰富了链接元素，即 **`<chapter>`** 元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>此 **计算字符串** 的链接，可从 **计算字符串** 属性。

在输入表单中，链接的编辑控件声明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

此 **[!UICONTROL Magnifier]** 图标可让您打开链接元素的编辑表单。

#### 链接收藏集 {#link-collection}

要填充链接集合，请添加 **unbound=&quot;true&quot;** 数据架构中链接元素定义的属性：

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

目标要素的内容丰富了每个收集要素：

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

将显示默认列以查看 **计算字符串** 目标元素的ID。

### 外部表的链接 {#links-to-external-tables}

指向外部表的链接在数据模式中声明，如下所示：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

链接的定义填充在 **链接**-type **`<element>`**，和 **目标** 属性引用目标架构（在我们的示例中为“nms：recipient”）。

按照惯例，必须从数据架构的主元素声明链接。

此 **计算字符串** 而目标元素的键会丰富 **`<name>-id`** 和 **`<name>-cs`** 属性。

在我们的示例中，链接填充在“cus：book”模式中，链接数据的内容包含在“mainContact-id”和“mainContact-cs”属性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

链接编辑控件的声明如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以通过添加 **`<sysfilter>`** 元素（通过输入表单中的链接定义）：

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

#### 链接收藏集 {#link-collection-1}

收藏集的定义与收藏集元素上列表的定义相同：

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
>此列表可编辑，允许您从上面显示的“链接”类型控件中选择链接。

目标要素的内容丰富了输出文档中的每个收集要素：

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### 链路聚合 {#link-aggregation}

每个引用链接的内容仅限于内部键和 **计算字符串** 目标元素的ID。

JavaScript脚本用于通过SOAP查询扩充链接的内容。

**示例**：将收件人姓名添加到“mainContact”链接和“contact”收藏集链接：

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

JavaScript代码的内容是通过 **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** 文件夹，并且必须在每个转换的发布模板中填充。

![](assets/d_ncs_content_link5.png)
