---
product: campaign
title: 适用于 Windows 的客户端控制台可用性
description: 适用于 Windows 的客户端控制台可用性
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# 适用于 Windows 的客户端控制台可用性{#client-console-availability-for-windows}



为了让Adobe Campaign用户能够登录到您已创建和配置的实例，他们需要使用客户端控制台。

## 使客户端控制台可用

当用于启动Adobe Campaign应用程序服务器的计算机时(**nlserver web**)接收来自客户端控制台的用户连接，您可以将其配置为通过HTML界面提供Adobe Campaign富客户端的安装程序。 每当有新版本的客户端控制台可用时，都会邀请用户在启动其客户端控制台时下载该版本。

要实现此目的，您必须：

1. 选择包含控制台安装程序的软件包。

   此文件名为 `setup-client-7.X.XXXX.exe` 对于v7或 `setup-client-6.X.XXXX.exe` 对于v6.1，其中 `X` 是Adobe Campaign的子版本，并且 `XXXX` 是内部版本号。

1. 将此包复制并粘贴到Adobe Campaign安装文件夹（对于混合安装，位于Marketing Server上）中的 **/datakit/nl/eng/jsp**.
1. 启动Adobe Campaign服务器。

之后，Campaign用户可借助以下URL通过Web浏览器下载控制台安装程序：

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此页面需要应用程序中定义的登录名和密码。

了解如何安装控制台 [在此部分中](../../installation/using/installing-the-client-console.md).

## 建议最终用户升级其客户端控制台

控制台在Campaign服务器文件夹中可用后，将邀请用户在专用的提示窗口中下载最新的客户端控制台版本。 Adobe建议保留选项 **[!UICONTROL No longer ask this question]** 未选中，以确保当有新版本的控制台可用时，所有用户都会收到警报。

如果选择此选项并选择不下载最新版本，则不会通知其他用户有新的可用版本。

如果选择了该选项，您可以重置此提示。 只有能够编辑Windows注册表的系统管理员才应该进行以下更改：

1. 使用打开注册表编辑器 **regedit** 命令 **[!UICONTROL Start > Run]** 菜单。
1. 搜索并展开节点。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除 **confAdvisedUpgrade** 输入并关闭注册表编辑器。
