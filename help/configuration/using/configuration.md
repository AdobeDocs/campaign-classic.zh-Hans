---
title: 配置
seo-title: 配置
description: 配置
seo-description: null
page-status-flag: never-activated
uuid: 0f2aadc3-5199-476c-9956-6e39b899a7d0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: b781fd52-828c-4582-a546-a1fee7e5a26d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 配置{#configuration}

在遵循 **xtk:navtree架构的语法的XML文档中描述导航列表使用的文件夹类型** 。

XML文档的结构如下：

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

XML文档包含根元素，其 **`<navtree>`** 中具有名称 **和namespace** 属性 **** ，用于指定文档名和namespace。 名称和命名空间构成文档标识密钥。

应用程序的全局命令在文档中从元素声明 **`<commands>`** 出来。

在文档中，文件类型声明的结构包括以下元素： **`<model>`** 和 **`<nodemodel>`**。

## 全局命令 {#global-commands}

全局命令可让您启动一个操作。 此操作可以是输入表单或SOAP调用。

可从主菜单访问全局命 **[!UICONTROL Tools]** 令。

命令配置结构如下：

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

全局命令的描述在元素中输入， **`<command>`** 并包含以下属性：

* **name**:命令的内部名称：名称必须输入且唯一
* **label**:命令的标签。
* **desc**:描述从主屏幕的状态栏中可见。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，“cus:recipient”)
* **rights**:允许访问此命令的已命名权限列表（以逗号分隔）。 可从文件夹访问可用权限列 **[!UICONTROL Administration > Access management > Named rights]** 表。
* **promptLabel**:在执行命令之前显示一个确认框。

元 **`<command>`** 素可以包 **`<command>`** 含子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令的显示顺序与在XML文档中声明的顺序相同。

命令分隔符可让您在命令之间显示分隔条。 它由命令标 **签中包含的** &#39;-&#39;值标识。

标签及其输入参 **`<soapcall>`** 数的可选存在定义要执行的SOAP方法的调用。 有关SOAP API的详细信息，请参阅 [Campaign JSAPI文档](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。

在从标记初始化时，可以更新表单上 **`<enter>`** 下文。 有关此标记的详细信息，请参阅有关输入表单的文档。

**示例**:

* 声明全局命令以启动“xtk:import”表单：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在命令标签中存在(&amp;I)，在“I”字符上 **声明键** 盘快捷键。

* 带有分隔符的子菜单示例：

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* 执行SOAP方法：

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## 文件夹类型 {#folder-type}

通过文件夹类型，您可以访问架构的数据。 与文件夹关联的视图由列表和输入表单组成。

文件夹类型配置结构如下所示：

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

必须在元素下输入文件夹类型声 **`<model>`** 明。 通过此元素，您可以定义从菜单中可见的分层 **[!UICONTROL Add new folder]** 组织。 元素 **`<model>`** 必须包含元 **`<nodemodel>`** 素和其他 **`<model>`** 元素。

名 **称****和标签属性填充元素的内部名称和菜单中显示的****[!UICONTROL Add new folder]** 标签。

元 **`<nodemodel>`** 素包含文件夹类型的说明，其属性如下：

* **name**:内部名称
* **label**:标签(用在菜 **[!UICONTROL Add new folder]** 单中)和作为插入文件夹时的默认标签。
* **img**:文件夹插入时的默认图像。
* **hiddenCommands**:要遮罩的命令列表（以逗号分隔）。 可能的值：“insert”、“delete”、“update”和“duplicate”。
* **newFolderShortCuts**:创建文件夹时模型(**`<nodemodel>`** 以逗号分隔)的快捷键列表。
* **insertRight**, **editRight**, **deleteRight**:用于插入、编辑和删除文件夹的权限。

元 **`<view>`** 素下的元素 **`<nodemodel>`** 包含与视图关联的列表的配置。 列表的架构在元素的架构属 **性中输** 入 **`<view>`** 。

要编辑列表记录，将隐式使用与列表架构同名的输入表单。 元 **素上的** type属 **`<view>`** 性影响表单的显示。 可能的值包括：

* **listdet**:在列表底部显示表单。
* **列表**:仅显示列表。 通过双击或通过选择列表的菜单中的“打开”启动表单。
* **表单**:显示只读表单。
* **editForm**:以编辑模式显示表单。

>[!NOTE]
>
>通过在元素中输入表单属性，输入表单的名 **称可** 以过载 **`<view>`** 。

列表列的默认配置是通过元素进 **`<columns>`** 行的。 在包含 **`<node>`** xpath **** 属性的元素上声明一列，其中要在其架构中引用的字段作为其值。

**示例**:“nms:recipient”架构上的文件夹类型声明。

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

相应的文件夹插入菜单：

![](assets/d_ncs_integration_navigation_exemple2.png)

加载列表时，可以应用筛选和排序：

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### 快捷键命令 {#shortcut-commands}

快捷键命令允许您在选择列表时启动操作。 操作可以是输入表单或SOAP调用。

可从列表菜单 **[!UICONTROL Action]** 或关联的菜单按钮访问命令。

命令配置结构如下：

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

在元素中输入命令的说明， **`<command>`** 并包含以下属性：

* **name**:命令的内部名称：名称必须输入且唯一。
* **label**:命令的标签。
* **desc**:描述从主屏幕的状态栏中可见。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，“cus:recipient”)。
* **rights**:允许访问此命令的已命名权限列表（以逗号分隔）。 可从文件夹访问可用权限列 **[!UICONTROL Administration > Access management > Named rights]** 表。
* **promptLabel**:在执行命令之前显示确认框
* **monoSelection**:强制进行单选（默认情况下为多选）。
* **refreshView**:强制在执行命令后重新加载列表。
* **enabledIf**:根据输入的表达式激活命令。
* **img**:输入允许从列表工具栏访问命令的图像。

元 **`<command>`** 素可以包 **`<command>`** 含子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令的显示顺序与在XML文档中声明的顺序相同。

命令分隔符可让您在命令之间显示分隔条。 它由命令标 **签中包含的** &#39;-&#39;值标识。

标签及其输入参 **`<soapcall>`** 数的可选存在定义要执行的SOAP方法的调用。 有关SOAP API的详细信息，请参阅 [Campaign JSAPI文档](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。

表单上下文可以通过标签在初始化时进行 **`<enter>`** 更新。 有关此标记的详细信息，请参阅输入表单文档。

**示例**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### 链接的文件夹 {#linked-folder}

有两种类型的文件夹管理操作：

1. 文件夹是一个视图：该列表显示与架构关联的所有记录，并且可能在文件夹属性中输入系统筛选。
1. 文件夹已链接：列表中的记录会隐式过滤到文件夹链接上。

对于链接的文件夹，必 **须填充元素****`<nodemodel>`** 上的folderLink属性。 此属性包含在数据架构中配置的文件夹上的链接名称。

数据架构中链接文件夹声明的示例：

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

在名为“ **`<nodemodel>`** folder”的文件夹链接上的配置如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

