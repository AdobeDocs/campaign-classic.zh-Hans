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
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 3%

---

# 密码丢失{#lost-password}

>[!NOTE]
>
>此页面仅适用于使用本机身份验证连接到Campaign的操作员。

您可以更改或恢复丢失的密码。
有两种可能的情况：

* [Adobe Campaign操作员密码丢失](#password-lost-by-campaign-operator)
* [内部密码丢失](#internal-password-lost)（仅限内部部署客户）

## Campaign操作员密码丢失 {#password-lost-by-campaign-operator}

如果Adobe Campaign操作员丢失了密码，您可以更改密码。

>[!NOTE]
>
>此过程仅适用于使用本机身份验证连接到Campaign的操作员。 有关Adobe IMS身份验证，请参阅[此文档](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}。

要重置Campaign密码，请执行以下步骤：

1. 通过具有管理员权限的操作员连接。
1. 右键单击运算符。
1. 选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**。

   ![](assets/operator-passwd.png)

1. 设置操作员的新密码。 我们建议操作员在首次重新连接时更改其密码。

## 内部密码丢失 {#internal-password-lost}

>[!NOTE]
>
>此部分仅适用于内部部署客户。

如果内部密码丢失，则必须重新初始化它。

要实现此目的，请执行以下步骤：

1. 编辑&#x200B;**/usr/local/neolane/nl6/conf/serverConf.xml**&#x200B;文件。

1. 转到&#x200B;**internalPassword**&#x200B;行。

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 删除带引号的字符串，在此例中为： `myPassword`。 您将获得以下行：

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. 保存更改并关闭文件。

1. 停止`nlserver`进程。

1. 配置新密码。 为此，请输入以下命令：

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 启动`nlserver`进程。

1. 您现在可以使用新密码在&#x200B;**内部**&#x200B;模式下连接。
