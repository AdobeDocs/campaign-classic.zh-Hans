---
product: campaign
title: 跟踪URL的预处理说明
description: 进一步了解用于编写电子邮件URL脚本并仍对其进行跟踪的预处理说明。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 预处理指令 {#pre-processing-instructions}

![](../../assets/common.svg)

您可以在投放内容中使用特定语法来添加说明并编写跟踪电子邮件的URL脚本。 &lt;%@说明不是JavaScript:此语法专用于Adobe Campaign。

它们仅适用于投放内容的上下文。 这是编写电子邮件URL脚本并仍对其进行跟踪（除URL参数外）的唯一方法。 在检测要跟踪的链接之前，这些链接可被视为在投放分析期间应用的自动复制/粘贴。

说明有三种类型：

* **[!DNL include]**:主要用于在选项、个性化块、外部文件或页面中对某些代码进行分解。[了解详情](#include)
* **[!DNL value]**:以访问投放中加载的投放、投放变量和自定义对象的字段。[了解详情](#value)
* **[!DNL foreach]**:循环作为自定义对象加载的数组。[了解详情](#foreach)

可直接从投放向导中对它们进行测试。 它们适用于内容预览以及单击跟踪按钮以查看URL列表的情况。

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

* 现成退订URL:

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

利用此说明，可访问所有收件人均为常量的投放参数。

语法:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

其中：

* **[!DNL object]**:对象的名称(示例：投放、提供商等)。对象可以是：
   * **[!DNL delivery]**:（请参阅下文子部分中的详细信息和限制）。
   * **[!DNL provider]**:用于当前投放提供商/路由(nms:externalAccount)。
   * 额外的脚本对象：如果通过以下方式在上下文中加载对象：**属性** > **个性化** > **在执行上下文中添加对象**。
   * 轮次循环的项目：请参阅下面的[Foreach](#foreach)部分。
* **[!DNL xpath]**:字段的xpath。
* **[!DNL index]** （可选）：如果 **[!DNL object]** 是数组（对于其他脚本对象），则数组中的项索引（从0开始）。

### [!DNL delivery] 对象 {#delivery-object}

对于电子邮件个性化，可通过两种方式访问投放对象：

* 使用JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   在JavaScript对象交付自定义字段中，不支持此字段。 它们在预览中工作，但在MTA中不工作，因为MTA只能访问即装即用投放架构。

* 使用预处理：

   ```
   <%@ value object="delivery"
   ```


**注意**

如果您对通过中间源发送的投放使用以下说明，则必须将自定义字段&#x200B;**@myCustomField**&#x200B;添加到营销和中间源平台上的nms:delivery架构中：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

对于投放参数/变量，请使用以下语法（使用投放对象）：

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript部分中 {#value-in-javascript}

要允许在Javascript部分中使用&lt;%@值，两个特殊对象将被替换为&lt;%和%>:

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

* **[!DNL object]**:要开始的对象的名称，通常为额外的脚本对象，但可以是投放。
* **[!DNL xpath]** （可选）：要循环的集合的xpath。默认值为“。”，表示对象是要循环的数组。
* **[!DNL index]** （可选）：如果xpath不为“”，则为“”。和对象本身是数组，对象的项索引（从0开始）。
* **[!DNL item]** （可选）：可通过访问的新对象的名称  &lt;>默认使用架构中的链接名称。

示例:

在投放属性/个性化中，加载一组文章以及收件人与文章之间的关系表。

只需使用Javascript即可显示指向这些文章的链接，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

使用该解决方案，可无差别地跟踪指向所有文章的链接。 您可以知道收件人已单击文章链接，但无法知道是哪篇文章。

解决方案是：

1. 将所有可能的文章预加载到投放的额外脚本数组 — articleList[]中，这意味着可能的文章数必须有限。
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
