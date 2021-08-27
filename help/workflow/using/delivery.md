---
product: campaign
title: 投放
description: 了解有关投放类型工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# 投放{#delivery}

![](../../assets/common.svg)

**Delivery**&#x200B;类型活动允许您创建投放操作。 它可以使用输入元素来构建。

要对其进行配置，请编辑活动并输入提交选项。

![](assets/edit_diffusion.png)

1. **投放**

   您可以：

   * 对集客过渡中指定的投放执行操作。 要执行此操作，请选择窗口&#x200B;**[!UICONTROL Delivery]**&#x200B;部分的第一个选项。

      当之前的工作流活动已创建或指定投放时，可以使用此选项。 与以下示例一样，也可以通过生成叫客过渡的相同类型的活动来执行此操作。

      在以下示例中，首次创建投放。 稍后会定义群体和内容。 接下来，使用集客过渡将这三个元素的信息重新输入到新投放活动中，以便发送该信息。

      ![](assets/specified_transition_option_exemple.png)

   * 直接选择相关投放。 要执行此操作，请选择&#x200B;**[!UICONTROL Explicit]**&#x200B;选项，然后从&#x200B;**[!UICONTROL Delivery]**&#x200B;字段的下拉列表中选择投放。

      默认情况下，该列表显示&#x200B;**Deliveries**&#x200B;文件夹中包含的未完成投放。 要访问其他营销活动，请单击&#x200B;**[!UICONTROL Select link]**&#x200B;图标。

      ![](assets/diffusion_edit_1.png)

      从&#x200B;**[!UICONTROL Folder]**&#x200B;字段的下拉列表中选择营销活动，或单击&#x200B;**[!UICONTROL Display sub-levels]**&#x200B;以显示子文件夹中包含的所有投放：

      ![](assets/diffusion_edit_2.png)

      选择投放操作后，可以单击&#x200B;**[!UICONTROL Edit link]**&#x200B;图标以显示内容。

   * 创建用于计算投放的脚本。 为此，请选择&#x200B;**[!UICONTROL Computed by a script]**&#x200B;选项并输入脚本。 单击&#x200B;**[!UICONTROL Edit...]**&#x200B;选项可打开输入窗口。 以下示例取回了投放的标识符：

      ![](assets/diffusion_edit_3.png)

   * 创建新投放。 要执行此操作，请选择&#x200B;**[!UICONTROL New, created from a template]**&#x200B;选项，然后选择投放所基于的投放模板。

      ![](assets/diffusion_edit_4.png)

      单击&#x200B;**[!UICONTROL Select link]**&#x200B;图标浏览文件夹，如果要查看所选模板的内容，请单击&#x200B;**[!UICONTROL Edit link]**&#x200B;图标。

1. **收件人**

   收件人可由集客事件指定（例如，在文件导入后），或在投放操作中指定。 它们也可以存储在一个或多个文件中。

   ![](assets/diffusion_edit_5.png)

1. **内容**

   可以在投放或集客事件中定义消息的内容。

   ![](assets/diffusion_edit_6.png)

