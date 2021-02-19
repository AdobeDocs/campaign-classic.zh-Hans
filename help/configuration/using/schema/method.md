---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---


# 方法元素{#method--element}

## 内容模型{#content-model-10}

方法：==(help |参数)

## 属性{#attributes-10}

* @_operation(string)
* @access(string)
* @const（布尔值）
* @hidden（布尔值）
* @label(string)
* @library(string)
* @name(MNTOKEN)
* @pkonly（布尔值）
* @static（布尔值）

## 父项{#parents-10}

`<methods>`  ,  `<interface />`

## 子项{#children-10}

* `<help>`
* `<parameters>`

## 说明{#description-10}

此元素允许您定义SOAP方法。

## 使用和上下文{#use-and-context-of-use-7}

SOAP方法启用应用程序进程。

声明新方法（非本机）时必须使用“@library”：命名空间和用于库的名称与声明所在模式的命名空间和名称无关。

## 属性描述{#attribute-description-10}

* **access(string**):此属性定义使用方法的访问控制。如果缺少此属性，则必须进行标识。 可用值有：“anonymous”、“admin”和“sql”。
* **const（布尔值）**:如果激活了该属性，则此属性意味着声明的方法将更改实体
* **label(string**):方法的标签。
* **库(字符串**):此方法不是应用程序的本机方法。此属性采用找到方法定义的方法库的值(nms:mylibrary.js)。
* **name(MNTOKEN)**:唯一方法名称。
* **静态（布尔值）**:如果激活了此属性，则该方法被视为自主方法，则调用该属性时必须为该方法指定所有参数。

## 示例{#examples-7}

现成“订阅”方法的定义：

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
