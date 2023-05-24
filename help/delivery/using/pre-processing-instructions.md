---
product: campaign
title: 跟踪的URL的预处理指令
description: 详细了解用于编写电子邮件URL脚本且仍对其进行跟踪的预处理指令
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 2%

---

# 预处理指令 {#pre-processing-instructions}



您可以在投放内容中使用特定语法来添加说明，并为跟踪电子邮件的URL编写脚本。 &lt;%@说明不是JavaScript：此语法特定于Adobe Campaign。

它们仅适用于投放内容的上下文。 这是为电子邮件的URL编写脚本但仍对其进行跟踪的唯一方法（除URL参数外）。 它们可以视为在检测要跟踪的链接之前投放分析期间应用的自动复制/粘贴。

有三种类型的说明：

* **[!DNL include]**：主要用于分解选项、个性化块、外部文件或页面中的某些代码。 [了解详情](#include)
* **[!DNL value]**：授予对投放字段、投放变量和投放中加载的自定义对象的访问权限。 [了解详情](#value)
* **[!DNL foreach]**：循环加载为自定义对象的数组。 [了解详情](#foreach)

可以直接从投放向导中测试它们。 它们适用于内容预览以及单击跟踪按钮以查看URL列表时。

## [!DNL include] {#include}

以下示例是最常用的：

* 包括镜像页面链接：

   ```
   <%@ include view="MirrorPage" %>  
   ```

* 镜像页面 URL:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* 开箱即用的退订URL：

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

本说明可让您访问对所有收件人都保持不变的投放参数。

语法:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

其中：

* **[!DNL object]**：对象的名称（例如：投放、提供程序等）。
对象可以是：
   * **[!DNL delivery]**：适用于当前投放（请参阅下面子部分中的详细信息和限制）。
   * **[!DNL provider]**：适用于当前投放提供商/路由(nms：externalAccount)。
   * 额外的脚本对象：如果对象是通过以下方式加载到上下文中的： **属性** > **个性化** > **在执行上下文中添加对象**.
   * foreach循环的项目：请参见 [福雷阿赫](#foreach) 部分。
* **[!DNL xpath]**：字段的xpath。
* **[!DNL index]** （可选）：如果 **[!DNL object]** 是一个数组（用于额外的脚本对象），数组中的项索引（从0开始）。

### [!DNL delivery] 对象 {#delivery-object}

对于电子邮件个性化，可通过两种方式访问投放对象：

* 使用JavaScript：

   ```
   <%= delivery.myField %>`.
   ```

   在JavaScript对象投放中，不支持自定义字段。 它们可以在预览中使用，但不能在MTA中使用，因为MTA只能访问现成的投放模式。

* 使用预处理：

   ```
   <%@ value object="delivery"
   ```


**注意**

如果您对通过中间源发送的投放使用以下说明，则自定义字段 **@myCustomField** 必须添加到营销和中间源平台上的nms：delivery模式中：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

对于投放参数/变量，请使用以下语法（使用投放对象）：

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript部分中 {#value-in-javascript}

要允许在Javascript部分中使用&lt;%@值，请将两个特殊对象替换为&lt;%和%>：

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

此指令允许对投放中加载的对象数组进行迭代，以跟踪与对象相关的各个链接。

语法:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

其中：

* **[!DNL object]**：开始对象的名称，通常是额外的脚本对象，但也可以是投放。
* **[!DNL xpath]** （可选）：要循环的集合的xpath。 默认值为“。”，这意味着对象是要循环处理的数组。
* **[!DNL index]** （可选）：如果xpath不是“。” 而对象本身是一个数组，即对象的项索引（从0开始）。
* **[!DNL item]** （可选）：可在foreach循环中使用&lt;%@值访问的新对象的名称。 默认为架构中的链接名称。

示例:

在投放属性/个性化中，加载项目数组和收件人与项目之间的关系表。

显示指向这些文章的链接只需使用Javascript即可，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

使用该解决方案，可以不加区别地跟踪指向所有文章的链接。 您可以知道收件人点击了文章链接，但您无法知道是哪篇文章。

解决方案是：

1. 在投放的额外脚本数组中预加载所有可能的文章 — articleList[]  — 这意味着必须有有限数量的可能项目。
1. 在内容的开头编写JavaScript函数。

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

1. 通过调用函数来显示文章。

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
