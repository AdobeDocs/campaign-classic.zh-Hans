---
product: campaign
title: 配置Campaign Explorer导航树
description: 了解如何配置Campaign Explorer导航树
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 1%

---

# 配置Campaign Explorer导航树{#configuration}

作为专家用户，您可以在资源管理器树中添加文件夹并对其进行自定义。

进一步了解Campaign资源管理器和导航层次结构 [在此部分中](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

导航列表使用的文件夹类型在遵循 **xtk:navtree** 架构。

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

XML文档包含 **`<navtree>`** 根元素，其中 **name** 和 **命名空间** 属性来指定文档名称和命名空间。 名称和命名空间构成了文档标识键。

应用程序的全局命令在文档中声明自 **`<commands>`** 元素。

在文档中，文件类型声明的结构具有以下元素： **`<model>`** 和 **`<nodemodel>`**.

## 全局命令 {#global-commands}

全局命令允许您启动操作。 此操作可以是输入表单或SOAP调用。

全局命令可从主 **[!UICONTROL Tools]** 菜单。

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

全局命令的说明将在 **`<command>`** 元素，其属性如下：

* **name**:命令的内部名称：必须输入名称且名称唯一
* **标签**:命令的标签。
* **desc**:描述从主屏幕的状态栏中可见。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，&quot;cus:recipient&quot;)
* **权利**:允许访问此命令的命名权限列表（以逗号分隔）。 可从 **[!UICONTROL Administration > Access management > Named rights]** 文件夹。
* **promptLabel**:在执行命令之前显示确认框。

A **`<command>`** 元素可包含 **`<command>`** 子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令以与在XML文档中声明的顺序相同的顺序显示。

使用命令分隔符可显示命令之间的分隔条。 它由 **&#39;-&#39;** 命令标签中包含的值。

可选存在 **`<soapcall>`** 标记及其输入参数定义要执行的SOAP方法的调用。 有关SOAP API的详细信息，请参阅 [Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans).

表单上下文可在从 **`<enter>`** 标记。 有关此标记的更多信息，请参阅有关输入表单的文档。

**示例**:

* 声明全局命令以启动“xtk:import”表单：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在“I”字符上，如果存在 **&amp;** 在命令标签中。

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

利用文件夹类型，可访问架构的数据。 与文件夹关联的视图由列表和输入表单组成。

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

必须在 **`<model>`** 元素。 利用此元素，可定义从 **[!UICONTROL Add new folder]** 菜单。 A **`<model>`** 元素必须包含 **`<nodemodel>`** 元素和其他 **`<model>`** 元素。

的 **name** 和 **标签** 属性填充元素的内部名称和 **[!UICONTROL Add new folder]** 菜单。

的 **`<nodemodel>`** 元素包含文件夹类型的描述，其属性如下：

* **name**:内部名称
* **标签**:在 **[!UICONTROL Add new folder]** ，作为默认标签。
* **img**:文件夹插入时的默认图像。
* **hiddenCommands**:要屏蔽的命令列表（以逗号分隔）。 可能值：&quot;adbnew&quot;、&quot;adbsave&quot;、&quot;adbcancel&quot;和&quot;adbdup&quot;。
* **newFolderShortCuts**:模型上的快捷方式列表(**`<nodemodel>`** 用逗号分隔)。
* **insertRight**, **editRight**, **deleteRight**:用于插入、编辑和删除文件夹的权限。

的 **`<view>`** 元素 **`<nodemodel>`** 元素包含与视图关联的列表的配置。 列表的架构在 **模式** 属性 **`<view>`** 元素。

要编辑列表的记录，将隐式使用与列表架构同名的输入表单。 的 **type** 属性 **`<view>`** 元素会影响表单的显示。 可能的值包括：

* **listdet**:在列表底部显示表单。
* **列表**:仅显示列表。 通过双击或通过选择列表的菜单中的“打开”启动表单。
* **表单**:显示只读表单。
* **editForm**:在编辑模式下显示表单。

>[!NOTE]
>
>通过输入 **表单** 属性 **`<view>`** 元素。

列表列的默认配置通过 **`<columns>`** 元素。 列在 **`<node>`** 包含 **xpath** 属性，其中要在其架构中引用的字段作为其值。

**示例**:“nms:recipient”模式上文件夹类型的声明。

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

在加载列表时，可以应用过滤和排序：

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

快捷键命令允许您在选择列表时启动一项操作。 操作可以是输入表单或SOAP调用。

可从 **[!UICONTROL Action]** 菜单或关联的菜单按钮。

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

在 **`<command>`** 元素，其属性如下：

* **name**:命令的内部名称：必须输入名称且名称唯一。
* **标签**:命令的标签。
* **desc**:描述从主屏幕的状态栏中可见。
* **表单**:要启动的表单：要输入的值是输入表单的标识键(例如，&quot;cus:recipient&quot;)。
* **权利**:允许访问此命令的命名权限列表（以逗号分隔）。 可从 **[!UICONTROL Administration > Access management > Named rights]** 文件夹。
* **promptLabel**:在执行命令之前显示确认框
* **monoSelection**:强制单选（默认情况下为多选）。
* **refreshView**:执行命令后强制重新加载列表。
* **enabledIf**:根据输入的表达式激活命令。
* **img**:输入允许从列表工具栏访问命令的图像。

A **`<command>`** 元素可包含 **`<command>`** 子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

命令以与在XML文档中声明的顺序相同的顺序显示。

使用命令分隔符可显示命令之间的分隔条。 它由 **&#39;-&#39;** 命令标签中包含的值。

可选存在 **`<soapcall>`** 标记及其输入参数定义要执行的SOAP方法的调用。 有关SOAP API的更多信息，请参阅 [Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans).

可以通过 **`<enter>`** 标记。 有关此标记的更多信息，请参阅输入表单文档。

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

1. 文件夹是一个视图：该列表显示与架构关联的所有记录，并可能在文件夹属性中输入系统筛选。
1. 文件夹已链接：列表中的记录会在文件夹链接上隐式过滤。

对于链接的文件夹， **folderLink** 属性 **`<nodemodel>`** 必须填充元素。 此属性包含在数据架构中配置的文件夹中的链接名称。

数据架构中链接文件夹的声明示例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

的配置 **`<nodemodel>`** 在名为“folder”的文件夹的链接上，如下所示：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
