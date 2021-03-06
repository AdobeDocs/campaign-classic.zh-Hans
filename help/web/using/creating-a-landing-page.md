---
product: campaign
title: 创建登陆页面
description: 创建登陆页面
feature: Landing Pages
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
source-git-commit: 4ff86349d6b8966273585bf2a1ea0d785a7e87cb
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 3%

---

# 创建登陆页面{#creating-a-landing-page}

![](../../assets/common.svg)

## 关于创建登陆页面 {#about-landing-pages-creation}

此用例展示了如何使用数字编辑器从Adobe Campaign控制台创建登陆页面。

在Adobe Campaign中开始配置登陆页面之前，请确保 **一个或多个模板** 来表示HTML页面。

此用例的主要目的是使用DCE中的函数，使登陆页面表单字段与Adobe Campaign中的内部字段相对应。

## 创建登陆页面 {#creating-the-landing-page}

要创建新的登陆页面类型Web应用程序，请执行以下步骤：

1. 转到 **[!UICONTROL Campaigns]** ，然后单击 **[!UICONTROL Web application]** 链接，然后单击 **[!UICONTROL Create]** 按钮。
1. 选择 **[!UICONTROL New landing page]** 模板并输入标签，然后单击 **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. 单击 **[!UICONTROL Edit]** 选项卡。
1. 删除 **结束** 活动。
1. 添加 **[!UICONTROL Page]** 活动之后 **[!UICONTROL Storage]** 活动。
1. 编辑 **第2页** 活动，然后取消选中 **[!UICONTROL Activate outbound transitions]** 选项 **[!UICONTROL Properties]** 选项卡。

   ![](assets/dce_uc1_transition.png)

1. 保存更改。

然后，您将获得以下排序：

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>有关创建Web应用程序的更多信息，请参阅 [此部分](creating-a-new-web-application.md).

## 步骤1 — 选择和加载模板 {#step-1---selecting-and-loading-templates}

在本节中，我们将介绍如何 **导入HTML内容** Web应用程序的每个页面。

模板必须包含：

* an **HTML** 文件（必填）
* 一个或多个 **CSS** 文件（可选）
* 一个或多个 **图像** （可选）

要在第一页上加载模板，请应用以下步骤：

1. 打开第一个 **[!UICONTROL Page]** 活动。
1. 选择 **[!UICONTROL From a file]** 以获取内容模板。

   ![](assets/dce_uc1_selectmodel.png)

1. 选择要使用的HTML文件。
1. 单击 **打开** 以开始导入。

   加载期间，将显示共享文件的列表。 导入系统会检查链接到选定HTML的所有文件（CSS、图像等）是否都存在。

   单击 **[!UICONTROL Close]** 按钮。

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >您必须等到收到以下消息后才能关闭： **[!UICONTROL The external resources have been successfully published]** .

1. 单击 **[!UICONTROL Properties]** 选项卡。
1. 输入 **标签** (例如：第1页=收集，第2页=谢谢)。

   ![](assets/dce_uc1_pagelabel.png)

对Web应用程序中插入的每个页面应用这些步骤。

>[!CAUTION]
>
>**DCE为加载的HTML页面执行JavaScript代码。** HTML模板中可能显示在Adobe Campaign界面中的JavaScript错误。 这些错误与编辑器无关。 要检查导入的文件中是否没有错误，建议先在Web浏览器中测试这些文件，然后再将文件导入DCE。

## 步骤2 — 配置内容 {#step-2---configuring-the-content}

在本节中，我们将调整导入的内容，并将数据库的字段链接到网页的形式。 以前创建的Web应用程序是：

![](assets/dce_uc1_lp_enchainement.png)

### 修改内容 {#modifying-content}

让我们从更改页面的颜色开始。 操作步骤：

1. 打开 **[!UICONTROL Collection]** 页面。
1. 单击背景。
1. 单击 **背景颜色** 在右侧。
1. 选择新的背景颜色。
1. 单击 **确定** 以确认更改。

   ![](assets/dce_uc1_changecolor.png)

1. 应用这些相同的流程以更改按钮的颜色

   ![](assets/dce_uc1_finalcolor.png)

### 链接表单字段 {#linking-form-fields}

为了保存提供的信息，我们将将页面中的字段链接到数据库中的字段。

1. 选择表单字段。
1. 编辑 **[!UICONTROL Field]** 编辑器右侧的部分。
1. 选择要链接到选定字段的数据库字段。

   ![](assets/dce_uc1_mapping.png)

1. 对页面上的每个字段重复此过程。

您可以将字段设为必填字段：例如，单击 **[!UICONTROL Email]** 字段，然后启用 **必需** 选项。

![](assets/dce_uc1_fieldmandatory.png)

### 创建指向下一页的链接 {#creating-a-link-to-the-next-page}

此步骤是强制性的，因为它将允许Web应用程序确定后续步骤的顺序：将收集的数据保存在数据库中，然后显示下一页(**谢谢** 页面)。

1. 选择 **[!UICONTROL Send it!]** 按钮 **[!UICONTROL Collection]** 页面。
1. 单击 **[!UICONTROL Action]** 下拉菜单。
1. 选择 **[!UICONTROL Next page]** 操作。

   ![](assets/dce_uc1_actionbouton.png)

### 插入个性化字段 {#inserting-a-personalization-field}

此步骤允许您个性化“感谢”页面。 操作步骤：

1. 打开 **[!UICONTROL Thank you]** 页面。
1. 将光标放在要插入收件人名字的文本区域中。
1. 选择 **[!UICONTROL Personalization field]** 在 **[!UICONTROL Insert]** 菜单。
1. 选择名字。

   ![](assets/dce_uc1_persochamp.png)

个性化字段在编辑器中的背景为黄色。

![](assets/dce_uc1_edit_champperso.png)

## 步骤3 — 发布内容 {#step-3---publishing-content}

内容从Web应用程序功能板发布。 单击 **[!UICONTROL Publish]** 按钮来运行它。

![](assets/dce_uc1_pub_dashboard.png)

在发布期间，会显示日志。 发布系统分析Web应用程序中找到的所有内容

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>在发布日志中，警告和错误按活动排序。

表单现已可用：其URL可在应用程序功能板中访问，并可发送给收件人。
