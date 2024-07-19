---
product: campaign
title: 用于跟踪URL的预处理指令
description: 了解更多有关用于编写电子邮件URL脚本并且仍对其进行跟踪的预处理指令
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring
role: User, Data Engineer, Developer
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# 预处理指令 {#pre-processing-instructions}

您可以在投放内容中使用特定语法来添加说明，并为跟踪电子邮件的URL编写脚本。 &lt;%@说明不是JavaScript：此语法特定于Adobe Campaign。

它们仅适用于投放内容的上下文。 这是为电子邮件的URL编写脚本并且仍对其进行跟踪的唯一方法（除URL参数外）。 它们可以看作是在投放分析期间应用的自动复制/粘贴，然后再检测要跟踪的链接。

有三种类型的说明：

* **[!DNL include]**：主要用于分解选项、个性化块、外部文件或页面中的某些代码。 [了解详情](#include)
* **[!DNL value]**：授予投放字段、投放变量和投放中加载的自定义对象的访问权限。 [了解详情](#value)
* **[!DNL foreach]**：循环作为自定义对象加载的数组。 [了解详情](#foreach)

可以直接从投放向导中测试它们。 它们适用于内容预览以及单击跟踪按钮查看URL列表时。

## [!DNL include] {#include}

以下示例是最常用的：

* 包括镜像页面链接：

  ```
  <%@ include view="MirrorPage" %>  
  ```

* 镜像页面URL：

  ```
  View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
  ```

* 现成的退订URL：

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

此说明允许访问对所有收件人都保持不变的投放参数。

语法：

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

其中：

* **[!DNL object]**：对象的名称（例如：投放、提供程序等）。
对象可以是：
   * **[!DNL delivery]**：当前投放（请参阅以下子部分中的详细信息和限制）。
   * **[!DNL provider]**：用于当前传递提供程序/路由(nms：externalAccount)。
   * 额外的脚本对象：如果对象是通过&#x200B;**属性** > **Personalization** > **在执行上下文中添加对象**&#x200B;加载到上下文中的。
   * foreach循环的项：请参阅下面的[Foreach](#foreach)部分。
* **[!DNL xpath]**：字段的xpath。
* **[!DNL index]** （可选）：如果&#x200B;**[!DNL object]**&#x200B;是一个数组（用于额外的脚本对象），则数组中的项索引（从0开始）。

### [!DNL delivery]对象 {#delivery-object}

对于电子邮件个性化，可通过两种方式访问投放对象：

* 使用JavaScript：

  ```
  <%= delivery.myField %>`.
  ```

  在JavaScript中，不支持对象投放自定义字段。 它们可以在预览中使用，但不能在MTA中使用，因为MTA只能访问现成的投放模式。

* 使用预处理：

  ```
  <%@ value object="delivery"
  ```


**警告**

如果您对通过中间源发送的投放使用以下说明，则必须将自定义字段&#x200B;**@myCustomField**&#x200B;添加到营销和中间源平台上的nms：delivery架构中：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

对于投放参数/变量，请使用以下语法（使用投放对象）：

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### Javascript部分中的[!DNL value] {#value-in-javascript}

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

语法：

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

其中：

* **[!DNL object]**：开始对象的名称，通常是额外的脚本对象，但也可以是投放。
* **[!DNL xpath]** （可选）：要循环的集合的xpath。 默认值为“。”，这意味着对象是要循环处理的数组。
* **[!DNL index]** （可选）：如果xpath不是“。” 而对象本身是一个数组，即对象的项索引（从0开始）。
* **[!DNL item]** （可选）：可通过foreach循环中的&lt;%@值访问的新对象的名称。 在架构中具有链接名称的默认值。

例如：

在投放属性/个性化中，加载项目数组，以及收件人和项目之间的关系表。

显示这些文章的链接可以简单地用Javascript完成，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

使用该解决方案，可不加区分地跟踪所有文章的链接。 您可以知道收件人已点击文章链接，但您无法知道是哪篇文章。

解决方案是：

1. 在投放的额外脚本数组(articleList[])中预加载所有可能的文章，这意味着可能的文章数必须是有限的。
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

1. 通过调用函数显示文章。

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
