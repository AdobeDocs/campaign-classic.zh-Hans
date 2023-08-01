---
product: campaign
title: 架构元素和属性 — 方法元素
description: 方法元素
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# 方法元素 {#method--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-10}

方法：==(帮助 |参数)

## 属性 {#attributes-10}

* @_operation（字符串）
* @access（字符串）
* @const（布尔型）
* @hidden（布尔型）
* @label（字符串）
* @library（字符串）
* @name (MNTOKEN)
* @pkonly（布尔型）
* @static（布尔型）

## 父项 {#parents-10}

`<methods>`  ,  `<interface />`

## 子项 {#children-10}

* `<help>`
* `<parameters>`

## 说明 {#description-10}

利用此元素，可定义SOAP方法。

## 使用和使用环境 {#use-and-context-of-use-7}

SOAP方法可启用应用程序进程。

对于声明新方法（非本地），“@library”是必需的：用于库的命名空间和名称与声明所在的架构的命名空间和名称无关。

## 属性说明 {#attribute-description-10}

* **访问（字符串）**：此属性定义使用方法的访问控制。 如果缺少此属性，则必须进行标识。 可用值为：“anonymous”、“admin”和“sql”。
* **常量（布尔型）**：如果激活，则此属性意味着声明的方法将更改实体
* **标签（字符串）**：方法的标签。
* **库（字符串）**：此方法不是应用程序的固有方法。 此属性采用找到方法定义的方法库的值(nms：mylibrary.js)。
* **名称(MNTOKEN)**：唯一的方法名称。
* **静态（布尔值）**：如果激活此属性，则该方法被视为自治方法，必须在调用该方法时将所有参数指定给该方法。

## 示例 {#examples-7}

“预订”开箱即用方法的定义：

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
