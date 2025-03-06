---
product: campaign
title: 查询投放信息
description: 了解如何查询投放信息
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: b699b064-1287-41c9-8d94-1c1aa2c145ab
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 1%

---

# 查询投放信息 {#querying-delivery-information}



## 特定投放的点击次数 {#number-of-clicks-for-a-specific-delivery}

在本例中，我们将恢复特定投放的点击数。 这些点击量会根据给定时间段内的收件人跟踪日志进行记录。 收件人通过其电子邮件地址进行标识。 此查询使用&#x200B;**[!UICONTROL Recipient tracking logs]**&#x200B;表。

* 需要选择哪个表？

  收件人日志跟踪表(**[!UICONTROL nms:trackingLogRcp]**)

* 要为输出列选择的字段？

  主键（含计数）和电子邮件

* 信息过滤依据什么标准？

  投放标签的特定期间和元素

要执行此示例，请应用以下步骤：

1. 打开&#x200B;**[!UICONTROL Generic query editor]**&#x200B;并选择&#x200B;**[!UICONTROL Recipient tracking logs]**&#x200B;架构。

   ![](assets/query_editor_tracklog_05.png)

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，我们要创建一个聚合以收集信息。 为此，请添加主键（位于主&#x200B;**[!UICONTROL Recipient tracking logs]**&#x200B;元素上方）：对此&#x200B;**[!UICONTROL Primary key]**&#x200B;字段执行跟踪日志计数。 编辑后的表达式将为&#x200B;**[!UICONTROL x=count(primary key)]**。 它将各种跟踪日志的总和链接到单个电子邮件地址。

   操作步骤：

   * 单击&#x200B;**[!UICONTROL Output columns]**&#x200B;字段右侧的&#x200B;**[!UICONTROL Add]**&#x200B;图标。 在&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Edit the formula using an expression]**&#x200B;选项并单击&#x200B;**[!UICONTROL Next]**。 在&#x200B;**[!UICONTROL Field to select]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Advanced selection]**。

     ![](assets/query_editor_tracklog_06.png)

   * 在&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口中，对聚合函数运行进程。 此过程将为主键计数。

     在&#x200B;**[!UICONTROL Aggregate]**&#x200B;部分中选择&#x200B;**[!UICONTROL Process on an aggregate function]**&#x200B;并单击&#x200B;**[!UICONTROL Count]**。

     ![](assets/query_editor_nveau_18.png)

     单击 **[!UICONTROL Next]**。

   * 选择&#x200B;**[!UICONTROL Primary key (@id)]**&#x200B;字段。 已配置&#x200B;**[!UICONTROL count (primary key)]**&#x200B;输出列。

     ![](assets/query_editor_nveau_19.png)

1. 选择要显示在输出列中的其他字段。 在&#x200B;**[!UICONTROL Available fields]**&#x200B;列中，打开&#x200B;**[!UICONTROL Recipient]**&#x200B;节点并选择&#x200B;**[!UICONTROL Email]**。 选中&#x200B;**[!UICONTROL Yes]**&#x200B;的&#x200B;**[!UICONTROL Group]**&#x200B;框以按电子邮件地址将跟踪日志分组：此组将每个日志链接到其收件人。

   ![](assets/query_editor_nveau_20.png)

1. 配置列排序，以便最先显示最活跃的收件人（具有最多的跟踪日志）。 检查&#x200B;**[!UICONTROL Descending sort]**&#x200B;列中的&#x200B;**[!UICONTROL Yes]**。

   ![](assets/query_editor_nveau_64.png)

