---
solution: Campaign Classic
product: campaign
title: 配置
description: 配置
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 1%

---

# 配置活动 Explorer导航树{#configuration}

作为专家用户，您可以在资源管理器树中添加文件夹并对其进行自定义。

在本节](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)中，进一步了解活动资源管理器和导航层次结构[。

导航列表使用的文件夹类型在遵循&#x200B;**xtk:navtree**&#x200B;模式语法的XML文档中进行描述。

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

XML文档包含具有&#x200B;**name**&#x200B;和&#x200B;**命名空间**&#x200B;属性的&#x200B;**`<navtree>`**&#x200B;根元素，用于指定文档名和命名空间。 名称和命名空间构成文档标识键。

应用程序的全局命令在文档中从&#x200B;**`<commands>`**&#x200B;元素声明。

在文档中，文件类型声明采用以下元素构建：**`<model>`**&#x200B;和&#x200B;**`<nodemodel>`**。

## 全局命令{#global-commands}

全局命令允许您启动操作。 此操作可以是输入表单或SOAP调用。

可从主&#x200B;**[!UICONTROL Tools]**&#x200B;菜单访问全局命令。

命令配置结构如下所示：

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

全局命令的描述输入在&#x200B;**`<command>`**&#x200B;元素中，并具有以下属性：

* **name**:命令的内部名称：名称必须输入且唯一
* **label**:命令的标签。
* **desc**:说明可从主屏幕的状态栏中显示。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，&quot;cus:收件人&quot;)
* **rights**:列表已命名权限（以逗号分隔），允许访问此命令。可从&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;文件夹访问可用权限的列表。
* **promptLabel**:在执行命令之前显示确认框。

**`<command>`**&#x200B;元素可包含&#x200B;**`<command>`**&#x200B;子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令的显示顺序与在XML文档中声明的顺序相同。

使用命令分隔符可以在命令之间显示分隔条。 它由命令标签中包含的&#x200B;**&#39;-&#39;**&#x200B;值标识。

**`<soapcall>`**&#x200B;标记及其输入参数的可选存在定义要执行的SOAP方法的调用。 有关SOAP API的详细信息，请参阅[活动 JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

在从&#x200B;**`<enter>`**&#x200B;标记进行初始化时，可以更新表单上下文。 有关此标签的更多信息，请参阅有关输入表单的文档。

**示例**:

* 启动“xtk:import”表单的全局命令声明：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在命令标签中存在&#x200B;**&amp;**，在“I”字符上声明键盘快捷键。

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

## 文件夹类型{#folder-type}

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

必须在&#x200B;**`<model>`**&#x200B;元素下输入文件夹类型声明。 此元素允许您定义从&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜单中可见的分层组织。 **`<model>`**&#x200B;元素必须包含&#x200B;**`<nodemodel>`**&#x200B;元素和其他&#x200B;**`<model>`**&#x200B;元素。

**name**&#x200B;和&#x200B;**label**&#x200B;属性填充元素的内部名称和显示在&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜单中的标签。

**`<nodemodel>`**&#x200B;元素包含文件夹类型的说明，其属性如下：

* **name**:内部名称
* **label**:标签(在菜 **[!UICONTROL Add new folder]** 单中使用)和作为插入文件夹时的默认标签。
* **img**:文件夹插入时的默认图像。
* **hiddenCommands**:列表要遮罩的命令（以逗号分隔）。可能的值：“adbnew”、“adbsave”、“adbcancel”和“adbdup”。
* **newFolderShortCuts**:列表创建文件夹时&#x200B;**`<nodemodel>`** 模型上的快捷键（用逗号分隔）。
* **insertRight**、 **editRight**、 **deleteRight**:插入、编辑和删除文件夹的权限。

**`<nodemodel>`**&#x200B;元素下的&#x200B;**`<view>`**&#x200B;元素包含与列表关联的视图的配置。 列表的模式输入到&#x200B;**`<view>`**&#x200B;元素的&#x200B;**模式**&#x200B;属性中。

要编辑列表的记录，将隐式使用与列表模式同名的输入表单。 **`<view>`**&#x200B;元素上的&#x200B;**type**&#x200B;属性影响表单的显示。 可能的值有：

* **listdet**:在列表底部显示表单。
* **列表**:仅显示列表。通过按住多次单击或通过选择列表的菜单中的“打开”启动表单。
* **表单**:显示只读表单。
* **editForm**:以编辑模式显示表单。

>[!NOTE]
>
>通过在&#x200B;**`<view>`**&#x200B;元素中输入&#x200B;**form**&#x200B;属性，可以重载输入表单的名称。

通过&#x200B;**`<columns>`**&#x200B;元素输入列表列的默认配置。 在&#x200B;**`<node>`**&#x200B;元素上声明一列，该元素包含&#x200B;**xpath**&#x200B;属性，且该字段在其模式中被引用为其值。

**示例**:在“nms:收件人”模式上声明文件夹类型。

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

加载列表时，可以应用过滤和排序：

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

### 快捷键命令{#shortcut-commands}

快捷命令可让您在选择列表时启动操作。 操作可以是输入表单或SOAP调用。

可从列表的&#x200B;**[!UICONTROL Action]**&#x200B;菜单或相关菜单按钮访问命令。

命令配置结构如下所示：

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

在&#x200B;**`<command>`**&#x200B;元素上输入命令的说明，其属性如下：

* **name**:命令的内部名称：名称必须输入且唯一。
* **label**:命令的标签。
* **desc**:说明可从主屏幕的状态栏中显示。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，“cus:收件人”)。
* **rights**:列表已命名权限（以逗号分隔），允许访问此命令。可从&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;文件夹访问可用权限的列表。
* **promptLabel**:在执行命令之前显示确认框
* **monoSelection**:强制单选（默认情况下为多选）。
* **refreshView**:执行命令后强制重装列表。
* **enabledIf**:根据输入的表达式激活命令。
* **img**:输入允许从“列表”工具栏访问命令的图像。

**`<command>`**&#x200B;元素可包含&#x200B;**`<command>`**&#x200B;子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令的显示顺序与在XML文档中声明的顺序相同。

使用命令分隔符可以在命令之间显示分隔条。 它由命令标签中包含的&#x200B;**&#39;-&#39;**&#x200B;值标识。

**`<soapcall>`**&#x200B;标记及其输入参数的可选存在定义要执行的SOAP方法的调用。 有关SOAP API的更多信息，请参阅[活动 JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

可以通过&#x200B;**`<enter>`**&#x200B;标记在初始化时更新表单上下文。 有关此标签的更多信息，请参阅输入表单文档。

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

### 链接文件夹{#linked-folder}

有两种类型的文件夹管理操作：

1. 该文件夹是视图:该列表显示与该模式关联的所有记录，并且可能在文件夹属性中输入系统筛选。
1. 文件夹已链接：该列表中的记录会在文件夹链接上隐式过滤。

对于链接的文件夹，必须填充&#x200B;**`<nodemodel>`**&#x200B;元素上的&#x200B;**folderLink**&#x200B;属性。 此属性包含在数据模式中配置的文件夹上的链接名称。

数据模式中链接文件夹声明的示例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

在名为“folder”的文件夹链接上的&#x200B;**`<nodemodel>`**&#x200B;配置如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
