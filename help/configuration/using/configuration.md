---
product: campaign
title: 配置Campaign Explorer导航树
feature: Application Settings
description: 了解如何配置Campaign Explorer导航树
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 0%

---

# 配置Campaign Explorer导航树{#configuration}

作为专家级用户，您可以在资源管理器树中添加文件夹并对其进行自定义。

请参阅[Adobe Campaign v8 （控制台）文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}以了解有关Campaign用户界面的更多信息。

导航列表使用的文件夹类型在遵循&#x200B;**xtk:navtree**&#x200B;架构语法的XML文档中进行了说明。

XML文档的结构如下所示：

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

XML文档包含具有&#x200B;**`<navtree>`**&#x200B;名称&#x200B;**和**&#x200B;命名空间&#x200B;**属性的**&#x200B;根元素，用于指定文档名称和命名空间。 名称和命名空间构成了文档标识键。

应用程序的全局命令在文档中的&#x200B;**`<commands>`**&#x200B;元素中声明。

文件类型声明在文档中具有以下元素： **`<model>`**&#x200B;和&#x200B;**`<nodemodel>`**。

## 全局命令 {#global-commands}

使用全局命令可启动操作。 此操作可以是输入表单或SOAP调用。

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

全局命令的描述输入到具有以下属性的&#x200B;**`<command>`**&#x200B;元素中：

* **name**：命令的内部名称：该名称必须输入且唯一
* **标签**：命令的标签。
* **desc**：从主屏幕的状态栏中显示的描述。
* **表单**：要启动的表单：要输入的值是输入表单的标识键（如“cus:recipient”）
* **权限**：允许访问此命令的已命名权限列表（以逗号分隔）。 可从&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;文件夹访问可用权限列表。
* **promptLabel**：在执行命令之前显示确认框。

**`<command>`**&#x200B;元素可以包含&#x200B;**`<command>`**&#x200B;个子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

这些命令的显示顺序与它们在XML文档中声明的顺序相同。

命令分隔符允许您在命令之间显示分隔条。 它由命令标签中包含的&#x200B;**&#39;-&#39;**&#x200B;值标识。

**`<soapcall>`**&#x200B;标记及其输入参数的可选存在性定义了要执行的SOAP方法的调用。 有关SOAP API的更多信息，请参阅[Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)。

初始化时可以从&#x200B;**`<enter>`**&#x200B;标记更新表单上下文。 有关此标记的详细信息，请参阅有关输入表单的文档。

**示例**：

* 用于启动“xtk:import”表单的全局命令的声明：

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  由于命令标签中存在&#x200B;**&amp;**，因此在“I”字符上声明了键盘快捷键。

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

通过文件夹类型，可授予对架构数据的访问权限。 与文件夹关联的视图由列表和输入表单组成。

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

必须在&#x200B;**`<model>`**&#x200B;元素下输入文件夹类型声明。 此元素允许您定义从&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜单可见的分层组织。 **`<model>`**&#x200B;元素必须包含&#x200B;**`<nodemodel>`**&#x200B;个元素和其他&#x200B;**`<model>`**&#x200B;个元素。

**name**&#x200B;和&#x200B;**label**&#x200B;属性填充&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜单中显示的元素和标签的内部名称。

**`<nodemodel>`**&#x200B;元素包含具有以下属性的文件夹类型描述：

* **名称**：内部名称
* **label**： **[!UICONTROL Add new folder]**&#x200B;菜单中使用的标签，在插入文件夹时用作默认标签。
* **img**：文件夹插入中的默认图像。
* **hiddenCommands**：要遮罩的命令列表（以逗号分隔）。 可能的值： “adbnew”、“adbsave”、“adbcancel”和“adbdup”。
* **newFolderShortCuts**：文件夹创建中的模型快捷方式列表（**`<nodemodel>`**，用逗号分隔）。
* **insertRight**，**editRight**，**deleteRight**：插入、编辑和删除文件夹的权限。

**`<view>`**&#x200B;元素下的&#x200B;**`<nodemodel>`**&#x200B;元素包含与视图关联的列表的配置。 在&#x200B;**元素的**&#x200B;架构&#x200B;**`<view>`**&#x200B;属性中输入了列表的架构。

要编辑列表的记录，隐式使用与列表架构同名的输入表单。 **元素上的** type **`<view>`**&#x200B;属性影响表单的显示。 可能的值包括：

* **listdet**：在列表底部显示表单。
* **列表**：单独显示列表。 通过双击或通过选择列表时的菜单中的“打开”来启动表单。
* **表单**：显示只读表单。
* **editForm**：在编辑模式下显示表单。

>[!NOTE]
>
>通过在&#x200B;**元素中输入** form **`<view>`**&#x200B;属性，可以重载输入表单的名称。

列表列的默认配置通过&#x200B;**`<columns>`**&#x200B;元素输入。 在包含&#x200B;**`<node>`** xpath **属性的**&#x200B;元素上声明了列，该属性的架构中要引用的字段作为其值。

**示例**：“nms:recipient”架构上文件夹类型的声明。

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

在加载列表时可以应用筛选和排序：

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

### 快捷命令 {#shortcut-commands}

使用快捷方式命令可在选择列表时启动操作。 该操作可以是输入表单或SOAP调用。

可从列表的&#x200B;**[!UICONTROL Action]**&#x200B;菜单或关联的菜单按钮访问命令。

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

在具有以下属性的&#x200B;**`<command>`**&#x200B;元素上输入了命令的描述：

* **name**：命令的内部名称：该名称必须输入且唯一。
* **标签**：命令的标签。
* **desc**：从主屏幕的状态栏中显示的描述。
* **表单**：要启动的表单：要输入的值是输入表单的标识键（例如“cus:recipient”）。
* **权限**：允许访问此命令的已命名权限列表（以逗号分隔）。 可从&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;文件夹访问可用权限列表。
* **promptLabel**：在执行命令之前显示确认框
* **monoSelection**：强制进行单选（默认为多选）。
* **refreshView**：执行命令后强制重新加载列表。
* **enabledIf**：根据输入的表达式激活该命令。
* **img**：输入允许从列表工具栏访问命令的图像。

**`<command>`**&#x200B;元素可以包含&#x200B;**`<command>`**&#x200B;个子元素。 在这种情况下，父元素允许您显示由这些子元素组成的子菜单。

这些命令的显示顺序与它们在XML文档中声明的顺序相同。

命令分隔符允许您在命令之间显示分隔条。 它由命令标签中包含的&#x200B;**&#39;-&#39;**&#x200B;值标识。

**`<soapcall>`**&#x200B;标记及其输入参数的可选存在性定义了要执行的SOAP方法的调用。 有关SOAP API的更多信息，请参阅[Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)。

初始化时可以通过&#x200B;**`<enter>`**&#x200B;标记更新表单上下文。 有关此标记的详细信息，请参阅输入表单文档。

**示例**：

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

1. 此文件夹是一个视图：列表显示与架构关联的所有记录，并可能在文件夹属性中输入系统筛选。
1. 已链接文件夹：列表中的记录已在文件夹链接上隐式筛选。

对于链接的文件夹，必须填充&#x200B;**元素上的** folderLink **`<nodemodel>`**&#x200B;属性。 此属性包含在数据架构中配置的文件夹上链接的名称。

数据架构中链接文件夹的声明示例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

名为“folder”的文件夹的链接上&#x200B;**`<nodemodel>`**&#x200B;的配置如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
