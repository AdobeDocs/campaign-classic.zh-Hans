---
title: 适用于Windows的客户端控制台可用性
seo-title: 适用于Windows的客户端控制台可用性
description: 适用于Windows的客户端控制台可用性
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 适用于Windows的客户端控制台可用性{#client-console-availability-for-windows}

要使Adobe Campaign用户能够登录您创建和配置的实例，他们需要使用客户端控制台。

当用于启动Adobe Campaign应用程序服务器(**nlserver web**)的计算机从客户端控制台接收用户连接时，您可以将其配置为通过HTML界面提供Adobe Campaign富客户端的设置程序。

为此，您必须：

1. 恢复包含控制台安装程序的包。

   v7或v6. `setup-client-7.X.XXXX.exe` 1调用此文件， `setup-client-6.X.XXXX.exe` 其中是Adobe Campaign的子版本， `X``XXXX` 是内部版本号。

1. 将此包复制并粘贴到Adobe Campaign安装文件夹中， **位于/datakit/nl/eng/jsp下**。
1. 启动Adobe Campaign服务器。

最终用户随后可以通过Web浏览器下载控制台安装程序，这要归功于以下URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此页面需要在应用程序中定义的登录名和口令。

要下载并安装控制台，请参阅安 [装客户端控制台](../../installation/using/installing-the-client-console.md)。

只要有新版本的客户端控制台可用，就会邀请您下载它。

>[!NOTE]
>
>在显示的提示中，Adobe建议取消选择该选项，以 **[!UICONTROL No longer ask this question]** 确保当控制台的新版本可用时，所有用户都会收到警告。\
>如果选择此选项并选择不下载最新版本，则不会向其他用户通知新的可用版本。

要重置此提示，请按照以下步骤操作（只有熟悉编辑注册表的系统管理员才应进行这些更改）:

1. 使用菜单中的regedit命 **令** ，打开注册表 **[!UICONTROL Start > Run]** 编辑器。
1. 搜索节点并展开它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除 **confDescuredUpgrade项** ，并关闭注册表编辑器。

