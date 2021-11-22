---
product: campaign
title: 密码丢失
description: 密码丢失
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 7%

---

# 密码丢失{#lost-password}

![](../../assets/v7-only.svg)

您可以更改或恢复丢失的密码。
有两种可能的情况：

* [Adobe Campaign运算符丢失密码](#password-lost-by-campaign-operator)
* [内部密码丢失](#internal-password-lost) （仅限内部部署客户）

## Campaign操作员丢失密码 {#password-lost-by-campaign-operator}

如果Adobe Campaign运算符丢失其密码，您可以更改它。
为此请执行以下操作步骤：

1. 通过具有管理员权限的运算符进行连接。
1. 右键单击运算符。
1. 选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. 设置操作员的新密码。 我们建议操作员在首次重新连接时更改其密码。

## 内部密码丢失 {#internal-password-lost}

>[!NOTE]
>
>此部分仅适用于内部部署客户。

如果内部密码丢失，则必须重新初始化它。
要执行此操作，请应用以下过程：

1. 编辑 **/usr/local/neolane/nl6/conf/serverConf.xml** 文件。

1. 转到 **internalPassword** 行。

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 删除带引号的字符串，在此例中为： **myPassword**

   因此，可获得以下行：

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

1. 现在，您可以使用新密码连接 **内部** 模式。
