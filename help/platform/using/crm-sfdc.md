---
product: campaign
title: Campaign - Salesforce CRM连接器
description: 了解如何连接Campaign和Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
TQID: https://experienceleague.adobe.com/LeUJ-F5dAECUrtkbvgwL0BN88Alofnh2rBWe7hIVGgI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 323
ht-degree: 0%

---

# 连接Campaign和Salesforce.com{#connect-to-sfdc}



在本页中，您将了解如何将Campaign Classic连接到&#x200B;**Salesforce**。

数据同步通过专用工作流活动执行。 [了解详情](../../platform/using/crm-data-sync.md)。


外部帐户允许您将Salesforce数据导入和导出到Adobe Campaign中。
要为Salesforce配置CRM连接器，请执行以下步骤：

1. 通过Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点创建新的外部帐户。
1. 选择 **[!UICONTROL Salesforce.com]**。
1. 输入设置以启用连接。

   ![](assets/ext_account_17.png)

   要将Salesforce CRM外部帐户配置为与Adobe Campaign配合使用，您需要提供以下详细信息：

   * **[!UICONTROL Account]**
用于登录到Salesforce CRM的帐户。

   * **[!UICONTROL Password]**
用于登录到Salesforce CRM的密码。

   * **[!UICONTROL Client identifier]**
要了解在何处查找您的客户端标识符，请参阅此[页面](https://help.salesforce.com/articleView?id=000205876&type=1)。

   * **[!UICONTROL Security token]**
要了解在何处查找您的安全令牌，请参阅此[页面](https://help.salesforce.com/articleView?id=000205876&type=1)。

   * **[!UICONTROL API version]**
选择API的版本。
1. 运行Configuration Assistant以生成可用的CRM表：Configuration Assistant允许您收集表并创建匹配的架构。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >要批准设置，您需要注销并重新登录到Adobe Campaign控制台。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;节点中检查Adobe Campaign中生成的架构。

   **Salesforce**&#x200B;架构示例：

   ![](assets/crm_connectors_sfdc_table.png)

1. 创建架构后，您可以自动将枚举从Salesforce同步到Adobe Campaign。

   为此，请单击&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;链接，然后选择与Salesforce枚举匹配的Adobe Campaign枚举。



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >您可以将Adobe Campaign枚举的所有值替换为CRM的值：要实现此目的，请在&#x200B;**[!UICONTROL Replace]**&#x200B;列中选择&#x200B;**[!UICONTROL Yes]**。


   单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始导入列表。

1. 检查&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;菜单中的导入值。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支持多选枚举。

Campaign和Salesforce.com现已连接。 您可以设置两个系统之间的数据同步。

要在Adobe Campaign数据和SFDC之间同步数据，您需要创建工作流并使用&#x200B;**[!UICONTROL CRM connector]**&#x200B;活动。

![](assets/crm_connectors_sfdc_wf.png)

在此页面](../../platform/using/crm-data-sync.md)中了解有关数据同步[的更多信息。
