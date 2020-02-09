---
title: 实现SOAP方法
seo-title: 实现SOAP方法
description: 实现SOAP方法
seo-description: null
page-status-flag: never-activated
uuid: c9366f4e-460d-4087-88f7-9cc6d0de597a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 76984d9d-7759-4e0f-a275-09cca27589fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 实现SOAP方法{#implementing-soap-methods}

## 简介 {#introduction}

可以在JavaScript中创建SOAP方法。 该函数只是使应用程序进程能够进行，避免了在表单中开发JSP及其调用。

这些SOAP方法的行为方式与应用程序中本机定义的方法相同。 支持相同的属性：static，仅限键和const。

## 定义方法库 {#defining-a-method-library}

创建方法库涉及两个阶段：

* SOAP方法声明，
* JavaScript中的定义（或实现）。

### 声明 {#declaration}

首先在架构中声明这些方法(有关如何创建和编辑架构的详细信息，请参阅 [本节](../../configuration/using/about-schema-edition.md))。

它们的声明与本机方法的声明类似，只是您需要添加“library”属性，以指定定义所在的方法库的名称。

此名称与“JavaScript代码”类型实体的名称（与命名空间）一致。

例如：

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
>用于库的命名空间和名称与找到声明的命名空间和架构名称无关。

### 定义 {#definition}

SOAP方法以JavaScript函数的形式实现，该函数以表示库的脚本的形式分组。

>[!NOTE]
>
>一种方法库可以对不同架构的函数进行分组，反之亦然，一个架构的函数可以在单独的库中定义。

脚本可以包含在初始库加载期间执行的代码。

**1. 名称**

函数名称必须符合以下格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

例如：

以下JavaScript函数是上述方法的实现。 它应使用“cus:test”名称在“JavaScript代码”类型实体中定义。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 签名**

函数的签名必须包含声明的每个“in”或“inout”参数的参数。

具体情况：

* **非静态方法**:该函数必须首先包含一个附加参数，与以“xml”(E4X)类型对象形式传递的XML实体相符。
* **“仅限键”类型方法**:该函数必须首先包含一个附加参数，与以字符串形式传递的键相同。

**3. 返回值**

函数必须为每个“out”或“inout”类型参数返回一个值。 具体情况：如果声明方法时没有“static”、“key only”或“const”属性，则第一个返回值必须与修改后的实体一致。 可以返回新对象或返回第一个修改过的参数。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

当要返回多个值时，它们必须显示在表中。

例如：

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

