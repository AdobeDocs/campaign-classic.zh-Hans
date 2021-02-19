---
solution: Campaign Classic
product: campaign
title: 密码丢失
description: 密码丢失
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 7%

---


# 密码丢失{#lost-password}

您可以更改或恢复丢失的密码。
有两种可能的情况：

* [密码由Adobe Campaign运算符丢失](#password-lost-by-campaign-operator)
* [内部密码丢失](#internal-password-lost) （仅限预置型客户）

## 活动运算符{#password-lost-by-campaign-operator}丢失了密码

如果Adobe Campaign运算符丢失了其密码，您可以更改它。
为此请执行以下操作步骤：

1. 通过具有管理员权限的操作员连接。
1. 右键单击运算符。
1. 选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**。

   ![](assets/operator-passwd.png)

1. 设置操作员的新密码。 我们建议操作员在首次重新连接时更改其密码。

## 内部密码丢失{#internal-password-lost}

>[!NOTE]
>
>本条仅适用于预置型客户。

如果内部密码丢失，则必须重新初始化它。
为此，请应用以下过程：

1. 编辑&#x200B;**/usr/local/neolane/nl6/conf/serverConf.xml**&#x200B;文件。

1. 转到&#x200B;**internalPassword**&#x200B;行。

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 删除引号中的字符串，在此例中为：**myPassword**

   因此，您获得以下行：

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. 保存更改并关闭文件。

1. 配置新密码。 要执行此操作，请输入以下命令：

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 您现在可以使用新口令在&#x200B;**Internal**&#x200B;模式下连接。
