---
product: campaign
title: 实施 SOAP 方法
description: 实施 SOAP 方法
audience: configuration
content-type: reference
topic-tags: api
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# 实施 SOAP 方法{#implementing-soap-methods}

![](../../assets/v7-only.svg)

## 简介 {#introduction}

可以在JavaScript中创建SOAP方法。 该函数仅支持应用进程，避免了JSP的开发及其在表单中的调用。

这些SOAP方法的行为方式与应用程序中本地定义的方法相同。 支持相同的属性：静态、仅键和常量。

## 定义方法库 {#defining-a-method-library}

创建方法库涉及两个阶段：

* SOAP方法声明，
* JavaScript中的定义（或实施）。

### 声明 {#declaration}

首先，声明架构中的方法（有关如何创建和编辑架构的更多信息，请参阅[此部分](../../configuration/using/about-schema-edition.md)）。

其声明与本机方法的声明类似，不同之处在于，您需要添加“library”属性，以指定定义所在的方法库的名称。

此名称与“JavaScript代码”类型实体的名称（以及命名空间）一致。

示例:

testLog(msg)方法在nms:recipient扩展中声明

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>命名空间和用于库的名称与找到声明的命名空间和架构名称无关。

### 定义 {#definition}

SOAP方法以JavaScript函数的形式实现，这些函数分组到代表库的脚本中。

>[!NOTE]
>
>方法库可以对各种模式的函数进行分组，反之亦然，一个模式的函数可以在单独的库中定义。

脚本可以包含要在初始库加载期间执行的代码。

**1. 名称**

函数的名称必须符合以下格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

示例:

以下JavaScript函数是上述方法的实现。 应在“JavaScript代码”类型实体中使用“cus:test”名称定义该代码。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2.签名**

函数的签名必须包含声明中每个“in”或“inout”参数的参数。

具体案例：

* **非静态方法**:函数必须先包含一个附加参数，该参数与以“xml”(E4X)类型对象形式传递的XML实体一致。
* **“仅限键”类型方法**:函数必须先包含一个附加参数，该参数与以字符串形式传递的键值一致。

**3.返回的值**

函数必须为每个“out”或“inout”类型参数返回一个值。 具体案例：如果在声明方法时没有任何“static”、“key only”或“const”属性，则第一个返回的值必须与修改后的实体一致。 可以返回新对象或返回第一个修改的参数。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

当要返回多个值时，必须在表中显示它们。

示例:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
