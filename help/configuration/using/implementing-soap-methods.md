---
product: campaign
title: 实施 SOAP 方法
description: 实施 SOAP 方法
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# 实施SOAP方法{#implementing-soap-methods}



## 简介 {#introduction}

可以在JavaScript中创建SOAP方法。 该功能简单实现了应用过程，避免了JSP的开发以及它们在表单中的调用。

这些SOAP方法的行为方式与应用程序中本机定义的方法相同。 支持相同的属性：静态、仅键和常量。

## 定义方法库 {#defining-a-method-library}

创建方法库涉及两个阶段：

* SOAP方法声明，
* JavaScript中的定义（或实现）。

### 声明 {#declaration}

首先声明架构中的方法(有关如何创建和编辑架构的更多信息，请参阅 [本节](../../configuration/using/about-schema-edition.md))。

它们的声明与本机方法的声明类似，不同之处在于，您需要添加“library”属性，指定定义所在的方法库的名称。

此名称与“JavaScript代码”类型实体的名称（以及命名空间）一致。

示例:

testLog(msg)方法在nms：recipient扩展中声明

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>用于库的命名空间和名称与发现声明的命名空间和架构名称无关。

### 条件 {#definition}

SOAP方法以分组在表示库的脚本中的JavaScript函数的形式实现。

>[!NOTE]
>
>方法库可以为各种架构对函数进行分组，反之亦然，一个架构的函数可以在单独的库中定义。

脚本可以包含在初始库加载期间要执行的代码。

**1. 名称**

函数的名称必须符合以下格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

示例:

以下JavaScript函数是上述方法的实现。 应使用&quot;cus：test&quot;名称在&quot;JavaScript Code&quot;类型实体中定义它。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 签名**

函数的签名必须为声明的每个“in”或“inout”参数包含一个参数。

具体案例：

* **非静态方法**：函数必须首先包含一个额外的参数，与以“xml”(E4X)类型对象的形式传递的XML实体相一致。
* **&quot;only&quot; type methods**：函数必须首先包含一个附加参数，该参数必须与以字符串形式传递的键值相一致。

**3. 返回的值**

该函数必须为每个“out”或“inout”类型参数返回一个值。 特定案例：如果在声明方法时未使用任何“static”、“key only”或“const”属性，则第一个返回值必须与修改的实体一致。 可以返回新对象或返回第一个修改后的参数。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

要返回多个值时，必须在表中显示它们。

示例:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
