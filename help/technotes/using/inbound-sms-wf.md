---
product: campaign
title: 中间源基础架构的入站短信工作流活动
description: 中间源基础架构的入站短信工作流活动
feature: Technote, SMS
exl-id: 756039b2-5f57-4dc5-8166-a421206b886b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---

# 中间源基础架构的入站短信工作流活动 {#inbound-sms-wf}

## 限制 {#limitations}

* 此用例仅适用于您从中间源实例收集inSMS数据的营销实例。
* 请勿在中间源实例上实施此用例。
* 每个外部中间源帐户只有一个自定义工作流。

## 实现 {#implementation}

1. 向营销实例上的`nms:inSMS`架构添加扩展。 该扩展将向`nms:inSMS`架构添加新属性，并跟踪来自中间源实例的inSMS记录主键。

   ```xml
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. 要应用对架构所做的修改，请启动数据库更新助手。 此助理可通过&#x200B;**工具** > **高级** > **更新数据库结构**&#x200B;访问。 它检查数据库的物理结构是否与其逻辑描述匹配，并执行SQL更新脚本。 [了解详情](../../configuration/using/updating-the-database-structure.md)

1. 停止并备份包含&#x200B;**入站SMS活动**&#x200B;的工作流。

   使用以下格式备份对应的选项指针`SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`。

[了解有关备份的详细信息](../../production/using/backup.md)

1. （**可选**）如果您已在使用调度程序活动，请打开工作流并按如下方式重新配置它：

   1. 将&#x200B;**入站SMS**&#x200B;活动的&#x200B;**计划**&#x200B;选项卡中的当前设置复制到外部&#x200B;**调度程序**&#x200B;活动中。

   1. 在&#x200B;**入站SMS**&#x200B;活动的&#x200B;**计划**&#x200B;选项卡中禁用当前设置。

      ![](assets/inbound_sms_1.png)

1. 更新&#x200B;**入站短信**&#x200B;自定义脚本。

   更换下面的块。 请注意，如果您之前自定义了此代码，则此脚本可能会有所不同。

   ```Javascript
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   使用以下新的自定义脚本，根据复合密钥更新inSMS数据，结合中间源记录的主密钥和营销短信路由的外部帐户ID。

   请遵循以下先决条件：

   * 输入`<EXTERNAL_ACCOUNT_ID>`的实际值，如`var iExtAccountId=72733155`。
   * 确保在自定义脚本中保留以下元素：
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. 使用以下脚本更新入站SMS高级初始化脚本。

   该脚本会将主键指针重置为24小时前的。 该工作流将尝试在之前的24小时内重新处理来自中间源实例的所有inSMS数据，并将任何缺失的数据添加到营销实例。

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * 如果多个SMS路由帐户链接到同一个中间源实例，则仅允许每个中间源实例有一个工作流。
   > * 您可以使用任何外部帐户ID。 外键的职责是在涉及不同中间源服务器的场景中维护数据协调完整性，在这些场景中，中间源SMS ID可能在其他中间源实例中相同。
   > * 如果每个中间源实例有多个inSMS工作流，则可能会发生重复数据删除，因为中间源SMS ID保持不变，而外部帐户ID则有所不同。

1. 保存并重新启动工作流。
