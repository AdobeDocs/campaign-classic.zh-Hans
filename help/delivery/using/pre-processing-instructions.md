---
solution: Campaign Classic
product: campaign
title: 跟踪的URL的预处理说明
description: 了解有关用于编写电子邮件URL脚本的预处理说明的更多信息，但仍要跟踪这些说明。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
translation-type: tm+mt
source-git-commit: fdcb96c3c4afed1f36529e658eda26766226c44f
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 预处理指令{#pre-processing-instructions}

您可以在投放内容中使用特定语法来添加说明和编写跟踪电子邮件的URL的脚本。 &lt;%@说明不是JavaScript:此语法特定于Adobe Campaign。

它们仅适用于投放内容的上下文。 这是编写电子邮件URL脚本并仍对其进行跟踪（除URL参数外）的唯一方法。 在检测要跟踪的链接之前，这些链接可被视为在投放分析期间应用的自动复制/粘贴。

有三种说明类型：

* **[!DNL include]**:主要是将选项、个性化块、外部文件或页面中的某些代码分解。[了解详情](#include)
* **[!DNL value]**:可访问投放、投放变量和加载到投放中的自定义对象的字段。[了解详情](#value)
* **[!DNL foreach]**:以循环作为自定义对象加载的数组。[了解详情](#foreach)

可以直接从投放向导中测试。 它们会在内容预览中应用，当您单击跟踪按钮时，您会看到URL的列表。

## [!DNL include] {#include}

以下示例是最常用的示例：

* 包括镜像页面链接：

   ```
   <%@ include view="MirrorPage" %>  
   ```

* 镜像页面URL:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* 开箱即用的退订url:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* 其他示例：

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   使用投放向导中的个性化按钮获取正确的语法。

## [!DNL value] {#value}

此说明允许访问所有投放的常量参数。

语法:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

地点：

* **[!DNL object]**:对象的名称(示例：投放、提供商等)。对象可以是：
   * **[!DNL delivery]**:当前投放（请参阅下文小节中的详细信息和限制）。
   * **[!DNL provider]**:对于当前投放提供者/路由(nms:externalAccount)。
   * 额外的脚本对象：如果对象通过以下方式加载到上下文中：**属性** > **个性化** > **在执行上下文中添加对象**。
   * foreach循环的项：请参见下面的[Foreach](#foreach)部分。
* **[!DNL xpath]**:字段的xpath。
* **[!DNL index]** （可选）：如 **[!DNL object]** 果是数组（对于其他脚本对象），则数组中的项索引(开始为0)。

### [!DNL delivery] 对象 {#delivery-object}

对于电子邮件个性化，可通过两种方式访问投放对象：

* 使用JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   在JavaScript对象投放中，不支持自定义字段。 它们在预览中工作，但在MTA中不工作，因为MTA只能访问现成的投放模式。

* 使用预处理：

   ```
   <%@ value object="delivery"
   ```


**警告**

如果您正在对通过中间源发送的投放使用以下说明，则必须在营销和中间源平台的nms:投放模式中添加自定义字段&#x200B;**@myCustomField**:

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

对于投放参数/变量，请使用以下语法(使用投放对象):

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript部分  {#value-in-javascript}

要允许在Javascript部分中使用&lt;%@值，两个特殊对象将替换为&lt;%和%>:

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

例如：

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

此指令允许对加载到投放中的对象数组进行迭代，以跟踪与对象相关的各个链接。

语法:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

地点：

* **[!DNL object]**:要从中开始的对象的名称，通常是额外的脚本对象，但它可以是投放。
* **[!DNL xpath]** （可选）：要循环的集合的xpath。默认值为“。”，表示对象是要循环的数组。
* **[!DNL index]** （可选）：如果xpath不是&quot;&quot;and object是数组本身，对象的项索引(开始为0)。
* **[!DNL item]** （可选）：新对象的名称  &lt;>默认为模式中的链接名称。

示例:

在投放属性/个性化中，加载一组文章以及收件人和文章之间的关系表。

只需使用Javascript即可显示指向这些文章的链接，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

通过该解决方案，可以毫不区分地跟踪指向所有文章的链接。 您可以知道收件人单击了文章链接，但您无法知道哪篇文章。

解决方案是：

1. 将所有可能的文章预加载到投放的额外脚本数组中 — articleList[] — 这意味着必须有有限数量的可能文章。
1. 在内容的开头编写一个JavaScript函数。

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```

1. 通过调用函数显示文章。

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
