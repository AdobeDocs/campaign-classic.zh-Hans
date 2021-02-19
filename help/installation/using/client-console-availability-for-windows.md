---
solution: Campaign Classic
product: campaign
title: 适用于 Windows 的客户端控制台可用性
description: 适用于 Windows 的客户端控制台可用性
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 5%

---


# 适用于 Windows 的客户端控制台可用性{#client-console-availability-for-windows}

为了使Adobe Campaign用户能够登录您创建和配置的实例，他们需要使用客户端控制台。

当用于开始Adobe Campaign应用程序服务器(**nlserver web**)的计算机从客户端控制台接收用户连接时，您可以配置它，使Adobe Campaign富客户端的设置项目通过HTML界面可用。

为此，您必须：

1. 恢复包含控制台安装项目的包。

   对于v7或v6.1，此文件称为`setup-client-7.X.XXXX.exe`，其中`X`是Adobe Campaign的子版本，`XXXX`是内部版本号。`setup-client-6.X.XXXX.exe`

1. 将此包复制并粘贴到Adobe Campaign安装文件夹中，位于&#x200B;**/datakit/nl/eng/jsp**&#x200B;下。
1. 开始Adobe Campaign服务器。

最终用户随后可以通过Web浏览器下载控制台安装项目，这要归功于以下URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此页要求在应用程序中定义登录名和口令。

要下载并安装控制台，请参阅[安装客户端控制台](../../installation/using/installing-the-client-console.md)。

只要有新版本的客户端控制台可用，您就会被邀请下载它。

>[!NOTE]
>
>在显示的提示中，Adobe建议取消选择选项&#x200B;**[!UICONTROL No longer ask this question]**，以确保当新版本的控制台可用时，所有用户都会收到警告。\
>如果您选择此选项并选择不下载最新版本，则不会向其他用户通知新的可用版本。

要重置此提示，请按照以下步骤操作（只有能够编辑注册表的系统管理员才应进行这些更改）：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表编辑器。
1. 搜索节点并展开它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除&#x200B;**confAdwerdedUpgrade**&#x200B;条目并关闭注册表编辑器。

