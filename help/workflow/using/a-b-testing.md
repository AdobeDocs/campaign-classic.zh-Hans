---
title: A/B测试
seo-title: A/B测试
description: A/B测试
seo-description: null
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# A/B测试{#a-b-testing}

如果您有多个电子邮件发送内容，并且想要了解哪个版本对目标人群的影响最大，您可以将不同版本发送给某些收件人，然后选择成功率最高的版本并将其发送给其他收件人。

在此用例中，我们将通过定位工作流比较两个电子邮件分发内容。 消息和文本在两个分发中都相同：只更改布局。

目标人口分为三类：两个测试组和其余人群。 交付的不同版本将发送给每个测试组。 在传送之后，在收集最佳打开速率的结果之前配置5天的等待期。 随后，最高分的交付内容由脚本恢复并发送到未用作测试组的人群。

请注意，将决定哪个交付最好的标准可能会根据您的需求而更改。 它可以是开放率、点击率、订阅率、反应性等。

此外，此用例中详细介绍的测试只涉及两个交付，但您可以测试所需数量的版本。 只需向工作流中添加活动即可。

要创建A/B测试，请应用以下步骤：

* [第1步：创建定位工作流](#step-1--creating-a-targeting-workflow)
* [第2步：配置人口示例](#step-2--configuring-population-samples)
* [第3步：创建两个交付模板](#step-3--creating-two-delivery-templates)
* [第4步：在工作流中配置提交](#step-4--configuring-the-deliveries-in-the-workflow)
* [第5步：创建脚本](#step-5--creating-the-script)
* [第7步：启动工作流](#step-7--starting-the-workflow)
* [第8步：分析结果](#step-8--analyzing-the-result)。

## 第1步：创建定位工作流 {#step-1--creating-a-targeting-workflow}

您需要在营销活动的选项卡 **[!UICONTROL Targeting and Workflows]** 中创建工作流。 它由活动、链 **[!UICONTROL Query]** 接到两个活 **[!UICONTROL Split]** 动的活动、活动、活 **[!UICONTROL Email delivery]** 动、活 **[!UICONTROL Wait]** 动和活动组成 **[!UICONTROL JavaScript code]****[!UICONTROL Delivery]** 。

1. 如果尚未创建营销活动，请创建营销活动(有关详细信息，请参阅此 [部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 转到选 **[!UICONTROL Targeting and Workflows]** 项卡。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改现有工作流的标签或单击以 **[!UICONTROL Add]** 创建新工作流(有关详细信息，请参阅此部 [分](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population))。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用鼠标将活动拖放到工作流中，包括 **[!UICONTROL Query]** (**[!UICONTROL Target]** 标签)、 **[!UICONTROL Split]** （标签）、两个&#x200B;**[!UICONTROL Target]** （标签）、活动（标签）、活动（标签）、 **[!UICONTROL Email deliveries]****[!UICONTROL Deliveries]****[!UICONTROL Wait]****[!UICONTROL Flow Control]****[!UICONTROL JavaScript code]****[!UICONTROL Actions]****[!UICONTROL Delivery]****[!UICONTROL Actions]** 活动（标签）、活动（标签）和活动（标签）。

![](assets/use_case_abtesting_targetwkfl_004.png)

## 第2步：配置人口示例 {#step-2--configuring-population-samples}

### 配置查询活动 {#configuring-the-query-activity}

* 双击活 **[!UICONTROL Query]** 动。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击链 **[!UICONTROL Edit query]** 接，然后选择要定位的收件人。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 将活动 **[!UICONTROL Query]** 链接到活 **[!UICONTROL Split]** 动。

   ![](assets/use_case_abtesting_createrecipients_003.png)

### 配置拆分活动 {#configuring-the-split-activity}

此活动允许您创建多个人群：接收递送A的那个，接收递送B的那个，以及剩余的人口。 使用随机选择，您只能瞄准每个递送的一部分人群。

1. 创建人口A:

   * 双击活 **[!UICONTROL Split]** 动。

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在现有选项卡中，将标签更改为填充A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 选择选 **[!UICONTROL Limit the selected records]** 项。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 单击链 **[!UICONTROL Edit]** 接，选择 **[!UICONTROL Activate random sampling]**&#x200B;并单击 **[!UICONTROL Next]**。

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 将阈值设置为10%，然后单击 **[!UICONTROL Finish]**。

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 创建人口B:

   * 单击 **[!UICONTROL Add]** 可为人群B创建新选项卡。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 将人口限制为以前的10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余人口：

   * 转到选 **[!UICONTROL General]** 项卡。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Select **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此人群既不包括A也不包括B，然后单 **[!UICONTROL OK]** 击以关闭活动。

      ![](assets/use_case_abtesting_createrecipients_013.png)

## 第3步：创建两个交付模板 {#step-3--creating-two-delivery-templates}

现在，我们要创建两个交付模板。 每个模板都将在链接到该活 **[!UICONTROL Email delivery]** 动的活动中引 **[!UICONTROL Split]** 用。 For more on this, refer to this [section](../../delivery/using/about-templates.md).

1. 转到文件 **[!UICONTROL Resources > Delivery template]** 夹。
1. 复制交 **[!UICONTROL Email]** 付模板。

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. 创建要用于分发A的内容。

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. 重复此过程，为分发B创建一个模板。

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## 第4步：在工作流中配置提交 {#step-4--configuring-the-deliveries-in-the-workflow}

下一步是配置提交。 它们的目标是前一阶段创造的三个群体：第 [2步：配置人口示例](#step-2--configuring-population-samples)。 前两个提交允许您向人群A和人群B发送不同的内容。第三次交货的目的地是既未收到A也未收到B的人口。其内容将由脚本计算，并且与A或B相同，具体取决于打开率最高的一个。 我们需要为第三个交货配置等待期，以了解交货A和B的结果。这就是第三个交付包含活动的 **[!UICONTROL Wait]** 原因。

1. 转到活动 **[!UICONTROL Split]** 并将转移的目标人群A链接到工作流中已有的电子邮件分发。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 双击传送以将其打开。
1. 使用下拉列表，选择传送A的模板。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 单 **[!UICONTROL Continue]** 击查看分发，然后保存。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 将目标为人口B的 **[!UICONTROL Split]** 活动的过渡链接到第二个电子邮件发送。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 打开传送，在传送B中选择模板，然后保存传送。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 将指定给剩余人口的过渡链接到活 **[!UICONTROL Wait]** 动。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 打开 **[!UICONTROL Wait]** 活动并配置5天的等待期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 将活动 **[!UICONTROL Wait]** 链接到活 **[!UICONTROL JavaScript code]** 动。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## 第5步：创建脚本 {#step-5--creating-the-script}

为剩余人群选择的交付内容由脚本计算。 此脚本以最高打开率恢复有关交付的信息，并将内容复制到最终交付中。

### 脚本示例 {#example-of-a-script}

以下脚本可以像在定位工作流程中一样使用。 For more on this, refer to [Implementation](#implementation).

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

有关脚本的详细说明，请参阅 [脚本的详细信息](#details-of-the-script)。

### 实施 {#implementation}

1. 打开您的 **[!UICONTROL JavaScript code]** 活动。
1. 将脚本示例中提 [供的脚本复制到](#example-of-a-script) “窗口 **[!UICONTROL JavaScript code]** ”中。

   ![](assets/use_case_abtesting_configscript_002.png)

1. 在字 **[!UICONTROL Label]** 段中，输入脚本的名称，即

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. 关闭活 **[!UICONTROL JavaScript code]** 动。
1. 保存您的工作流。

### 脚本的详细信息 {#details-of-the-script}

本节详细介绍了脚本的各个部分及其操作模式。

* 脚本的第一部分是查询。 通过 **queryDef** 命令，您可以从 **NmsDelivery** 表中恢复通过执行定位工作流创建的分发，并根据其估计的打开率对它们进行排序，然后恢复来自具有最高打开率的分发的信息。

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

* 打开率最高的交付重复。

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* 将修改复制交付的标签，并将单词 **final** 添加到该标签。

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* 分发会复制到营销活动仪表板中。

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

* 交付保存在数据库中。

   ```
   // save the delivery in database
   delivery.save()
   ```

* 复制交付的唯一标识符存储在工作流变量中。

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### 其他选择条件 {#other-selection-criteria}

通过上面的示例，您可以根据电子邮件打开率选择分发的内容。 您可以根据其他特定交付指标调整它：

* 最佳点击吞吐量： `[indicators/@recipientClickRatio]`,
* 最高反应性率（打开电子邮件并在邮件中单击）: `[indicators/@reactivity]`,
* 最低投诉率：( `[indicators/@refusedRatio]` 对sortDesc属性使用false值),
* 最高转化率： `[indicators/@transactionRatio]`,
* 接收消息后访问的页数： `[indicators/@totalWebPage]`,
* 最低取消订阅率： `[indicators/@optOutRatio]`,
* 事务处理金额： `[indicators/@amount]`.

## 第6步：定义最终交付 {#step-6--defining-the-final-delivery}

创建脚本以选择A/B测试优胜者后，您可以定义最终交付的参数。

1. 将活动 **[!UICONTROL JavaScript code]** 连接到其余活 **[!UICONTROL Delivery]** 动。
1. 打开活 **[!UICONTROL Delivery]** 动。
1. 取消选中 **[!UICONTROL Generate an outbound transition]** 此选项，以完成此活动的工作流。
1. 将其他选项保留为其默认值。

   ![](assets/ab_test_final_delivery.png)

通过准备在转移中指定的交付（通过活动定义），您随后将能够批准它并开始发送，如下一步所述。 **[!UICONTROL Javascript Code]**

## 第7步：启动工作流 {#step-7--starting-the-workflow}

1. 单击 **[!UICONTROL Start]** 工作流。

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. 通过营销活动仪表板批准分发A和B的目标和内容。
1. 确认交付。
1. 等到5天期间结束，了解在交付开始结果后计算的内容。

   ![](assets/use_case_abtesting_startwkfl_002.png)

   在这种情况下，选择了模板B。

1. 确定第三个分发的内容后，批准目标和内容。

## 第8步：分析结果 {#step-8--analyzing-the-result}

发送测试分发后，您可以检查发送给哪些收件人以及他们是否打开。

* 要查找已定位的收件人，请通过营销活动仪表板打开分发，然后单击选 **[!UICONTROL Delivery]** 项卡。

   ![](assets/use_case_abtesting_analysis_001.png)

* 要了解是否已打开交付，请转到选项 **[!UICONTROL Tracking]** 卡。

   ![](assets/use_case_abtesting_analysis_002.png)

* 与其他交付内容进行比较。

   ![](assets/use_case_abtesting_analysis_003.png)

在我们的示例中，交付B的开放率最高。 这意味着内容B将用于最终交付。

![](assets/use_case_abtesting_analysis_004.png)