1. **要执行的操作**

   您可以创建投放、准备投放、启动投放、评估目标或发送校样。

   ![](assets/diffusion_edit_7.png)

   选择要执行的操作类型：

   * **[!UICONTROL Save]**:利用此选项，可创建投放并保存。它不会分析或提交它。
   * **[!UICONTROL Estimate the target]**:利用此选项，可计算投放目标以评估其潜力（第一个分析阶段）。此操作等同于在通过&#x200B;**Delivery**&#x200B;向主目标发送投放时选择&#x200B;**[!UICONTROL Estimate the population to be targeted]**&#x200B;选项并单击&#x200B;**[!UICONTROL Analyze]**。
   * **[!UICONTROL Prepare]**:利用此选项，可运行完整的分析流程（目标计算和内容准备）。未发送投放。 此操作等同于使用&#x200B;**Delivery**&#x200B;将投放发送到主目标时，选择&#x200B;**[!UICONTROL Deliver as soon as possible]**&#x200B;选项并单击&#x200B;**[!UICONTROL Analyze]**。
   * **[!UICONTROL Send a proof]**:利用此选项，可发送投放的校样。此操作等同于单击&#x200B;**Delivery**&#x200B;投放工具栏中的&#x200B;**[!UICONTROL Send a proof]**&#x200B;按钮
   * **[!UICONTROL Prepare and start]**:此选项会启动完整的分析流程（目标计算和内容准备）并发送投放。此操作等同于使用&#x200B;**Delivery**&#x200B;向主目标发送投放时单击&#x200B;**[!UICONTROL Deliver as soon as possible]**、**[!UICONTROL Analyze]**&#x200B;和&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;选项。

   通过工作流中进一步使用的&#x200B;**[!UICONTROL Act on a delivery]**&#x200B;活动，您可以启动开始投放所需的所有其余步骤（目标计算、内容准备、投放）。 有关更多信息，请参阅[投放控制](delivery-control.md)。

   还提供以下选项：

   * **[!UICONTROL Generate an outbound transition]**

      创建将在执行结束时激活的叫客过渡。 您可以选择是否检索叫客投放的目标。

   * **[!UICONTROL Do not recover target]**

      无法恢复传出投放操作的目标。

   * **[!UICONTROL Processing errors]**

      请参阅[传递控件](delivery-control.md)。
   使用&#x200B;**Script**&#x200B;选项卡可修改投放参数。

   ![](assets/edit_diffusion_fil_script.png)

## 示例：投放工作流 {#example--delivery-workflow}

创建新工作流并添加活动，如下图所示：

![](assets/new-workflow-5.png)

打开&#x200B;**Delivery**&#x200B;活动并定义以下属性：

* 在&#x200B;**[!UICONTROL Delivery]**&#x200B;部分中，选择&#x200B;**[!UICONTROL New, created from a template]**&#x200B;并选择投放模板。
* 在&#x200B;**[!UICONTROL Recipients]**&#x200B;部分中，选择&#x200B;**[!UICONTROL Specified in the delivery]**。
* 在&#x200B;**[!UICONTROL Action to execute]**&#x200B;部分中，保留&#x200B;**[!UICONTROL Prepare]**&#x200B;选项。

![](assets/new-workflow-param-delivery.png)

单击&#x200B;**[!UICONTROL OK]**&#x200B;以关闭属性窗口。 您刚刚配置了一个活动，该活动包括根据将在其中指定目标的投放模板创建和准备新投放。

打开&#x200B;**Approval**&#x200B;活动并定义以下属性：

1. 在&#x200B;**[!UICONTROL Assignment type]**&#x200B;字段中，选择您注册的组。 如果您使用“管理员”帐户连接，请选择管理组。
1. 接下来，输入标题并在消息正文中插入以下文本：

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   此消息包括使用JavaScript编写的表达式：**[!UICONTROL vars.recCount]**&#x200B;表示上一任务投放所定向的收件人数。 有关JavaScript表达式的更多信息，请参阅[JavaScript脚本和模板](javascript-scripts-and-templates.md)。

   ![](assets/new-workflow-param-validation.png)

   [Approval](approval.md)中详细说明了“批准”任务。

## 输入参数 {#input-parameters}

投放标识符（如果在&#x200B;**[!UICONTROL Delivery]**&#x200B;部分中选择了&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;选项）。

* deliveryId
* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。

>[!NOTE]
>
>仅当在&#x200B;**[!UICONTROL Recipients]**&#x200B;部分中选择了&#x200B;**[!UICONTROL Specified by inbound event(s)]**&#x200B;选项时，才会显示此参数。

* 文件名

   如果在&#x200B;**[!UICONTROL Recipients]**&#x200B;部分中选择了&#x200B;**[!UICONTROL File(s) specified by inbound event(s)]**&#x200B;选项，则生成的文件的全名。

* contentId

   在&#x200B;**[!UICONTROL Content]**&#x200B;部分中选择了&#x200B;**[!UICONTROL Specified by inbound events]**&#x200B;选项时的内容标识符。

## 输出参数 {#output-parameters}

* tableName
* 模式
* recCount

这三个值集标识由投放生成的目标。 **[!UICONTROL tableName]** 是用于存储目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms:recipient）， **[!UICONTROL recCount]** 是表中元素的数量。

与补码关联的过渡具有相同的参数。

>[!NOTE]
>
>选择&#x200B;**[!UICONTROL Do not recover target]**&#x200B;选项时，没有输出参数。
