---
solution: Campaign Classic
product: campaign
title: 适用于 Windows 的客户端控制台可用性
description: 适用于 Windows 的客户端控制台可用性
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---


# 适用于 Windows 的客户端控制台可用性{#client-console-availability-for-windows}

为了使Adobe Campaign用户能够登录您创建和配置的实例，他们需要使用客户端控制台。

## 使客户端控制台可用

当用于开始Adobe Campaign应用程序服务器(**nlserver web**)的计算机从客户端控制台接收用户连接时，您可以配置它，使Adobe Campaign富客户端的设置项目通过HTML界面可用。 只要有新版本的客户端控制台可用，用户就会在启动其客户端控制台时被邀请下载它。

为此，您必须：

1. 选择包含控制台安装项目的包。

   对于v7或v6.1，此文件称为`setup-client-7.X.XXXX.exe`，其中`X`是Adobe Campaign的子版本，`XXXX`是内部版本号。`setup-client-6.X.XXXX.exe`

1. 将此包复制并粘贴到Adobe Campaign安装文件夹（在混合安装的营销服务器上）中，位于&#x200B;**/datakit/nl/eng/jsp**&#x200B;下。
1. 开始Adobe Campaign服务器。

活动用户随后可以通过Web浏览器下载控制台安装项目，这要归功于以下URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此页要求在应用程序中定义登录名和口令。

了解如何在本节](../../installation/using/installing-the-client-console.md)中安装控制台[。

## 建议最终用户升级其客户端控制台

控制台在活动服务器文件夹中可用后，将邀请用户在专用的提示窗口中下载最新的客户端控制台版本。 Adobe建议取消选择选项&#x200B;**[!UICONTROL No longer ask this question]**，以确保当新版本的控制台可用时，所有用户都会收到警告。

如果您选择此选项并选择不下载最新版本，则不会向其他用户通知新的可用版本。

如果选中了该选项，您可以重置此提示。 只有能够编辑Windows注册表的系统管理员才应进行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表编辑器。
1. 搜索节点并展开它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除&#x200B;**confAdwerdedUpgrade**&#x200B;条目并关闭注册表编辑器。

