---
solution: Campaign Classic
product: campaign
title: 创建登陆页面
description: 创建登陆页面
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 3%

---


# 创建登陆页面{#creating-a-landing-page}

## 关于登陆页创建 {#about-landing-pages-creation}

此用例说明如何使用数字编辑器从登陆页控制台创建Adobe Campaign。

在开始以Adobe Campaign配置登陆页之前，请 **确保有一个或多个模板** 来表示HTML页面。

此用例的主要目的是使登陆页表单字段与Adobe Campaign中使用数字内容编辑器中的函数的内部字段相对应。

## Creating the landing page {#creating-the-landing-page}

要创建新的登陆页类型Web 应用程序，请执行以下步骤：

1. 转到选项 **[!UICONTROL Campaigns]** 卡并单击链 **[!UICONTROL Web application]** 接，然后单击按 **[!UICONTROL Create]** 钮。
1. 选择模 **[!UICONTROL New landing page]** 板并输入标签，然后单击 **[!UICONTROL Save]**。

   ![](assets/dce_uc1_newlandingpage.png)

1. 单击选 **[!UICONTROL Edit]** 项卡。
1. 删除“ **结束** ”活动。
1. 在活动 **[!UICONTROL Page]** 后添加一个 **[!UICONTROL Storage]** 活动。
1. 编辑第 **2页活动** ，然后取消选中 **[!UICONTROL Activate outbound transitions]** 选项卡中的 **[!UICONTROL Properties]** 选项。

   ![](assets/dce_uc1_transition.png)

1. 保存更改。

然后，您将获得以下排序：

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>有关创建Web 应用程序的详细信息，请参 [阅此部分](../../web/using/creating-a-new-web-application.md)。

## 第1步——选择和加载模板 {#step-1---selecting-and-loading-templates}

本节将介绍如何为Web 应用程序的 **每页** 导入HTML内容。

模板必须包含：

* HTML **文件** （必填）
* 一个或多个 **CSS** 文件（可选）
* 一张或多 **张图像** （可选）

要在第一页上加载模板，请应用以下步骤：

1. 打开活动 **[!UICONTROL Page]** 的第一个Web 应用程序。
1. 选择 **[!UICONTROL From a file]** 以获取您的内容模板。

   ![](assets/dce_uc1_selectmodel.png)

1. 选择要使用的HTML文件。
1. 单击 **打开** ，以开始导入。

   加载过程中，将显示共享文件的列表。 导入系统检查链接到所选HTML的所有文件（CSS、图像等）是否在此处。

   完成导 **[!UICONTROL Close]** 入后，单击按钮。

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >您必须等到收到以下消息后才关闭： **[!UICONTROL The external resources have been successfully published]** .

1. 单击选 **[!UICONTROL Properties]** 项卡。
1. 为每个 **页面** 输入标签(例如：第1页=收集，第2页=谢谢)。

   ![](assets/dce_uc1_pagelabel.png)

对插入Web 应用程序的每个页面应用这些步骤。

>[!CAUTION]
>
>**数字内容编辑器为加载的HTML页执行JavaScript代码。** HTML模板中可能显示在Adobe Campaign界面中的JavaScript错误。 这些错误与编辑器无关。 要检查导入的文件中是否没有错误，建议先在浏览器(Internet Explorer/Firefox/Chrome)中测试这些错误，然后再将文件导入数字内容编辑器。

## 第2步——配置内容 {#step-2---configuring-the-content}

在本节中，我们将调整导入的内容并将数据库的字段链接到网页的表单。 以前创建的Web 应用程序是：

![](assets/dce_uc1_lp_enchainement.png)

### 修改内容 {#modifying-content}

让我们通过更改页面颜色来开始。 操作步骤：

1. 打开页 **[!UICONTROL Collection]** 面。
1. 单击背景。
1. 单 **击右侧** 的“背景颜色”。
1. 选择新的背景颜色。
1. 单击 **确定** ，以确认更改。

   ![](assets/dce_uc1_changecolor.png)

1. 应用这些相同的进程以更改按钮的颜色

   ![](assets/dce_uc1_finalcolor.png)

### 链接表单字段 {#linking-form-fields}

为了保存提供的信息，我们将将页面中的字段链接到数据库中的字段。

1. 选择表单字段。
1. 编辑 **[!UICONTROL Field]** 编辑器右侧的章节。
1. 选择要链接到所选字段的数据库字段。

   ![](assets/dce_uc1_mapping.png)

1. 对页面上的每个字段重复此过程。

您可以将字段设为必填字段：例如，单击字段 **[!UICONTROL Email]** ，然后启用“必 **选”** 选项。

![](assets/dce_uc1_fieldmandatory.png)

### 创建指向下一页的链接 {#creating-a-link-to-the-next-page}

此步骤是必选步骤，因为它将允许Web 应用程序确定后续步骤的顺序：将收集的数据保存在数据库中，然后显示下一页(**感谢页** )。

1. 选择页 **[!UICONTROL Send it!]** 面的按 **[!UICONTROL Collection]** 钮。
1. 单击下 **[!UICONTROL Action]** 拉菜单。
1. 选择操 **[!UICONTROL Next page]** 作。

   ![](assets/dce_uc1_actionbouton.png)

### 插入个性化字段 {#inserting-a-personalization-field}

通过此步骤，您可以个性化“感谢”页面。 操作步骤：

1. 打开页 **[!UICONTROL Thank you]** 面。
1. 将光标放在文本区域中，您希望在该区域插入收件人的名字。
1. 在工 **[!UICONTROL Personalization field]** 具栏 **[!UICONTROL Insert]** 的菜单中选择。
1. 选择名。

   ![](assets/dce_uc1_persochamp.png)

个性化字段在编辑器中具有黄色背景。

![](assets/dce_uc1_edit_champperso.png)

## 步骤3 —— 发布内容 {#step-3---publishing-content}

内容从Web 应用程序仪表板发布。 单击按 **[!UICONTROL Publish]** 钮以运行它。

![](assets/dce_uc1_pub_dashboard.png)

在发布过程中，将显示日志。 发布系统会分析在Web 应用程序中找到的所有内容

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>在发布日志中，警告和错误按活动排序。

表单现已可用：其URL可在应用程序仪表板中访问，并可发送给收件人。
