---
title: 投放
seo-title: 投放
description: 投放
seo-description: null
page-status-flag: never-activated
uuid: 3a74fd0b-8598-46a0-bf13-cf35db0987d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9fd7122e-22c7-4f9a-a2a4-5de3daaa3c2e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 投放{#delivery}

“交 **付类型**”活动允许您创建交付活动。 它可以使用输入元件来构造。

要进行配置，请编辑活动并输入传送选项。

![](assets/edit_diffusion.png)

1. **投放**

   您可以：

   * 对入站过渡中指定的交付执行操作。 为此，请选择窗口部分的 **[!UICONTROL Delivery]** 第一个选项。

      当以前的工作流活动已创建或指定了交付时，可以使用此选项。 可以像以下示例中一样，通过已生成出站过渡的同一类型的活动执行此操作。

      在以下示例中，首次创建了交付。 稍后将定义人群和内容。 然后，使用入站过渡将这三个元素的信息重新输入到新的交付活动中，以便发送该信息。

      ![](assets/specified_transition_option_exemple.png)

   * 直接选择相关的交付。 为此，请选择选 **[!UICONTROL Explicit]** 项，然后从字段的下拉列表中选择分 **[!UICONTROL Delivery]** 发。

      此列表默认显示“分发”文件夹中包 **含的未完** 成的分发。 要访问其他营销活动，请单击 **[!UICONTROL Select link]** 图标。

      ![](assets/diffusion_edit_1.png)

      从字段的下拉列表中选择营销活动，或 **[!UICONTROL Folder]** 者单击以显示子 **[!UICONTROL Display sub-levels]** 文件夹中包含的所有分发内容：

      ![](assets/diffusion_edit_2.png)

      在选择分发操作后，您可以通过单击图标来显示 **[!UICONTROL Edit link]** 内容。

   * 创建用于计算交付的脚本。 要执行此操作，请选择 **[!UICONTROL Calculated by a script]** 选项并输入脚本。 可以通过单击选项打开输入窗 **[!UICONTROL Edit...]** 口。 以下示例恢复交付的标识符：

      ![](assets/diffusion_edit_3.png)

   * 创建新分发。 为此，请选择选 **[!UICONTROL New, created from a template]** 项并选择传送将基于的传送模板。

      ![](assets/diffusion_edit_4.png)

      单击图 **[!UICONTROL Select link]** 标以浏览文件夹，如果您想 **[!UICONTROL Edit link]** 查看所选模板的内容，请单击该图标。

1. **收件人**

   收件人可以由入站事件指定，例如，在文件导入之后，或在分发操作中指定。 它们也可以存储在一个或多个文件中。

   ![](assets/diffusion_edit_5.png)

1. **内容**

   消息的内容可以在分发或入站事件中定义。

   ![](assets/diffusion_edit_6.png)

1. **要执行的操作**

   您可以创建交付、准备、开始、评估目标或发送证明。

   ![](assets/diffusion_edit_7.png)

   选择要执行的操作类型：

   * **[!UICONTROL Save]**:通过此选项，您可以创建交付并保存它。 它不会分析或提供它。
   * **[!UICONTROL Estimate the target]**:此选项允许您计算交付目标以评估其潜力（第一个分析阶段）。 此操作等效于选择选项， **[!UICONTROL Estimate the population to be targeted]** 并在通过 **[!UICONTROL Analyze]** Delivery将分发发送到主目标时单击 **该选项**。
   * **[!UICONTROL Prepare]**:此选项允许您运行完整的分析过程（目标计算和内容准备）。 送货不送。 此操作等效于选择选项， **[!UICONTROL Deliver as soon as possible]** 并在将分 **[!UICONTROL Analyze]** 发发送到主目标时单 **击**。
   * **[!UICONTROL Send a proof]**:此选项允许您发送交货的证明。 此操作等同于单击包含 **[!UICONTROL Send a proof]** 交付的交付的工具栏中的按 **钮**
   * **[!UICONTROL Prepare and start]**:此选项启动完整的分析过程（目标计算和内容准备）并发送交付。 此操作等同于在将传送发 **[!UICONTROL Deliver as soon as possible]**&#x200B;送到主 **[!UICONTROL Analyze]**&#x200B;目标 **[!UICONTROL Confirm delivery]** 时单击、和选 **项**。
   在工 **[!UICONTROL Act on a delivery]** 作流中进一步使用的活动允许您启动开始交付所需的所有剩余步骤（目标计算、内容准备、交付）。 For more on this, refer to [Delivery control](../../workflow/using/delivery-control.md).

   还提供以下选项：

   * **[!UICONTROL Generate an outbound transition]**

      创建将在执行结束时激活的出站过渡。 您可以选择是否检索出站分发的目标。

   * **[!UICONTROL Do not recover target]**

      不恢复传出交付操作的目标。

   * **[!UICONTROL Processing errors]**

      请参阅 [交付控件](../../workflow/using/delivery-control.md)。
   “脚 **本** ”选项卡允许您修改传送参数。

   ![](assets/edit_diffusion_fil_script.png)

## 示例：交付工作流程 {#example--delivery-workflow}

创建新工作流并添加活动，如下图所示：

![](assets/new-workflow-5.png)

打开“ **交付** ”活动并定义以下属性：

* 在部分 **[!UICONTROL Delivery]** 中，选择 **[!UICONTROL New, created from a template]** 并选择分发模板。
* 在部分 **[!UICONTROL Recipients]** 中，选择 **[!UICONTROL Specified in the delivery]**。
* 在部 **[!UICONTROL Action to execute]** 分中，保留选 **[!UICONTROL Prepare]** 项。

![](assets/new-workflow-param-delivery.png)

单击 **[!UICONTROL OK]** 以关闭属性窗口。 您刚刚配置了一个活动，该活动包括根据将在其中指定目标的交付模板创建和准备新交付。

打开“ **批准** ”活动并定义以下属性：

1. 在字 **[!UICONTROL Assignment type]** 段中，选择您注册的组。 如果您使用“admin”帐户连接，请选择“管理”组。
1. 然后，输入标题，并在邮件正文中插入以下文本：

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   这是一条消息，其中包含用JavaScript编写的表达式：表 **[!UICONTROL vars.recCount]** 示由前一任务的交付所定位的收件人数。 有关JavaScript表达式的详细信息，请参阅 [JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md)。

   ![](assets/new-workflow-param-validation.png)

   批准任务在批准中有详细 [说明](../../workflow/using/approval.md)。

## 输入参数 {#input-parameters}

交付标识符(如果在部 **[!UICONTROL Specified in the transition]** 分中选择了此选项) **[!UICONTROL Delivery]** 。

* deliveryId
* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

>[!NOTE]
>
>此参数仅在部分中选 **[!UICONTROL Specified by inbound event(s)]** 择了该选项时显 **[!UICONTROL Recipients]** 示。

* 文件名

   在部分中选择该选项时生成 **[!UICONTROL File(s) specified by inbound event(s)]** 的文件的完整名 **[!UICONTROL Recipients]** 称。

* contentId

   内容标识符(如 **[!UICONTROL Specified by inbound events]** 果在部分中选择了该 **[!UICONTROL Content]** 选项)。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三个值集标识了由交付生成的目标。 **[!UICONTROL tableName]** 是存储目标标识符的表的名称，是 **[!UICONTROL schema]** 人群（通常是nms:recipient）的模式， **[!UICONTROL recCount]** 是表中元素的数量。

与补码相关联的过渡具有相同的参数。

>[!NOTE]
>
>选中该选项时，没有 **[!UICONTROL Do not recover target]** 输出参数。

