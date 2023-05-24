---
product: campaign
title: 投放
description: 了解有关投放类型工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# 投放{#delivery}



A **投放**-type活动允许您创建投放操作。 它可以使用输入元素来构建。

要对其进行配置，请编辑活动并输入交付选项。

![](assets/edit_diffusion.png)

1. **投放**

   您可以：

   * 对集客过渡中指定的投放执行操作。 要实现此目的，请选择 **[!UICONTROL Delivery]** 部分。

      当之前的工作流活动已创建或指定投放时，可以使用此选项。 可以像下面的示例一样，由已生成叫客过渡的相同类型的活动执行此操作。

      在以下示例中，首次创建了投放。 群体和内容稍后定义。 接下来，使用集客过渡将这三个元素的信息重新输入到新的投放活动中，以便发送该信息。

      ![](assets/specified_transition_option_exemple.png)

   * 直接选择相关的投放。 要执行此操作，请选择 **[!UICONTROL Explicit]** 选项并从的下拉列表中选择投放 **[!UICONTROL Delivery]** 字段。

      该列表显示了中包含的未完成投放 **投放** 默认文件夹。 要访问其他营销活动，请单击 **[!UICONTROL Select link]** 图标。

      ![](assets/diffusion_edit_1.png)

      从的下拉列表中选择营销活动 **[!UICONTROL Folder]** 字段，或单击 **[!UICONTROL Display sub-levels]** 显示子文件夹中包含的所有投放：

      ![](assets/diffusion_edit_2.png)

      选择投放操作后，您可以通过单击 **[!UICONTROL Edit link]** 图标。

   * 创建脚本以计算投放。 要执行此操作，请选择 **[!UICONTROL Computed by a script]** 选项并输入脚本。 您可以通过单击 **[!UICONTROL Edit...]** 选项。 以下示例可恢复投放的标识符：

      ![](assets/diffusion_edit_3.png)

   * 创建新投放。 要执行此操作，请选择 **[!UICONTROL New, created from a template]** 选项并选择投放所基于的投放模板。

      ![](assets/diffusion_edit_4.png)

      单击 **[!UICONTROL Select link]** 图标浏览文件夹，然后单击 **[!UICONTROL Edit link]** 图标（如果您要查看所选模板的内容）。

1. **收件人**

   收件人可由集客事件指定（例如，在文件导入后），或在投放操作中指定。 它们也可以存储在一个或多个文件中。

   ![](assets/diffusion_edit_5.png)

1. **内容**

   消息的内容可以在投放或集客事件中定义。

   ![](assets/diffusion_edit_6.png)

1. **要执行的操作**

   您可以创建投放、准备投放、启动投放、评估目标或发送校样。

   ![](assets/diffusion_edit_7.png)

   选择要执行的操作类型：

   * **[!UICONTROL Save]**：利用此选项可创建并保存投放。 它不会分析或提供它。
   * **[!UICONTROL Estimate the target]**：利用此选项，可计算投放目标以评估其潜力（第一个分析阶段）。 此操作等同于选择 **[!UICONTROL Estimate the population to be targeted]** 选项并单击 **[!UICONTROL Analyze]** 通过以下方式将投放发送到主目标时 **投放**.
   * **[!UICONTROL Prepare]**：利用此选项可运行完整分析过程（目标计算和内容准备）。 投放未发送。 此操作等同于选择 **[!UICONTROL Deliver as soon as possible]** 选项并单击 **[!UICONTROL Analyze]** 使用将投放发送到主目标时 **投放**.
   * **[!UICONTROL Send a proof]**：利用此选项，可发送投放的证明。 此操作等同于单击 **[!UICONTROL Send a proof]** 使用进行投放的工具栏中的按钮 **投放**
   * **[!UICONTROL Prepare and start]**：此选项启动完整分析过程（目标计算和内容准备）并发送投放。 此操作等同于单击 **[!UICONTROL Deliver as soon as possible]**， **[!UICONTROL Analyze]**、和 **[!UICONTROL Confirm delivery]** 使用将投放发送到主目标时的选项 **投放**.

   此 **[!UICONTROL Act on a delivery]** 在工作流中继续使用的活动允许您启动启动投放所需的所有剩余步骤（目标计算、内容准备、投放）。 有关更多信息，请参阅 [投放控制](delivery-control.md).

   以下选项也可用：

   * **[!UICONTROL Generate an outbound transition]**

      创建将在执行结束时激活的叫客过渡。 您可以选择是否检索出站投放的目标。

   * **[!UICONTROL Do not recover target]**

      不恢复传出投放操作的目标。

   * **[!UICONTROL Processing errors]**

      请参阅 [投放控制](delivery-control.md).
   此 **脚本** 选项卡可让您修改投放参数。

   ![](assets/edit_diffusion_fil_script.png)

## 示例：投放工作流 {#example--delivery-workflow}

创建新工作流并添加活动，如下图所示：

![](assets/new-workflow-5.png)

打开 **投放** 活动并定义属性，如下所示：

* 在 **[!UICONTROL Delivery]** 部分，选择 **[!UICONTROL New, created from a template]** 并选择投放模板。
* 在 **[!UICONTROL Recipients]** 部分，选择 **[!UICONTROL Specified in the delivery]**.
* 在 **[!UICONTROL Action to execute]** 部分，保留 **[!UICONTROL Prepare]** 选项。

![](assets/new-workflow-param-delivery.png)

单击 **[!UICONTROL OK]** 以关闭属性窗口。 您刚刚配置了一个活动，该活动包括根据将在其中指定目标的投放模板创建和准备新投放。

打开 **批准** 活动并定义属性，如下所示：

1. 在 **[!UICONTROL Assignment type]** 字段中，选择注册所在的组。 如果您是使用“管理员”帐户连接的，请选择“管理”组。
1. 接下来，输入标题，并在消息正文中插入以下文本：

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   此消息包含使用JavaScript编写的表达式： **[!UICONTROL vars.recCount]** 表示投放前一个任务所针对的收件人数量。 有关JavaScript表达式的详细信息，请参阅 [JavaScript脚本和模板](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   有关批准任务的详情，请参见 [批准](approval.md).

## 输入参数 {#input-parameters}

投放标识符，如果 **[!UICONTROL Specified in the transition]** 选项已选中 **[!UICONTROL Delivery]** 部分。

* deliveryId
* 表名
* 架构

每个入站事件都必须指定由这些参数定义的目标。

>[!NOTE]
>
>此参数仅在 **[!UICONTROL Specified by inbound event(s)]** 选项已选中 **[!UICONTROL Recipients]** 部分。

* 文件名

   在以下情况下生成的文件的全名： **[!UICONTROL File(s) specified by inbound event(s)]** 选项已选中 **[!UICONTROL Recipients]** 部分。

* contentId

   内容标识符，如果 **[!UICONTROL Specified by inbound events]** 选项已选中 **[!UICONTROL Content]** 部分。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识了投放产生的目标。 **[!UICONTROL tableName]** 是存储目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

与补充关联的过渡具有相同的参数。

>[!NOTE]
>
>如果符合以下条件，则没有输出参数 **[!UICONTROL Do not recover target]** 选项。
