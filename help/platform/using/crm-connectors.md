---
solution: Campaign Classic
product: campaign
title: CRM 连接器
description: 开始使用活动中的CRM连接器
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 24%

---


# CRM 连接器{#crm-connectors}

## 开始使用CRM连接器{#about-crm-connectors}

Adobe Campaign 提供各种 CRM 连接器，可将您的 Adobe Campaign 平台链接到第三方系统。通过这些 CRM 连接器，您可以同步处理联系人、帐户、购买等。您可以使用这些 CRM 连接器轻松地将您的应用程序与各第三方和商务应用程序相集成。

通过这些连接器，可快速轻松地集成数据：Adobe Campaign 提供专用的向导，让您从 CRM 中提供的表中收集和选择数据。并且可确保双向同步处理，让整个系统中的数据随时保持最新。

>[!NOTE]
>
>此功能可通过&#x200B;**CRM连接器**&#x200B;专用软件包进行Adobe Campaign。


### 兼容系统{#compatible-crm-systems-and-limitations}

支持的CRM和版本详见活动[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

>[!NOTE]
>
>CRM连接器只能使用安全URL(https)。

### 实施步骤 {#crm-implementation-steps}

了解连接活动和Microsoft Dynamics [的分步过程，请参阅本节](../../platform/using/crm-ms-dynamics.md)

通常，要在Adobe Campaign中使用CRM连接器，请执行以下步骤：

1. 通过外部帐户树的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点创建新Adobe Campaign。
1. 选择需要将活动连接到的CRM系统。
1. 输入设置以启用连接。
1. 运行配置向导以生成可用的CRM表：通过配置向导，可以收集表并创建匹配的模式。

   **Salesforce**&#x200B;配置向导的示例：

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >要批准设置，您需要注销并重新登录到Adobe Campaign控制台。

1. 检查在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;节点的Adobe Campaign中生成的模式。

   **Salesforce**&#x200B;模式示例：

   ![](assets/crm_connectors_sfdc_table.png)

1. 创建模式后，您可以通过CRM自动将明细列表同步到Adobe Campaign。

   为此，请单击&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;链接，然后选择与CRMAdobe Campaign匹配的明细列表。

   >[!NOTE]
   >
   >您可以将Adobe Campaign明细列表的所有值替换为CRM的值：为此，请在&#x200B;**[!UICONTROL Replace]**&#x200B;列中选择&#x200B;**[!UICONTROL Yes]**。

   **Salesforce**&#x200B;明细列表示例：

   ![](assets/crm_connectors_sfdc_enum.png)

   单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始导入列表。

1. 检查&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;菜单中导入的值。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Salesforce中不支持多个选择明细列表。

1. 要在Adobe Campaign数据和CRM系统之间同步数据，您需要创建一个工作流并使用&#x200B;**[!UICONTROL CRM connector]**&#x200B;活动。

   ![](assets/crm_connectors_sfdc_wf.png)

   了解有关此页](../../platform/using/crm-data-sync.md)中数据同步[的更多信息。
