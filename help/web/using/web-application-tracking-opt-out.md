---
solution: Campaign Classic
product: campaign
title: Web 应用程序跟踪退出
description: Web 应用程序跟踪退出
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---


# Web 应用程序跟踪退出{#web-application-tracking-opt-out}

Adobe Campaign允许您通过cookie或网络信标停止跟踪退出行为跟踪的最终用户的网络行为。 该功能包括显示横幅以向最终用户显示该选项的功能；您可以将这些横幅添加到web应用程序或登陆页。

如果最终用户通过cookie或网络信标退出行为跟踪，则该信息将通过JavaScript API传输到Adobe Campaign跟踪服务器。 请注意，有些地区可能要求客户在向最终用户提供选择退出服务之前（或有其他法律要求），客户有责任遵守适用法律。

>[!NOTE]
>
>当脚本始终遵循[安全和隐私清单](https://helpx.adobe.com/campaign/kb/acc-security.html#dev)中所述的准则时。

## 配置横幅{#configuring-the-banner-}

要在Web 应用程序或登陆页中显示横幅，需要进行配置。

Adobe Campaign提供的横幅示例必须适应您的需求。 此横幅版本显示为位于内容模型文件夹中的个性化块。 请参见[此页面](../../delivery/using/personalization-blocks.md)。

>[!IMPORTANT]
>
>要创建自己的横幅，您必须个性化现成的横幅。

要激活横幅，您必须配置Web 应用程序属性。 请参阅[设计Web应用程序](../../web/using/designing-a-web-application.md)部分。

如果Web 跟踪已激活，您可以：

* 没有横幅。
* 在每个页面上手动配置横幅：选中此选项，并在页面属性的每个页面中选择横幅。

   ![](assets/pageproperties.png)

* 自动向所有页面添加横幅：直接在Web 应用程序属性中选择横幅。

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>v5Web 应用程序具有相同的行为，可使用兼容模式。

默认横幅的结构如下：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

您必须将&#x200B;**Please insert your message here**&#x200B;替换为包含跟踪信息的块。 此替换应在与退出横幅相关的新个性化块中执行。

横幅是通过特定CSS交付的。 但是，在创建和配置网页时，可以覆盖样式。 请参见[此页面](../../web/using/content-editor-interface.md)。

## 使用API {#setting-the-opt-out-cookie-using-api}设置退出Cookie

Adobe Campaign通过API提供，它允许您管理cookie值和检索用户首选项。

Cookie名称为&#x200B;**acoptout**。 常见值有：

* 0:用户已允许Web 跟踪（默认值）
* 1:用户已禁止Web 跟踪
* null:用户尚未选择，但允许Web 跟踪，因为它是默认值

可用于自定义横幅的客户端API包括：

* **NL.ClientWebTracking.allow()**:设置退出Cookie值以允许Web 跟踪。Web 跟踪默认为允许。
* **NL.ClientWebTracking.ordion()**:设置退出Cookie值以禁止Web 跟踪。Web 跟踪需要禁止用户输入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**:用户单击“接受”或“拒绝”按钮后，关闭退出Cookie横幅。(在单击事件冒泡阶段)

   bannerDomElt {DOMElement}需要删除的cookie横幅的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**:如果用户已选择其Web 跟踪首选项，则返回true。
* **NL.ClientWebTracking.getUserPrefs()**:返回定义用户首选项的退出Cookie值。

如果必须编写JSSP，则可以使用服务器端API:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**:为要插入JSSP页面的退出横幅生成标记

   **escapeJs {Boolean}**:当需要转义生成的标记以在JavaScript中使用时，为true。

   它返回需要在页面中打印的退出横幅标记的HTML。

* **NL.ServerWebTracking。_displayOptOutBanner()**

   如果管理员选择退出横幅后应显示退出横幅，则返回“true”

   管理员已选择使用Web 跟踪退出横幅时将调用此代码。

   如果用户尚未选择是否要跟踪，则应显示横幅。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   通过将退出横幅插入JSSP页面来呈现标记。 它在Jssp中按&lt;% %>的方式调用

   **escapeJs {Boolean}**:当需要转义生成的标记以在JavaScript内使用时为true

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

