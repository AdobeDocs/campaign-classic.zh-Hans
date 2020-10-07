---
title: A/B 测试
seo-title: A/B 测试
description: A/B 测试
seo-description: null
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 2%

---


# A/B 测试{#a-b-testing}

如果电子邮件投放有多个内容，并且想了解哪个版本对目标用户群影响最大，可以将不同版本发送给某些收件人，然后选择成功率最高的版本并发送给其他收件人。

在此用例中，我们将通过定位工作流来比较两个电子邮件投放内容。 消息和文本在两个投放中是相同的：只更改布局。

目标人口分为三个：两个测试组和剩余人口。 投放的不同版本将发送到每个测试组。 在投放之后，在收集最佳打开速率的结果之前配置5天的等待时间。 得分最高的投放的内容随后由脚本恢复，并发送给未用作测试组的人群。

请注意，将决定哪个投放最佳的标准可能会根据您的需要而更改。 可以是开放率、点击率、订阅率、反应性等。

此外，此用例中详细介绍的测试只涉及两个投放，但您可以根据需要测试任意多个版本。 只需向工作流中添加活动。

要创建A/B测试，请应用以下步骤：

* [第1步：创建定位工作流](#step-1--creating-a-targeting-workflow)
* [第2步：配置填充示例](#step-2--configuring-population-samples)
* [第3步：创建两个投放模板](#step-3--creating-two-delivery-templates)
* [第4步：在工作流中配置投放](#step-4--configuring-the-deliveries-in-the-workflow)
* [第5步：创建脚本](#step-5--creating-the-script)
* [第7步：启动工作流](#step-7--starting-the-workflow)
* [第8步：分析结果](#step-8--analyzing-the-result)。

## Step 1: Creating a targeting workflow {#step-1--creating-a-targeting-workflow}

您需要在活动的选项卡中 **[!UICONTROL Targeting and Workflows]** 创建工作流。 它由活动、 **[!UICONTROL Query]** 活动和两个 **[!UICONTROL Split]** 活动、一个 **[!UICONTROL Email delivery]** 活动、一 **[!UICONTROL Wait]** 个活动和一个 **[!UICONTROL JavaScript code]****[!UICONTROL Delivery]** 活动组成。

1. 如果尚未创建活动，请创建此(有关详细信息，请参阅此 [部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 转到 **[!UICONTROL Targeting and Workflows]** 选项卡。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改现有工作流的标签或单 **[!UICONTROL Add]** 击以创建新工作流(有关详细信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population))。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用鼠标将活动拖放到图中，包括 **[!UICONTROL Query]** (**[!UICONTROL Target]** tab)、( **[!UICONTROL Split]** tab)、两个&#x200B;**[!UICONTROL Target]** (tab)、一个活动标签( **[!UICONTROL Email deliveries]** 活动标签)、活动(标签&#x200B;**[!UICONTROL Deliveries]****[!UICONTROL Wait]****[!UICONTROL Flow Control]****[!UICONTROL JavaScript code]****[!UICONTROL Actions]****[!UICONTROL Delivery]****[!UICONTROL Actions]** )、（标签）和（标签）工作流。

![](assets/use_case_abtesting_targetwkfl_004.png)

## 第2步：配置填充示例 {#step-2--configuring-population-samples}

### 配置查询活动 {#configuring-the-query-activity}

* Double-click the **[!UICONTROL Query]** activity.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击链 **[!UICONTROL Edit query]** 接，然后选择要目标的收件人。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 将活动 **[!UICONTROL Query]** 链接到 **[!UICONTROL Split]** 活动。

   ![](assets/use_case_abtesting_createrecipients_003.png)

### 配置拆分活动 {#configuring-the-split-activity}

此活动允许您创建多个人群：接收投放A的投放B，以及剩余人口。 使用随机选择，您只能目标每个投放的一部分人口。

1. 创建人口A:

   * Double-click the **[!UICONTROL Split]** activity.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在现有选项卡中，将标签更改为填充A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 选择选 **[!UICONTROL Limit the selected records]** 项。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 单击链 **[!UICONTROL Edit]** 接，选 **[!UICONTROL Activate random sampling]**&#x200B;择，然后单击 **[!UICONTROL Next]**。

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 将阈值设置为10%，然后单击 **[!UICONTROL Finish]**。

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 创建人口B:

   * 单 **[!UICONTROL Add]** 击可为人口B创建新选项卡。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 将人口限制为以前的10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余人口：

   * 转到 **[!UICONTROL General]** 选项卡。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 选择 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此填充不包括A和B，然后单 **[!UICONTROL OK]** 击以关闭活动。

      ![](assets/use_case_abtesting_createrecipients_013.png)

## 第3步：创建两个投放模板 {#step-3--creating-two-delivery-templates}

我们现在想创建两个投放模板。 每个模板都将在链接到该 **[!UICONTROL Email delivery]** 活动的活动中引 **[!UICONTROL Split]** 用。 有关更多信息，请参阅此](../../delivery/using/about-templates.md)章节[。

1. Go to the **[!UICONTROL Resources > Delivery template]** folder.
1. 重复 **[!UICONTROL Email]** 投放模板。

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. 创建要用于投放A的内容。

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. 重复此过程以为投放B创建模板。

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## 第4步：在工作流中配置投放 {#step-4--configuring-the-deliveries-in-the-workflow}

下一步是配置投放。 它们的目标是前一阶段创造的三个人口： [第2步：配置填充示例](#step-2--configuring-population-samples)。 前两个投放允许您向群体A和B发送不同的内容。第三个投放用于未接收A和B的群体。其内容将由脚本计算，并且与A或B相同，具体取决于打开率最高的群体。 我们需要为第三个投放配置等待期，以了解投放A和B的结果。这就是为什么第三个投放包括 **[!UICONTROL Wait]** 活动。

1. 转到活动 **[!UICONTROL Split]** 并将用于填充A的过渡链接到工作流中已有的电子邮件投放之一。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 多次-单击投放以打开它。
1. 使用下拉列表，选择投放A的模板。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 单 **[!UICONTROL Continue]** 击视图投放，然后保存它。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 将目标为人群B **[!UICONTROL Split]** 的过渡链接到第二个电子邮件投放。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 打开投放，在投放B中选择模板，然后保存投放。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 将用于剩余人口的过渡链接到 **[!UICONTROL Wait]** 活动。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 打开 **[!UICONTROL Wait]** 活动并配置5天的等待期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 将活动 **[!UICONTROL Wait]** 链接到 **[!UICONTROL JavaScript code]** 活动。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## 第5步：创建脚本 {#step-5--creating-the-script}

投放内容的选择将由脚本计算。 此脚本以最高打开率恢复有关投放的信息，并将内容复制到最终投放。

### 脚本示例 {#example-of-a-script}

以下脚本可以像在定位工作流中一样使用。 For more on this, refer to [Implementation](#implementation).

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

有关脚本的详细说明，请参 [阅脚本的详细信息](#details-of-the-script)。

### 实施 {#implementation}

1. 打开 **[!UICONTROL JavaScript code]** 活动。
1. 将脚本示例中提 [供的脚本复制](#example-of-a-script) 到窗口 **[!UICONTROL JavaScript code]** 中。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在字 **[!UICONTROL Label]** 段中，输入脚本的名称，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 关闭 **[!UICONTROL JavaScript code]** 活动。
1. 保存您的工作流。

### 脚本的详细信息 {#details-of-the-script}

本节详细介绍了脚本的各个部分及其操作模式。

* 脚本的第一部分是查询。 使 **用queryDef****** 命令可以从NmsDelivery表中恢复通过执行定位工作流创建的投放，并根据其估计的打开率对它们进行排序，然后恢复来自打开率最高的投放的信息。

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

* 打开率最高的投放重复。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 将修改复制投放的标签，并将词 **final** 添加到该标签。

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 投放被复制到活动仪表板。

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

### 其他选择条件 {#other-selection-criteria}

以上示例允许您根据电子邮件打开率选择投放的内容。 您可以根据其他投放特定指标调整它：

* 最佳点击吞吐量： `[indicators/@recipientClickRatio]`,
* 最高反应率（打开电子邮件并在邮件中单击）: `[indicators/@reactivity]`,
* 最低投诉率： `[indicators/@refusedRatio]` （对sortDesc属性使用false值）,
* 最高转化率: `[indicators/@transactionRatio]`,
* 接收消息后访问的页数： `[indicators/@totalWebPage]`,
* 最低退订率： `[indicators/@optOutRatio]`,
* 交易金额： `[indicators/@amount]`.

## 第6步：定义最终投放 {#step-6--defining-the-final-delivery}

创建脚本以选择A/B测试入选方后，您可以定义最终投放的参数。

1. 将活动 **[!UICONTROL JavaScript code]** 连接到其余的 **[!UICONTROL Delivery]** 活动。
1. 打开 **[!UICONTROL Delivery]** 活动。
1. 取消选中 **[!UICONTROL Generate an outbound transition]** 此选项，以使用此活动完成工作流。
1. 保留其他选项的默认值。

   ![](assets/ab_test_final_delivery.png)

准备在投放中指定的过渡(通过定 **[!UICONTROL Javascript Code]** 义)后，您便可以批准该活动并开始发送，如下一步所述。

## 第7步：启动工作流 {#step-7--starting-the-workflow}

1. 单击 **[!UICONTROL Start]** 工作流。

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. 通过目标仪表板批准投放A和B的活动和内容。
1. 确认投放。
1. 等到5天期间结束，了解在投放开始结果后计算了哪些内容。

   ![](assets/use_case_abtesting_startwkfl_002.png)

   在这种情况下，选择模板B。

1. 确定第三个投放的内容后，批准该目标和该内容。

## 第8步：分析结果 {#step-8--analyzing-the-result}

发送测试投放后，您可以检查已将其发送到的收件人以及是否已打开它们。

* 要了解哪些收件人已成为目标，请通过活动仪表板打开一个投放，然后单击选 **[!UICONTROL Delivery]** 项卡。

   ![](assets/use_case_abtesting_analysis_001.png)

* 要了解投放是否已打开，请转到选项 **[!UICONTROL Tracking]** 卡。

   ![](assets/use_case_abtesting_analysis_002.png)

* 与其他投放比较。

   ![](assets/use_case_abtesting_analysis_003.png)

在我们的例子中，投放B的公开率最高。 这意味着内容B将用于最终投放。

![](assets/use_case_abtesting_analysis_004.png)

