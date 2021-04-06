---
solution: Campaign Classic
product: campaign
title: 活动- Salesforce CRM连接器
description: 连接活动和Salesforce.com
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Connect 活动和Microsoft Dynamics 365{#connect-to-msdyn}

在本页中，您将学习如何将Campaign Classic连接到&#x200B;**Salesforce**。

通过专用工作流活动进行数据同步。 [了解详情](../../platform/using/crm-data-sync.md)。


该外部帐户允许您将Salesforce数据导入并导出到Adobe Campaign。
要为Salesforce配置CRM连接器，请执行以下步骤：

1. 通过Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点创建新外部帐户。
1. 选择 **[!UICONTROL Salesforce.com]**。
1. 输入设置以启用连接。

   ![](assets/ext_account_17.png)

   要配置Salesforce CRM外部帐户以与Adobe Campaign一起使用，您需要提供以下详细信息：

   * **[!UICONTROL Account]**
用于登录Salesforce CRM的帐户。

   * **[!UICONTROL Password]**
用于登录Salesforce CRM的密码。

   * **[!UICONTROL Client identifier]**
要了解在何处查找客户端标识符，请参阅 [此页](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL Security token]**
要了解在何处查找您的安全令牌，请参阅此 [页](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL API version]**
选择API的版本。
1. 运行配置向导以生成可用的CRM表：通过配置向导，可以收集表并创建匹配模式。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >要批准设置，您需要注销并返回Adobe Campaign控制台。

1. 检查在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;节点的Adobe Campaign中生成的模式。

   **Salesforce**&#x200B;模式示例：

   ![](assets/crm_connectors_sfdc_table.png)

1. 创建模式后，您可以将明细列表从Salesforce自动同步到Adobe Campaign。

   要执行此操作，请单击&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;链接，然后选择与SalesforceAdobe Campaign匹配的明细列表明细列表。



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >您可以将Adobe Campaign明细列表的所有值替换为CRM的值：要执行此操作，请在&#x200B;**[!UICONTROL Replace]**&#x200B;列中选择&#x200B;**[!UICONTROL Yes]**。


   单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始导入列表。

1. 检查&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;菜单中导入的值。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支持多个选择明细列表。

活动和Salesforce.com现已连接。 可以在两个系统之间设置数据同步。

要在Adobe Campaign数据和SFDC之间同步活动，您需要创建一个工作流并使用&#x200B;**[!UICONTROL CRM connector]**&#x200B;数据。

![](assets/crm_connectors_sfdc_wf.png)

了解有关此页](../../platform/using/crm-data-sync.md)中数据同步[的更多信息。
