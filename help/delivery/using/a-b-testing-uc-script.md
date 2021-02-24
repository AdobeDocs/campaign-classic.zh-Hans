---
solution: Campaign Classic
product: campaign
title: 创建脚本
description: 了解如何通过专用的用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# 创建脚本{#step-5--creating-the-script}

投放内容的选择将由脚本计算。 此脚本以最高打开率恢复有关投放的信息，并将内容复制到最终投放。

## 脚本{#example-of-a-script}的示例

以下脚本可以像在定位工作流程中一样使用。 有关详细信息，请参阅[实施](#implementation)。

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

有关脚本的详细说明，请参阅[脚本的详细信息](#details-of-the-script)。

## 实现{#implementation}

1. 打开&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动。
1. 将[脚本示例](#example-of-a-script)中提供的脚本复制到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;窗口中。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中，输入脚本的名称，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 关闭&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动。
1. 保存您的工作流。

## 脚本{#details-of-the-script}的详细信息

本部分详细介绍了脚本的各个部分及其操作模式。

* 脚本的第一部分是查询。 使用&#x200B;**queryDef**&#x200B;命令，您可以从&#x200B;**NmsDelivery**&#x200B;表中恢复通过执行定位工作流创建的投放，并根据其估计的打开率对它们进行排序，然后恢复来自打开率最高的投放的信息。

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* 打开率最高的投放是重复的。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 将修改复制投放的标签，并将单词&#x200B;**final**&#x200B;添加到该标签中。

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 投放将复制到活动仪表板。

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* 投放保存在数据库中。

   ```
   // save the delivery in database
   delivery.save()
   ```

* 复制投放的唯一标识符存储在工作流变量中。

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## 其他选择标准{#other-selection-criteria}

通过上面的示例，您可以根据电子邮件的打开率选择投放的内容。 您可以根据其他特定投放的指标调整它：

* 最佳点击吞吐量：`[indicators/@recipientClickRatio]`,
* 最高反应率（打开电子邮件并在邮件中单击）：`[indicators/@reactivity]`,
* 最低投诉率：`[indicators/@refusedRatio]`（对sortDesc属性使用false值），
* 最高转化率:`[indicators/@transactionRatio]`,
* 接收消息后访问的页数：`[indicators/@totalWebPage]`,
* 最低退订率：`[indicators/@optOutRatio]`,
* 事务处理金额：`[indicators/@amount]`。

您现在可以定义最终投放(请参阅[步骤6:定义最终投放](../../delivery/using/a-b-testing-uc-final-delivery.md))。