1. 然后，您必须筛选出您感兴趣的日志，即存在时间少于2周并与销售相关投放相关的日志。

   操作步骤：

   * 配置数据筛选。 为此，请选择&#x200B;**[!UICONTROL Filter conditions]**，然后单击&#x200B;**[!UICONTROL Next]**。

     ![](assets/query_editor_nveau_22.png)

   * 在特定投放的给定时间段内恢复跟踪日志。 需要三个过滤条件：两个日期条件，用于将搜索时段设置在当前日期之前的2周和当前日期之前的1天之间；另一个条件，用于将搜索限制到特定投放。

     在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，配置将考虑跟踪日志的开始日期。 单击 **[!UICONTROL Add]**。将显示条件行。 通过单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;函数编辑&#x200B;**[!UICONTROL Expression]**&#x200B;列。 在&#x200B;**[!UICONTROL Field to select]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Date (@logDate)]**。

     ![](assets/query_editor_nveau_23.png)

     选择&#x200B;**[!UICONTROL greater than]**&#x200B;运算符。 在&#x200B;**[!UICONTROL Value]**&#x200B;列中，单击&#x200B;**[!UICONTROL Edit expression]**，然后在&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口中选择&#x200B;**[!UICONTROL Process on dates]**。 最后，在&#x200B;**[!UICONTROL Current date minus n days]**&#x200B;中输入“15”。

     单击 **[!UICONTROL Finish]**。

     ![](assets/query_editor_nveau_24.png)

   * 要选择跟踪日志搜索结束日期，请单击&#x200B;**[!UICONTROL Add]**&#x200B;创建第二个条件。 在&#x200B;**[!UICONTROL Expression]**&#x200B;列中，再次选择&#x200B;**[!UICONTROL Date (@logDate)]**。

     选择&#x200B;**[!UICONTROL less than]**&#x200B;运算符。 在&#x200B;**[!UICONTROL Value]**&#x200B;列中，单击&#x200B;**[!UICONTROL Edit expression]**。 要处理日期，请转到&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口，在&#x200B;**[!UICONTROL Current date minus n days]**&#x200B;中输入“1”。

     单击 **[!UICONTROL Finish]**。

     ![](assets/query_editor_nveau_65.png)

     现在，我们要配置第三个筛选条件，即查询涉及的投放标签。

   * 单击&#x200B;**[!UICONTROL Add]**&#x200B;函数以创建另一个筛选条件。 在&#x200B;**[!UICONTROL Expression]**&#x200B;列中，单击&#x200B;**[!UICONTROL Edit expression]**。 在&#x200B;**[!UICONTROL Field to select]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Delivery]**&#x200B;节点中的&#x200B;**[!UICONTROL Label]**。

     单击 **[!UICONTROL Finish]**。

     ![](assets/query_editor_nveau_66.png)

     查找包含“sales”一词的投放。 由于您不记得其确切标签，因此可以选择&#x200B;**[!UICONTROL contains]**&#x200B;运算符并在&#x200B;**[!UICONTROL Value]**&#x200B;列中输入“sales”。

     ![](assets/query_editor_nveau_25.png)

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;直到进入&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口：此处不需要格式化。
1. 在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;以查看每个投放收件人的跟踪日志数。

   结果按降序显示。

   ![](assets/query_editor_tracklog_04.png)

   对于此投放，用户的最大日志数为6。 5个不同的用户打开了投放电子邮件或单击了电子邮件中的某个链接。

## 未打开任何投放的收件人 {#recipients-who-did-not-open-any-delivery}

在本例中，我们要筛选过去7天内未打开电子邮件的收件人。

要创建此示例，请应用以下步骤：

1. 在工作流中拖放&#x200B;**[!UICONTROL Query]**&#x200B;活动并打开该活动。
1. 单击&#x200B;**[!UICONTROL Edit query]**&#x200B;并将目标和筛选维度设置为&#x200B;**[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 选择&#x200B;**[!UICONTROL Filtering conditions]**，然后单击&#x200B;**[!UICONTROL Next]**。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择&#x200B;**[!UICONTROL Tracking logs]**。
1. 将&#x200B;**[!UICONTROL Tracking logs]**&#x200B;表达式的&#x200B;**[!UICONTROL Operator]**&#x200B;设置为&#x200B;**[!UICONTROL Do not exist such as]**。

   ![](assets/query_open_1.png)

1. 添加另一个表达式。 选择&#x200B;**[!UICONTROL URL]**&#x200B;类别中的&#x200B;**[!UICONTROL Type]**。
1. 然后，将其&#x200B;**[!UICONTROL Operator]**&#x200B;设置为&#x200B;**[!UICONTROL equal to]**，将其&#x200B;**[!UICONTROL Value]**&#x200B;设置为&#x200B;**[!UICONTROL Open]**。

   ![](assets/query_open_2.png)

1. 添加另一个表达式并选择&#x200B;**[!UICONTROL Date]**。 **[!UICONTROL Operator]**&#x200B;应设置为&#x200B;**[!UICONTROL on or after]**。

   ![](assets/query_open_3.png)

1. 若要设置该值最近7天，请单击&#x200B;**[!UICONTROL Value]**&#x200B;字段中的&#x200B;**[!UICONTROL Edit expression]**&#x200B;按钮。
1. 在&#x200B;**[!UICONTROL Function]**&#x200B;类别中，选择&#x200B;**[!UICONTROL Current date minus n days]**&#x200B;并添加要定位的天数。 这里，我们要定位过去7天。

   ![](assets/query_open_4.png)

叫客过渡将包含过去7天内未打开电子邮件的收件人。

相反，如果您希望筛选至少打开了一封电子邮件的收件人，则您的查询应如下所示。 请注意，在这种情况下，**[!UICONTROL Filtering dimension]**&#x200B;应设置为&#x200B;**[!UICONTROL Tracking logs (Recipients)]**。

![](assets/query_open_5.png)

## 已打开投放的收件人 {#recipients-who-have-opened-a-delivery}

以下示例显示如何定向最近2周内打开过投放的用户档案：

