---
product: campaign
title: 适用于 Windows 的客户端控制台可用性
description: 适用于 Windows 的客户端控制台可用性
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# 适用于 Windows 的客户端控制台可用性{#client-console-availability-for-windows}

![](../../assets/v7-only.svg)

要使Adobe Campaign用户能够登录到您创建和配置的实例，他们需要使用客户端控制台。

## 使客户端控制台可用

当用于启动Adobe Campaign应用程序服务器(**nlserver web**)的计算机从客户端控制台接收用户连接时，您可以对其进行配置，以使Adobe Campaign富客户端的安装程序可通过HTML界面使用。 当客户端控制台有新版本可用时，系统会邀请用户在启动其客户端控制台时下载它。

为此，您必须：

1. 选择包含控制台安装程序的包。

   对于v7，此文件名为`setup-client-7.X.XXXX.exe`；对于v6.1，此文件名为`setup-client-6.X.XXXX.exe`，其中`X`是Adobe Campaign的子版本，`XXXX`是内部版本号。

1. 将此包复制并粘贴到Adobe Campaign安装文件夹（在混合安装的营销服务器上）的&#x200B;**/datakit/nl/eng/jsp**&#x200B;下。
1. 启动Adobe Campaign服务器。

然后，由于以下URL，Campaign用户可以通过Web浏览器下载控制台安装程序：

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此页面需要在应用程序中定义登录名和密码。

在此部分](../../installation/using/installing-the-client-console.md)中了解如何安装控制台[。

## 建议最终用户升级其客户端控制台

控制台在Campaign服务器文件夹中可用后，系统会邀请用户在专用的提示窗口中下载最新的客户端控制台版本。 Adobe建议取消选中选项&#x200B;**[!UICONTROL No longer ask this question]** ，以确保当有新版本的控制台可用时，所有用户都会收到警报。

如果选择此选项并选择不下载最新版本，则不会向其他用户通知新的可用版本。

如果选择了选项，则可以重置此提示。 只有能够编辑Windows注册表的系统管理员才应进行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表编辑器。
1. 搜索节点并展开该节点。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除&#x200B;**confAdwerdedUpgrade**&#x200B;条目并关闭注册表编辑器。
