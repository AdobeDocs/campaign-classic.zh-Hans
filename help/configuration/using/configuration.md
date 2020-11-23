---
solution: Campaign Classic
product: campaign
title: 配置
description: 配置
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 1%

---


# 配置{#configuration}

导航列表使用的文件夹类型在遵循xtk:navtree模式语法的XML文档 **中进行了描述** 。

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

XML文档包含根元 **`<navtree>`** 素，该元素具 **有** name和 **命名空间属性** ，用于指定文档名和命名空间。 名称和命名空间构成文档标识密钥。

应用程序的全局命令在元素的文档中声 **`<commands>`** 明。

在文档中，文件类型声明采用以下元素进行结构化： **`<model>`** 和 **`<nodemodel>`**。

## 全局命令 {#global-commands}

全局命令允许您启动操作。 此操作可以是输入表单或SOAP调用。

可从主菜单访问全局 **[!UICONTROL Tools]** 命令。

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
* **标签**:命令的标签。
* **desc**:描述可从主屏幕的状态栏中显示。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，&quot;cus:收件人&quot;)
* **rights**:列表已命名权限（以逗号分隔），允许访问此命令。 可从文件夹访问可用权限的 **[!UICONTROL Administration > Access management > Named rights]** 列表。
* **promptLabel**:在执行命令之前显示确认框。

元 **`<command>`** 素可以包 **`<command>`** 含子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令的显示顺序与在XML文档中声明的顺序相同。

命令分隔条允许您在命令之间显示分隔条。 它由命令标 **签中包含** 的&#39;-&#39;值标识。

标签及其输入 **`<soapcall>`** 参数的可选存在定义要执行的SOAP方法的调用。 有关SOAP API的详细信息，请参阅 [活动JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

表单上下文可以在从标记进行初始化时 **`<enter>`** 更新。 有关此标签的更多信息，请参阅输入表单的相关文档。

**示例**:

* 启动“xtk:import”表单的全局命令声明：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在命令标签中存在(&amp;I)，在“I”字 **符上** 声明键盘快捷键。

* 带分隔符的子菜单示例：

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

通过文件夹类型，您可以访问模式的数据。 与文件夹关联的视图由列表和输入表单组成。

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

必须在元素下输入文件夹类型 **`<model>`** 声明。 通过此元素，您可以定义从菜单中可见的分层 **[!UICONTROL Add new folder]** 组织。 元素 **`<model>`** 必须包含元 **`<nodemodel>`** 素和其他 **`<model>`** 元素。

名 **称****和标签属性填充元素的内部名称** ，以及菜单中显示的标 **[!UICONTROL Add new folder]** 签。

元 **`<nodemodel>`** 素包含文件夹类型的说明，其属性如下：

* **name**:内部名称
* **标签**:标签(在菜单 **[!UICONTROL Add new folder]** 中使用)和在插入文件夹时用作默认标签。
* **img**:文件夹插入时的默认图像。
* **hiddenCommands**:列表要遮罩的命令（以逗号分隔）。 可能的值：“插入”、“删除”、“更新”和“重复”。
* **newFolderShortCuts**:创建文件夹时模型&#x200B;**`<nodemodel>`** 的快捷键列表（以逗号分隔）。
* **插入右**、 **编辑右**、 **删除右**:用于插入、编辑和删除文件夹的权限。

元 **`<view>`** 素下的元 **`<nodemodel>`** 素包含与列表关联的视图的配置。 模式的列表在元素的 **模式** 属性中 **`<view>`** 输入。

要编辑列表的记录，将隐式使用与列表模式同名的输入表单。 元 **素上** 的type **`<view>`** 属性影响表单的显示。 可能的值有：

* **listdet**:在列表底部显示表单。
* **列表**:仅显示列表。 通过多次单击或通过选择列表菜单中的“打开”启动表单。
* **表单**:显示只读表单。
* **editForm**:在编辑模式下显示表单。

>[!NOTE]
>
>通过在元素中输入表单属性，可以重 **载输** 入表单的 **`<view>`** 名称。

列表列的默认配置通过元素进 **`<columns>`** 行。 在包含xpath属性的元 **`<node>`** 素上声明一 **列** ，其模式中要引用的字段作为其值。

**示例**:在“nms:收件人”模式中声明文件夹类型。

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

可从列表的菜 **[!UICONTROL Action]** 单或关联的菜单按钮访问命令。

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

命令的描述在元素中输入， **`<command>`** 并具有以下属性：

* **name**:命令的内部名称：名称必须输入且唯一。
* **标签**:命令的标签。
* **desc**:描述可从主屏幕的状态栏中显示。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，“cus:收件人”)。
* **rights**:列表已命名权限（以逗号分隔），允许访问此命令。 可从文件夹访问可用权限的 **[!UICONTROL Administration > Access management > Named rights]** 列表。
* **promptLabel**:在执行命令之前显示确认框
* **monoSelection**:强制单选（默认情况下为多选）。
* **refreshView**:执行命令后强制重装列表。
* **enabledIf**:根据输入的表达式激活命令。
* **img**:输入允许从列表工具栏访问命令的图像。

元 **`<command>`** 素可以包 **`<command>`** 含子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令的显示顺序与在XML文档中声明的顺序相同。

命令分隔条允许您在命令之间显示分隔条。 它由命令标 **签中包含** 的&#39;-&#39;值标识。

标签及其输入 **`<soapcall>`** 参数的可选存在定义要执行的SOAP方法的调用。 有关SOAP API的更多信息，请参阅 [活动JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

表单上下文可以通过标签在初始化时进 **`<enter>`** 行更新。 有关此标记的更多信息，请参阅输入表单文档。

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

文件夹管理操作有两种类型：

1. 文件夹是视图:该列表显示与该模式关联的所有记录，并且可能在文件夹属性中输入系统筛选。
1. 文件夹已链接：该列表中的记录会隐式筛选到文件夹链接。

对于链接的文件夹， **必须填** 充元素 **`<nodemodel>`** 上的folderLink属性。 此属性包含在数据模式中配置的文件夹上的链接名称。

数据模式中链接文件夹声明的示例：

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

名为“ **`<nodemodel>`** folder”的文件夹链接上的配置如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

