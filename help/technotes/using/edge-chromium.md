---
product: campaign
title: 技术说明 — 在Campaign环境中启用Microsoft Edge Chromium
description: Campaign - Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 7%

---

# 如何在您的环境中启用Microsoft Edge Chromium {#edge-conf}




## 更改了哪些内容？

在Microsoft Internet Explorer 11的生命周期终止后，客户端控制台中仪表板的HTML渲染引擎使用的是Edge Chromium，从Campaign Classicv7.3开始。

此外，还安装了Microsoft Edge Webview 2运行时，现在是 [任何客户端控制台安装均需要](../../installation/using/installing-the-client-console.md#webview)，必须在实例上启用Microsoft Edge Chromium 。

## 您是否受影响？

如果您的环境已升级到Campaign Classicv7.3（或更高版本），则您将受到影响。

## 如何更新？

* 作为 **托管** 客户，Adobe已在您的实例上启用Microsoft Edge Chromium 。 无需执行其他操作。

* 作为 **内部部署/混合** 客户，您需要在实例上启用Microsoft Edge Chromium 。

  升级到Campaign Classicv7.3（及更高版本）时，将 `webView2Mode` 属性在Campaign服务器配置文件中可用 `serverConf.xml`. 必须启用此属性。

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

   1. 如果您的环境使用Apache作为Web服务器，请运行以下命令以重新启动Apache：

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>

## 相关主题

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [安装 Campaign Client Console](../../installation/using/installing-the-client-console.md)
