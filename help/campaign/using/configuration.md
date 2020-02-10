---
title: 配置
seo-title: 配置
description: 配置
seo-description: null
page-status-flag: never-activated
uuid: 59503b54-ad49-4b00-8ffb-52e6f6c62070
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: ed4afa5e-c184-4c8e-a086-41d87b863190
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 配置{#configuration}

本节面向负责配置响应管理的人员。 它假定了有关扩展架构、定义工作流和SQL编程的一定数量的知识。

这使您能够了解如何使用个人表来调整标准数据模型，使其符合Adobe Campaign外部的事务处理表的特定性质。 此人员表可以与Adobe Campaign中的可用人员表或其他表格保持一致

测量假设由操作过程工作流( **[!UICONTROL operationMgt]** )启动。 每个假设表示以异步方式执行的单独进程（正在编辑、待定、已完成、失败等）由调度器控制，该调度器管理优先级约束、同时进程的数量限制、低活动页面和以频率自动执行。

## 配置架构 {#configuring-schemas}

>[!CAUTION]
>
>请勿修改应用程序的标准架构，而应使用架构扩展机制。 否则，在应用程序将来升级时，修改的架构将不会更新。 这可能导致在使用Adobe Campaign时出现故障。

在使用反应模块之前，需要应用程序集成，以定义要测量的各种表（事务、交易详细信息）及其与交付、优惠和个人的关系。

### 标准架构 {#standard-schemas}

现成模式包含 **[!UICONTROL nms:remaMatch]** 反应日志表，即个体、假设和事务表之间的关系。 此模式将用作响应日志的最终目标表的继承模式。

此 **[!UICONTROL nms:remaMatchRcp]** 架构也作为标准提供，它包含Adobe Campaign收件人的响应日志存储( **[!UICONTROL nms:recipient]** )。 为了使用，需要将其扩展以映射到事务表（包含购买等）。

### 事务表和事务详细信息 {#transaction-tables-and-transaction-details}

事务表必须包含指向个人的直接链接。

您还可以添加包含事务详细信息的表。 这并不直接与个人相关。

例如，如果我们以收款为例，则事务处理表会链接到联系人（收款表），而收款行表仅会链接到收款表（明细表）。 然后，您可以直接在接收行表与接收表链接的层配置假设。

>[!NOTE]
>
>如果要保留描述假设中预期行为的接收标识符，则可以扩展nms:remaMatchRcp表模板以向其添加标识符（在本例中，不将ROI计算链接到这些字段）。

我们强烈建议添加活动日期。

完成配置后，以下架构将显示不同表之间的连接：

![](assets/response_data_model.png)

### 使用Adobe Campaign收件人进行响应管理 {#response-management-with-adobe-campaign-recipients}

在此示例中，我们将使用Adobe Campaign收件人表( **[!UICONTROL nms:recipient]** )在响应管理模块中集成购买表。

对收件人上的响应日志表进 **[!UICONTROL nms:remaMatchRcp]** 行扩展，以添加指向购买表模式的链接。 在以下示例中，购买表称为 **demo:purchase**。

1. 通过Adobe Campaign资源管理器，选择 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**。
1. 右键单击“收 **件人** ”，然后选 **[!UICONTROL Actions]** 择和 **[!UICONTROL Modify the options of the targeting dimensions]**。

   ![](assets/delivery_mapping1.png)

1. 您可以在下一个窗 **[!UICONTROL Extension namespace]** 口中对其进行个性化设置，然后单击 **[!UICONTROL Next]**。

   ![](assets/delivery_mapping2.png)

1. 在类 **[!UICONTROL Response management]** 别中，确保选中 **[!UICONTROL Generate a storage schema for reactions]** 该框。

   然后单 **[!UICONTROL Define additional fields...]** 击以选择相关的事务表，并将所需字段添加到nms:remaMatchRcp架构的扩展中。

   ![](assets/delivery_mapping3.png)

创建的架构如下所示：

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

### 具有个性化收件人表的响应管理 {#response-management-with-a-personalized-recipient-table}

在此示例中，我们将使用除Adobe Campaign中提供的收件人表之外的其他人员表，在响应管理模块中集成购买表。

* 创建从架构派生的新响应日志 **[!UICONTROL nms:remaMatch]** 架构。

   由于个人表与Adobe Campaign收件人表不同，因此必须基于此架构创建响应日志的新架 **[!UICONTROL nms:remaMatch]** 构。 然后，填写它，并提供指向交付日志和购买表的链接。

   在以下示例中，我们将使用 **demo:broadLogPers架构和** demo:purchase事务表 **** :

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

* 修改架构中的假设 **[!UICONTROL nms:remaHypothesis]** 表单。

   默认情况下，响应日志列表显示在收件人日志中。 因此，您必须修改假设表单才能查看在上一步中创建的新响应日志。

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

响应管理器模块附带预定义指示符列表。 但是，您可以添加其他个性化的衡量指标。

为此，必须为每个新指示符插入两个字段来扩展假设表：

* 第一个是目标人群，
* 第二个是控制组。

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

