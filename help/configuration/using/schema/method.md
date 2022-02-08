---
product: campaign
title: 架构元素和属性
description: 方法元件
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 方法元件 {#method--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-10}

方法：==（帮助） |参数)

## 属性 {#attributes-10}

* @_operation（字符串）
* @access（字符串）
* @const（布尔）
* @hidden（布尔）
* @label（字符串）
* @library（字符串）
* @name(MNTOKEN)
* @pkonly（布尔）
* @static（布尔）

## 父母 {#parents-10}

`<methods>`  ,  `<interface />`

## 子项 {#children-10}

* `<help>`
* `<parameters>`

## 说明 {#description-10}

此元素允许您定义SOAP方法。

## 使用和使用上下文 {#use-and-context-of-use-7}

SOAP方法可启用应用程序进程。

声明新方法（非本机）时，需要使用“@library”：命名空间和用于库的名称与声明所在架构的命名空间和名称无关。

## 属性描述 {#attribute-description-10}

* **访问（字符串）**:此属性定义使用方法的访问控制。 如果缺少此属性，则必须进行标识。 可用值包括：“anonymous”、“admin”和“sql”。
* **常量（布尔值）**:如果激活了该属性，则此属性意味着声明的方法将更改实体
* **标签（字符串）**:方法的标签。
* **库（字符串）**:此方法不是应用程序的本机方法。 此属性采用找到方法定义的方法库的值(nms:mylibrary.js)。
* **name(MNTOKEN)**:唯一方法名称。
* **静态（布尔）**:如果激活此属性，则该方法被视为自主方法，则在调用该属性时必须为方法指定所有参数。

## 示例 {#examples-7}

“订阅”的现成方法定义：

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
