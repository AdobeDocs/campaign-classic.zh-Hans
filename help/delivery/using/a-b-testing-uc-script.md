---
product: campaign
title: 创建脚本
description: 了解如何通过专用用例执行A/B测试
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 4%

---

# AB测试：创建脚本 {#step-5--creating-the-script}


由脚本计算预定用于剩余群体的投放内容的选择。 此脚本可恢复有关打开率最高的投放的信息，并将内容复制到最终投放中。

## 脚本示例 {#example-of-a-script}

以下脚本可在定位工作流中按原样使用。 如需详细信息，请参阅[此小节](#implementation)。

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

有关脚本的详细说明，请参阅 [本节](#details-of-the-script).

## 实现 {#implementation}

1. 打开您的 **[!UICONTROL JavaScript code]** 活动。
1. 复制中提供的脚本 [脚本示例](#example-of-a-script) 到 **[!UICONTROL JavaScript code]** 窗口。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在 **[!UICONTROL Label]** 字段中，输入脚本的名称，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 关闭 **[!UICONTROL JavaScript code]** 活动。
1. 保存您的工作流。

## 脚本的详细信息 {#details-of-the-script}

此部分详细介绍脚本的各个部分及其操作模式。

* 脚本的第一部分是查询。 此 **queryDef** 命令允许您从 **NmsDelivery** 对通过执行定位工作流创建的投放进行表，并根据预计的打开率对它们进行排序，然后恢复打开率最高的投放中的信息。

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

* 将复制打开率最高的投放。

  ```
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
  var delivery = nms.delivery.create()
  delivery.Duplicate("nms:delivery|" + winner.@id)
  ```

* 已复制投放的标签已修改，并且单词 **最终** 会添加到其中。

  ```
  // append 'final' to the delivery label
  delivery.label = winner.@label + " final"
  ```

* 投放将会复制到活动仪表板中。

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

* 投放将保存在数据库中。

  ```
  // save the delivery in database
  delivery.save()
  ```

* 重复投放的唯一标识符存储在工作流变量中。

  ```
  // store the new delivery Id in event variables
  vars.deliveryId = delivery.id
  ```

## 其他选择标准 {#other-selection-criteria}

以上示例允许您根据电子邮件打开率选择投放的内容。 您可以根据其他特定于投放的指标对其进行调整：

* 最佳点击吞吐量： `[indicators/@recipientClickRatio]`，
* 最高反应率（电子邮件打开数和邮件点击数）： `[indicators/@reactivity]`，
* 最低投诉率： `[indicators/@refusedRatio]` （对sortDesc属性使用false值），
* 最高转化率： `[indicators/@transactionRatio]`，
* 收到消息后访问的页面数： `[indicators/@totalWebPage]`，
* 最低退订率： `[indicators/@optOutRatio]`，
* 交易金额： `[indicators/@amount]`.

您现在可以定义最终投放。 [了解详情](a-b-testing-uc-final-delivery.md)。