1. 要定位已打开投放的用户档案，您需要使用跟踪日志。 它们存储在链接表中：首先在&#x200B;**[!UICONTROL Filtering dimension]**&#x200B;字段的下拉列表中选择此表，如下所示：

   ![](assets/s_advuser_query_sample1.0.png)

1. 有关筛选条件，请单击跟踪日志的子树结构中显示的条件的&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标。 选择&#x200B;**[!UICONTROL Date]**&#x200B;字段。

   ![](assets/s_advuser_query_sample1.1.png)

   单击&#x200B;**[!UICONTROL Finish]**&#x200B;确认选择。

   要仅恢复两周前的跟踪日志，请选择&#x200B;**[!UICONTROL Greater than]**&#x200B;运算符。

   ![](assets/s_advuser_query_sample1.4.png)

   然后单击&#x200B;**[!UICONTROL Value]**&#x200B;列中的&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标以定义要应用的计算公式。 选择&#x200B;**[!UICONTROL Current date minus n days]**&#x200B;公式并在相关字段中输入15。

   ![](assets/s_advuser_query_sample1.5.png)

   单击公式窗口的&#x200B;**[!UICONTROL Finish]**&#x200B;按钮。 在筛选窗口中，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以检查定位条件。

   ![](assets/s_advuser_query_sample1.6.png)

## 过滤投放后的收件人行为 {#filtering-recipients--behavior-folllowing-a-delivery}

在工作流中，**[!UICONTROL Query]**&#x200B;和&#x200B;**[!UICONTROL Split]**&#x200B;框允许您选择上一次投放后的行为。 此选择是通过&#x200B;**[!UICONTROL Delivery recipient]**&#x200B;筛选器执行的。

* 示例的目的

  在投放工作流中，有几种方法可跟进第一个电子邮件通信。 此类操作涉及使用&#x200B;**[!UICONTROL Split]**&#x200B;框。

* 上下文

  发送“夏季体育优惠”投放。 投放四天后，将发送其他两个投放。 其中一个是“水上运动优惠”，另一个是第一个“夏季运动优惠”的后续服务。

  “水上运动选件”投放会发送给在第一次投放中单击“水上运动”链接的收件人。 这些点击显示收件人对该主题感兴趣。 有必要引导他们接受类似的提议。 但是，未点击“夏季体育优惠”的收件人将再次收到相同的内容。

以下步骤说明了如何通过集成两种不同的行为来配置&#x200B;**[!UICONTROL Split]**&#x200B;框：

1. 将&#x200B;**[!UICONTROL Split]**&#x200B;框插入工作流。 此框将第一个投放的收件人划分为接下来的两个投放。 在首次投放期间，根据与收件人行为关联的筛选条件发生细分。

   ![](assets/query_editor_ex_09.png)

1. 打开&#x200B;**[!UICONTROL Split]**&#x200B;框。 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，为实例输入标签： **根据行为拆分**。

   ![](assets/query_editor_ex_04.png)

1. 在&#x200B;**[!UICONTROL Subsets]**&#x200B;选项卡中，定义第一个拆分分支。 例如，输入此分支的&#x200B;**Clicked**&#x200B;标签。
1. 选择&#x200B;**[!UICONTROL Add a filtering condition on the incoming population]**&#x200B;选项。 单击 **[!UICONTROL Edit]**。
1. 在&#x200B;**[!UICONTROL Targeting and filtering dimension]**&#x200B;窗口中，双击&#x200B;**[!UICONTROL Recipients of a delivery]**&#x200B;筛选器。

   ![](assets/query_editor_ex_05.png)

1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，选择要应用于此分支的行为： **[!UICONTROL Recipients having clicked (email)]**。

   在下方选择&#x200B;**[!UICONTROL Delivery specified by the transition]**&#x200B;选项。 此功能将在首次投放期间自动恢复目标人员。

   这是“水上运动选件”交付。

   ![](assets/query_editor_ex_08.png)

1. 定义第二个分支。 此分支将包括跟进电子邮件，其内容与首次投放的内容相同。 转到&#x200B;**[!UICONTROL Subsets]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;以创建它。

   ![](assets/query_editor_ex_06.png)

1. 将显示另一个子选项卡。 将其命名为“**未单击**”。
1. 单击 **[!UICONTROL Add a filtering condition for the incoming population]**。然后单击 **[!UICONTROL Edit...]**。

   ![](assets/query_editor_ex_07.png)

1. 在&#x200B;**[!UICONTROL Targeting and filtering dimension]**&#x200B;窗口中单击&#x200B;**[!UICONTROL Delivery recipients]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Recipients who did not click (email)]**&#x200B;行为。 为最后一个分支选择所示的&#x200B;**[!UICONTROL Delivery specified by the transition]**&#x200B;选项。

   **[!UICONTROL Split]**&#x200B;框现已完全配置。

   ![](assets/query_editor_ex_03.png)

以下是默认配置的各种组件的列表：

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

  ![](assets/query_editor_ex_02.png)
