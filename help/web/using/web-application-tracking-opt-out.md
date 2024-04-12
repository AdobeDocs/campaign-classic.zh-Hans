---
product: campaign
title: 选择退出 Web 应用程序跟踪
description: 选择退出 Web 应用程序跟踪
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%

---

# 选择退出 Web 应用程序跟踪{#web-application-tracking-opt-out}



Adobe Campaign允许您停止跟踪通过Cookie或Web信标选择退出行为跟踪的最终用户的Web行为。 该功能包括显示横幅以向最终用户展示该选项的功能；您可以将这些横幅添加到Web应用程序或登陆页面中。

如果最终用户选择通过Cookie或Web信标退出行为跟踪，则该信息将通过JavaScript API传输到Adobe Campaign跟踪服务器。 请注意，某些管辖区可能要求客户在提供选择退出服务之前向最终用户提供选择加入服务（或有其他法律要求），并且客户有责任遵守适用法律。

>[!NOTE]
>
>当脚本编写始终遵循中所述的准则时 [安全和隐私检查清单](https://helpx.adobe.com/campaign/kb/acc-security.html#dev).

## 配置横幅 {#configuring-the-banner-}

要在Web应用程序或登陆页面中显示，需要配置横幅。

Adobe Campaign附带一个横幅示例，您必须根据自己的需求进行调整。 此横幅版本在内容模型文件夹中显示为个性化块。 请参见[此页面](../../delivery/using/personalization-blocks.md)。

>[!IMPORTANT]
>
>要创建您自己的横幅，必须个性化现成的横幅。

要激活横幅，您必须配置Web应用程序属性。 请参阅 [设计Web应用程序](designing-a-web-application.md) 部分。

如果激活了Web跟踪，则您可以：

* 无横幅。
* 在每个页面上手动配置横幅：选中此选项并在页面属性中选择每个页面中的横幅。

  ![](assets/pageproperties.png)

* 自动将横幅添加到所有页面：直接在Web应用程序属性中选择横幅。

  ![](assets/optoutconfig.png)

>[!NOTE]
>
>兼容模式适用于具有相同行为的v5 Web应用程序。

默认横幅具有以下结构：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

您必须更换 **请在此处插入您的消息** 包含跟踪信息的块。 此替换应在与选择退出横幅相关的新个性化块中执行。

横幅使用特定的CSS交付。 但是，您可以在创建和配置网页时覆盖样式。 请参见[此页面](content-editor-interface.md)。

## 使用API设置选择退出Cookie {#setting-the-opt-out-cookie-using-api}

Adobe Campaign附带的API允许您管理Cookie值并检索用户首选项。

Cookie名称为 **acoptout**. 通用值包括：

* 0：用户已允许Web跟踪（默认值）
* 1：用户已禁止进行Web跟踪
* null：用户尚未选择，但允许Web跟踪，因为它是默认值

用于自定义横幅的可用客户端API包括：

* **NL.ClientWebTracking.allow()**：设置选择退出Cookie值以允许Web跟踪。 默认情况下，允许Web跟踪。
* **NL.ClientWebTracking.forbid()**：设置选择退出Cookie值以禁止Web跟踪。 Web跟踪需要禁止用户输入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**：在用户单击接受或拒绝按钮后，关闭选择退出Cookie横幅。 （在单击事件冒泡阶段期间）

  bannerDomElt {DOMElement} 需要删除的Cookie横幅的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**：如果用户已选择他们的Web跟踪首选项，则返回true。
* **NL.ClientWebTracking.getUserPrefs()**：返回定义用户首选项的选择退出Cookie值。

如果必须编写JSSP，则可以使用服务器端API：

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**：为要插入到JSSP页面中的选择退出横幅生成标记

  **escapeJs {Boolean}**：当生成的标记需要转义以便在JavaScript中使用时，返回true。

  它会返回需要在页面中打印的选择退出横幅标记的HTML。

* **NL.ServerWebTracking。_displayOptOutBanner()**

  如果在管理员选择退出横幅后应显示选择退出横幅，则返回“true”

  当管理员已选择使用Web跟踪选择退出横幅时，将调用此代码。

  如果用户尚未选择是否进行跟踪，则将显示横幅。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

  通过将选择退出横幅插入JSSP页面来呈现该横幅的标记。 此函数在Jssp中为&lt;% %>之间，按原样调用

  **escapeJs {Boolean}**：当生成的标记需要转义以便在JavaScript中使用时，为true

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
