---
product: campaign
title: 创建脚本
description: 了解如何通过专用用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 4%

---

# 创建脚本 {#step-5--creating-the-script}

![](../../assets/common.svg)

脚本会计算用于剩余群体的投放内容的选择。 此脚本以最高打开率恢复有关投放的信息，并将内容复制到最终投放。

## 脚本示例 {#example-of-a-script}

以下脚本可以像在定位工作流中一样使用。 如需详细信息，请参阅[此部分](#implementation)。

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

有关脚本的详细说明，请参阅[此部分](#details-of-the-script)。

## 实施 {#implementation}

1. 打开&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动。
1. 将[脚本示例](#example-of-a-script)中提供的脚本复制到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;窗口中。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中，输入脚本的名称，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 关闭&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动。
1. 保存工作流。

## 脚本的详细信息 {#details-of-the-script}

本节详细介绍脚本的各个部分及其操作模式。

* 脚本的第一部分是查询。 通过&#x200B;**queryDef**&#x200B;命令，您可以从&#x200B;**NmsDelivery**&#x200B;表中恢复通过执行定向工作流创建的投放，并根据其估计的打开率对其进行排序，然后恢复来自具有最高打开率的投放的信息。

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

* 具有最高打开率的投放会重复显示。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 修改了复制投放的标签，并将单词&#x200B;**final**&#x200B;添加到该标签中。

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 投放会复制到营销活动仪表板中。

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

## 其他选择标准 {#other-selection-criteria}

通过以上示例，您可以根据电子邮件的打开率选择投放的内容。 您可以根据其他特定于投放的指标来调整它：

* 最佳点击吞吐量：`[indicators/@recipientClickRatio]`,
* 最高反应率（电子邮件打开和在消息中点击）：`[indicators/@reactivity]`,
* 最低投诉率：`[indicators/@refusedRatio]`（对sortDesc属性使用false值）、
* 最高转化率：`[indicators/@transactionRatio]`,
* 收到消息后访问的页数：`[indicators/@totalWebPage]`,
* 退订率最低：`[indicators/@optOutRatio]`,
* 交易金额：`[indicators/@amount]`。

您现在可以定义最终投放。 [了解详情](a-b-testing-uc-final-delivery.md)。
