---
title: 丢失密码
seo-title: 丢失密码
description: 丢失密码
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# 丢失密码{#lost-password}

您可以更改或恢复丢失的密码。

有两种可能的情况：

* Adobe Campaign运营商丢失了密码。

   在这种情况下，您可以更改相关操作员的口令。 为此，请通过具有管理员权限的操作员进行连接，右键单击操作员，选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 并设置操作员的新密码。 我们建议运营商在首次重新连接时更改其口令。

   ![](assets/operator-passwd.png)

* **内部** 密码丢失（仅限内部部署客户）。

   如果内 **部密码丢失** ，则必须重新初始化它。 为此，请应用以下过程：

   1. 编辑/usr/local/neolane/nl6/conf/serverConf.xml **文件** 。
   1. 转到 **internalPassword** 行。

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. 删除引号中的字符串，在本例中： **myPassword**

      因此，您会获得以下代码行：

      ```
      !-- XTK authentication mode internalPassword : Password of internal account -->
      <xtk internalPassword=""/
      ```

   1. 保存更改并关闭文件。
   1. 配置新密码。 为此，请输入以下命令：

      ```
      nlserver config -internalpassword
      HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
      Enter current password.
      Password: (empty)
      Enter the new password.
      Password: 
      Confirmation 
      ```

   1. 您现在可以使用新密码在“内部”模式 **下连接** 。

