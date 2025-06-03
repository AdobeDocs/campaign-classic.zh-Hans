---
product: campaign
title: Campaign - Salesforce CRM连接器
description: 了解如何连接Campaign和Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '321'
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
要了解在何处查找您的客户端标识符，请参阅此[页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL Security token]**
要了解在何处查找您的安全令牌，请参阅此[页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

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
