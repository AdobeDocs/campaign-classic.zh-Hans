---
title: 实现 SOAP 方法
seo-title: 实现 SOAP 方法
description: 实现 SOAP 方法
seo-description: null
page-status-flag: never-activated
uuid: c9366f4e-460d-4087-88f7-9cc6d0de597a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 76984d9d-7759-4e0f-a275-09cca27589fa
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---


# 实现 SOAP 方法{#implementing-soap-methods}

## 简介 {#introduction}

可以在JavaScript中创建SOAP方法。 该函数简单支持应用进程，避免了在表单中开发JSP及其调用。

这些SOAP方法的行为方式与应用程序中本机定义的方法相同。 支持相同的属性：静态、仅密钥和const。

## 定义方法库 {#defining-a-method-library}

创建方法库涉及两个阶段：

* SOAP方法声明，
* JavaScript中的定义（或实现）。

### 声明 {#declaration}

开始，在模式中声明方法(有关如何创建和编辑模式的详细信息，请参 [阅本节](../../configuration/using/about-schema-edition.md))。

它们的声明与本机方法的声明相似，只是需要添加指定定义所在方法库名称的“library”属性。

此名称与“JavaScript代码”类型实体的名称(命名空间符)重合。

示例:

testLog(msg)方法在nms:收件人扩展中声明

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>命名空间和用于库的名称与找到声明的命名空间和模式名称无关。

### 定义 {#definition}

SOAP方法以JavaScript函数的形式实现，该函数以表示库的脚本的形式分组。

>[!NOTE]
>
>方法库可以对各种模式的函数进行分组，反之亦然，一个模式的函数可以在单独的库中定义。

脚本可包含在初始库加载期间要执行的代码。

**1. 名称**

函数名称必须符合以下格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

示例:

以下JavaScript函数是上述方法的实现。 它应使用“cus:test”名称在“JavaScript代码”类型实体中定义。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 签名**

函数的签名必须包含声明的每个“in”或“inout”参数的参数。

具体案例：

* **非静态方法**:该函数必须首先包含一个附加参数，与以“xml”(E4X)类型对象形式传递的XML实体一致。
* **“仅限键”类型方法**:该函数必须首先包含一个附加参数，与以字符串形式传递的键一致。

**3. 返回值**

函数必须为每个“out”或“inout”类型参数返回一个值。 具体情况：如果声明方法时没有“static”、“key only”或“const”属性，则第一个返回值必须与修改后的实体一致。 可以返回新对象或返回第一个修改的参数。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

当要返回多个值时，它们必须显示在表中。

示例:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

