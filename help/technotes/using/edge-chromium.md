---
product: campaign
title: 技术说明 — 在您的Campaign环境中启用Microsoft Edge Chromium
description: 营销活动 — Edge Chromium
source-git-commit: a4a5e014d8055cf29bdbf7debb72eb20388c9b19
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---


# 如何在您的环境中启用Microsoft Edge Chromium {#edge-conf}

![](../../assets/v7-only.svg)


## 更改了哪些内容？

在Microsoft Internet Explorer 11生命周期结束后，客户端控制台中功能板的HTML渲染引擎正在使用Edge Chromium，从Campaign Classicv7.3开始。

除了Microsoft Edge Webview 2运行时的安装之外，该运行时现在为 [任何客户端控制台安装都需要](../../installation/using/installing-the-client-console.md#webview)，则必须在实例上启用Microsoft Edge Chromium 。

## 您是否受影响？

如果您的环境已升级到Campaign Classicv7.3（或更高版本），则您会受到影响。

## 如何更新？

* As a **托管** 客户，Adobe已在您的实例上启用Microsoft Edge Chromium。 无需执行其他操作。

* 作为 **内部部署/混合** 客户，您需要在实例上启用Microsoft Edge Chromium。

   升级到Campaign Classicv7.3（及更高版本）时，新 `webView2Mode` 属性在Campaign服务器配置文件中可用 `serverConf.xml`. 必须启用此属性。

   要执行此操作，请在所有环境(MKT、MID、RT)中应用以下步骤：

   1. 编辑Campaign服务器配置文件(`serverConf.xml`)
   1. 在 `<web>` 模块，设置 `webView2Mode = "1"`
   1. 运行以下命令以重新加载服务器配置：

      ```
      nlserver config -reload
      ```

   1. 运行以下命令以重新启动Web服务器：

      ```
      nlserver restart web
      ```

   1. 如果您的环境使用Apache作为Web服务器，请运行以下命令以重新启动Apache:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 相关主题

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [安装 Campaign Client Console](../../installation/using/installing-the-client-console.md)

