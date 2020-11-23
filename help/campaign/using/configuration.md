---
solution: Campaign Classic
product: campaign
title: 配置
description: 配置
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# 配置{#configuration}

本节面向负责配置响应管理的人员。 它假定有关扩展模式、定义工作流和SQL编程的一定知识。

这使您能够了解如何使标准数据模型适应与个人表Adobe Campaign外的事务处理表的特定性质。 此个人表可以与Adobe Campaign的可用个人表或不同的表重合

度量假设验证由操作流程工作流( **[!UICONTROL operationMgt]** )启动。 每个假设验证代表一个以执行状态（正在编辑、挂起、完成、失败等）异步执行的单独进程 由调度程序控制，该活动管理优先级约束、同时处理数量限制、低页以及频率自动执行。

## 配置模式 {#configuring-schemas}

>[!CAUTION]
>
>请勿修改应用程序的标准模式，而应使用模式扩展机制。 否则，在应用程序将来升级时，将不更新修改的模式。 这可能导致在使用Adobe Campaign时出现故障。

在使用反应模块之前，需要应用程序集成，以定义要测量的各种表（事务、事务详细信息）及其与投放、优惠和个人的关系。

### 标准模式 {#standard-schemas}

现成的模式包 **[!UICONTROL nms:remaMatch]** 含反应日志表，即个人、假设验证和事务表之间的关系。 此模式应用作反应日志最终目的表的继承模式。

模式 **[!UICONTROL nms:remaMatchRcp]** 也作为标准，它包含Adobe Campaign收件人的反应日志存储( **[!UICONTROL nms:recipient]** )。 为了使用，需要将其扩展以映射到事务表（包含购买等）。

### 事务表和事务详细信息 {#transaction-tables-and-transaction-details}

事务表必须包含指向个人的直接链接。

您还可以添加包含事务详细信息的表。 这不直接与个人相关。

以收款为例，事务处理表链接到联系人（收款表），收款行表仅链接到收款表（明细表）。 然后，您可以直接在收款行表链接至收款表的层配置假设验证。

>[!NOTE]
>
>如果要保留描述假设验证中预期行为的接收标识符，可扩展nms:remaMatchRcp表模板以向其添加标识符（在这种情况下，没有将ROI计算链接到这些字段）。

我们强烈建议添加事件日期。

完成配置后，以下模式显示不同表之间的连接：

![](assets/response_data_model.png)

### 利用Adobe Campaign收件人进行响应管理 {#response-management-with-adobe-campaign-recipients}

在此示例中，我们将使用Adobe Campaign收件人表()在响应管理模块中集成购买表。 **[!UICONTROL nms:recipient]**

收件人上的响应日志 **[!UICONTROL nms:remaMatchRcp]** 表经过扩展以添加指向购买表模式的链接。 在以下示例中，购买表称 **为demo:purchase**。

1. 通过Adobe Campaign浏览器，选择 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**。
1. 右键单击 **收件人** ，然后选 **[!UICONTROL Actions]** 择并 **[!UICONTROL Modify the options of the targeting dimensions]**。

   ![](assets/delivery_mapping1.png)

1. 您可以在下一个窗 **[!UICONTROL Extension namespace]** 口中对其进行个性化设置，然后单击 **[!UICONTROL Next]**。

   ![](assets/delivery_mapping2.png)

1. 在类别 **[!UICONTROL Response management]** 中，确保选中 **[!UICONTROL Generate a storage schema for reactions]** 该框。

   然后单 **[!UICONTROL Define additional fields...]** 击以选择相关的事务表，并将所需字段添加到nms:remaMatchRcp模式的扩展。

   ![](assets/delivery_mapping3.png)

创建的模式如下所示：

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### 通过个性化的收件人表进行响应管理 {#response-management-with-a-personalized-recipient-table}

在此示例中，我们将使用除Adobe Campaign中提供的收件人表之外的其他个人表，在响应管理模块中集成购买表。

* 创建从模式派生的新响应日志 **[!UICONTROL nms:remaMatch]** 模式。

   由于个人表与Adobe Campaign收件人表不同，因此有必要根据模式创建响应日志的新模式 **[!UICONTROL nms:remaMatch]** 。 然后，使用指向投放日志和购买表的链接完成该操作。

   在以下示例中，我们将使 **用demo:broadLogPers** 模式和 **demo:purchase事务表** :

   ```
   <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
   img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
     <element name="remaMatchPers" template="nms:remaMatch">
       <key internal="true" name="match">
         <keyfield xlink="hypothesis"/>
        <keyfield xlink="purchase"/>
       </key>
   
       <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
       <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
                target="demo:propositionPers" type="link"/>
       <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
     </element>
   </srcSchema>
   ```

* 在假设验证中修改模式表 **[!UICONTROL nms:remaHypothesis]** 单。

   默认情况下，响应日志的列表显示在收件人日志中。 因此，您必须修改假设验证表单，以视图在上一步中创建的新响应日志。

   例如：

   ```
    <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                 <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                  toolbarCaption="Responses generated by the hypothesis" type="linklist"
                  xpath="remaMatchPers">
             <input xpath="[.]"/>
             <input xpath="@controlGroup"/>
           </input>
      </container> 
   ```

## 管理指示器 {#managing-indicators}

响应管理器模块附带一列表预定义指示符。 但是，您可以添加其他个性化的衡量指标。

为此，必须通过为每个新指示符插入两个字段来扩展假设验证表：

* 对目标来说，
* 第二个对照组。

例如：

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```

