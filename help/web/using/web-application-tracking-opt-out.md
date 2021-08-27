---
product: campaign
title: 选择退出 Web 应用程序跟踪
description: 选择退出 Web 应用程序跟踪
audience: web
content-type: reference
topic-tags: web-applications
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---

# 选择退出 Web 应用程序跟踪{#web-application-tracking-opt-out}

![](../../assets/common.svg)

Adobe Campaign允许您停止跟踪通过cookie或网络信标选择退出行为跟踪的最终用户的Web行为。 该功能包括能够显示横幅，以向最终用户显示该选项；您可以将这些横幅添加到Web应用程序或登陆页面中。

如果最终用户通过Cookie或网络信标选择退出行为跟踪，则该信息会通过JavaScript API传输到Adobe Campaign跟踪服务器。 请注意，某些司法辖区可能要求客户在向最终用户提供选择加入后才能提供选择退出（或有其他法律要求），并且客户有责任遵守适用法律。

>[!NOTE]
>
>脚本编写时始终遵循[安全和隐私检查列表](https://helpx.adobe.com/campaign/kb/acc-security.html#dev)中描述的准则。

## 配置横幅 {#configuring-the-banner-}

要在Web应用程序或登陆页面中显示横幅，需要配置横幅。

Adobe Campaign提供了一个示例横幅，您必须根据自己的需求进行调整。 此横幅版本显示为位于内容模型文件夹中的个性化块。 请参见[此页面](../../delivery/using/personalization-blocks.md)。

>[!IMPORTANT]
>
>要创建您自己的横幅，必须个性化现成的横幅。

要激活横幅，必须配置Web应用程序属性。 请参阅[设计Web应用程序](designing-a-web-application.md)一节。

如果激活了Web跟踪，您可以：

* 没有横幅。
* 在每个页面上手动配置横幅：选中此选项，然后在页面属性的每个页面中选择横幅。

   ![](assets/pageproperties.png)

* 自动将横幅添加到所有页面：直接在Web应用程序属性中选择横幅。

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>v5 Web应用程序具有相同行为，可使用兼容模式。

默认横幅的结构如下：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

您必须将&#x200B;**Please insert your message here**&#x200B;替换为包含跟踪信息的块。 此替换操作应在与选择退出横幅相关的新个性化块中执行。

横幅将使用特定CSS进行传递。 但是，在创建和配置网页时，您可以覆盖样式。 请参见[此页面](content-editor-interface.md)。

## 使用API设置选择退出Cookie {#setting-the-opt-out-cookie-using-api}

Adobe Campaign随API一起提供，允许您管理Cookie值并检索用户首选项。

Cookie名称为&#x200B;**acoptout**。 常见值包括：

* 0:用户已允许Web跟踪（默认值）
* 1:用户已禁止Web跟踪
* null:用户未选择，但允许Web跟踪，因为它是默认值

用于自定义横幅的可用客户端API包括：

* **NL.ClientWebTracking.allow()**:设置选择禁用Cookie值以允许Web跟踪。默认情况下允许Web跟踪。
* **NL.ClientWebTracking.proid()**:设置禁用Cookie值以禁止Web跟踪。Web跟踪需要禁止用户输入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**:用户单击接受或拒绝按钮后，关闭选择退出Cookie横幅。（在点击事件冒泡阶段期间）

   bannerDomElt {DOMElement}需要删除的Cookie横幅的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**:如果用户选择了Web跟踪的首选项，则返回true。
* **NL.ClientWebTracking.getUserPrefs()**:返回用于定义用户首选项的选择退出Cookie值。

如果必须编写JSSP，则可以使用服务器端API:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**:为要插入到JSSP页面的选择退出横幅生成标记

   **escapeJs {Boolean}**:当生成的标记需要进行转义以在JavaScript中使用时，为true。

   它会返回需要在页面中打印的选择退出横幅标记的HTML。

* **NL.ServerWebTracking。_displayOptOutBanner()**

   如果管理员在选择禁用横幅后应显示禁用横幅，则返回“true”

   当管理员已选择使用Web跟踪选择退出横幅时，将调用此代码。

   如果用户尚未选择进行跟踪或未选择进行跟踪，则应显示横幅。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   通过将选择退出横幅的标记插入JSSP页面，可渲染该标记。 在&lt;% %>之间的Jssp中，此调用方式为

   **escapeJs {Boolean}**:当生成的标记需要进行转义以在JavaScript中使用时为true

JSSP示例：

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```
