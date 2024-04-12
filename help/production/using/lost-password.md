---
product: campaign
title: 密码丢失
description: 密码丢失
feature: Monitoring, Access Management
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 7%

---

# 密码丢失{#lost-password}



您可以更改或恢复丢失的密码。
有两种可能的情况：

* [Adobe Campaign操作员密码丢失](#password-lost-by-campaign-operator)
* [内部密码丢失](#internal-password-lost) （仅限内部部署客户）

## Campaign操作员密码丢失 {#password-lost-by-campaign-operator}

如果Adobe Campaign操作员丢失了密码，您可以更改密码。
为此请执行以下操作步骤：

1. 通过具有管理员权限的操作员连接。
1. 右键单击运算符。
1. 选择 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. 设置操作员的新密码。 我们建议操作员在首次重新连接时更改其密码。

## 内部密码丢失 {#internal-password-lost}

>[!NOTE]
>
>此部分仅适用于内部部署客户。

如果内部密码丢失，则必须重新初始化它。
要实现此目的，请执行以下步骤：

1. 编辑 **/usr/local/neolane/nl6/conf/serverConf.xml** 文件。

1. 转到 **internalPsword** 行。

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 删除引号中的字符串，在此例中为： **我的密码**

   这样，您将获得以下行：

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

1. 您现在可以使用新密码进行连接 **内部** 模式。
