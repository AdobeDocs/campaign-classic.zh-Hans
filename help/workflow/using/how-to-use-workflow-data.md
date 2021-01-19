---
solution: Campaign Classic
product: campaign
title: 如何使用工作流数据
description: 了解如何使用工作流数据
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 1901db70fde2b7b3c2789154bd93160012cd4c29
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---


# 如何使用工作流数据{#how-to-use-workflow-data}

## 更新数据库{#updating-the-database}

所有收集的数据都可用于更新数据库或投放。 例如，您可以丰富消息内容个性化的可能性（包括消息中的合同数、指定去年的平均购物车等） 或详细定位人群(向合同合同持有人发送消息，向1,000名最佳订阅者目标在线服务等)。 此数据也可以在列表中导出或存档。

### 列表和直接更新{#lists-and-direct-updates}

Adobe Campaign库和现有列表的数据可以使用两个专用活动进行更新：

* **[!UICONTROL List update]**&#x200B;活动允许您将工作表存储在数据列表中。

   您可以选择现有列表或创建它。 在这种情况下，将计算名称和可能的记录文件夹。

   ![](assets/s_user_create_list.png)

   请参阅[列表更新](../../workflow/using/list-update.md)。

* **[!UICONTROL Update data]**&#x200B;活动对数据库中的字段执行大量更新。

   有关详细信息，请参阅[更新数据](../../workflow/using/update-data.md)。

### 订阅/退订管理{#subscription-unsubscription-management}

要了解如何通过工作流订阅和取消订阅收件人信息服务，请参阅[订阅服务](../../workflow/using/subscription-services.md)。

## 通过工作流{#sending-via-a-workflow}发送

### 投放活动{#delivery-activity}

投放活动详见[投放](../../workflow/using/delivery.md)。

### 丰富和定向投放{#enriching-and-targeting-deliveries}

投放可以处理来自工作流的数据，以便自定义内容或在目标群体选择框架内。

例如，在直接邮件投放的框架中，您可以在提取文件中包含从工作流中执行的数据操作获取的附加数据：

![](assets/s_advuser_add_data_postal_mail.png)

除了常见的个性化字段之外，您还可以将工作流阶段的个性化字段添加到投放内容。 可以在投放向导中保留和访问工作流活动中定义的其他数据，如以下示例所示，以在直邮投放框架中定义输出文件的名称：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的数据由其名称标识：它始终由&#x200B;**targetData**&#x200B;链接组成。 有关详细信息，请参阅[目标数据](../../workflow/using/data-life-cycle.md#target-data)。

在电子邮件投放框架中，个性化字段还可以使用来自在定位工作流阶段执行的目标扩展的数据，如下例所示：

![](assets/s_advuser_add_data_email.png)

如果在定位段代码中指定了活动，则会将其添加到工作流表的特定列，并将提供该个性化字段。 要显示所有个性化字段，请单击可通过个性化按钮访问的&#x200B;**[!UICONTROL Target extension > Other...]**&#x200B;链接。

![](assets/s_advuser_segment_code_select.png)
