---
solution: Campaign Classic
product: campaign
title: 密码丢失
description: 密码丢失
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# 密码丢失{#lost-password}

您可以更改或恢复丢失的密码。

有两种可能的情况：

* Adobe Campaign操作员丢失密码。

   在这种情况下，您可以更改相关操作员的口令。 为此，请通过具有管理员权限的操作员进行连接，右键单击操作员，选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**&#x200B;并设置操作员的新密码。 我们建议运营商在首次重新连接时更改其口令。

   ![](assets/operator-passwd.png)

* **内** 部密码丢失（仅限预置型客户）。

   如果&#x200B;**internal**&#x200B;密码丢失，则必须重新初始化它。 为此，请应用以下过程：

   1. 编辑&#x200B;**/usr/local/neolane/nl6/conf/serverConf.xml**&#x200B;文件。
   1. 转至&#x200B;**internalPassword**&#x200B;行。

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. 删除引号中的字符串，在本例中：**myPassword**

      因此，您可以获得以下行：

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

   1. 您现在可以使用新密码在&#x200B;**内部**&#x200B;模式下进行连接。

