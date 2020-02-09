---
title: 创建登陆页面
seo-title: 创建登陆页面
description: 创建登陆页面
seo-description: null
page-status-flag: never-activated
uuid: fc0e9749-f44e-4aa0-bdfa-6f44ba570bea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 5f1e5886-628f-4c9e-80c1-d82feec23e8c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 创建登陆页面{#creating-a-landing-page}

## 关于登陆页面创建 {#about-landing-pages-creation}

此用例说明了如何使用数字编辑器从Adobe Campaign控制台创建登录页面。

在Adobe Campaign中开始配置登录页面之前，请确 **保有一个或多个模板** ，以表示HTML页面。

此用例的主要目的是使登录页面表单字段与Adobe Campaign中的内部字段对应，并使用DCE中的功能。

## 创建登陆页面 {#creating-the-landing-page}

要创建新的登录页面类型Web应用程序，请执行以下步骤：

1. 转到选项卡 **[!UICONTROL Campaigns]** 并单击链接， **[!UICONTROL Web application]** 然后单击按 **[!UICONTROL Create]** 钮。
1. 选择模 **[!UICONTROL New landing page]** 板并输入标签，然后单击 **[!UICONTROL Save]**。

   ![](assets/dce_uc1_newlandingpage.png)

1. 单击选 **[!UICONTROL Edit]** 项卡。
1. 删除“ **结束** ”活动。
1. 在活动 **[!UICONTROL Page]** 之后添加活 **[!UICONTROL Storage]** 动。
1. 编辑第2页 **活动** ，然后取消选中 **[!UICONTROL Activate outbound transitions]** 选项卡中的 **[!UICONTROL Properties]** 选项。

   ![](assets/dce_uc1_transition.png)

1. 保存更改。

然后，您将获得以下序列：

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>有关创建Web应用程序的详细信息，请参 [阅本节](../../web/using/creating-a-new-web-application.md)。

## 第1步——选择和加载模板 {#step-1---selecting-and-loading-templates}

本节将介绍如何为Web应用程 **序的每页导入HTML** 内容。

模板必须包含：

* HTML **文件** （必填）
* 一个或多个 **CSS** 文件（可选）
* 一张或多 **张图像** （可选）

要在第一页上加载模板，请应用以下步骤：

1. 打开Web应 **[!UICONTROL Page]** 用程序的第一个活动。
1. 选择 **[!UICONTROL From a file]** 以获取您的内容模板。

   ![](assets/dce_uc1_selectmodel.png)

1. 选择要使用的HTML文件。
1. 单击 **打开** ，开始导入。

   在加载过程中，将显示共享文件的列表。 导入系统检查链接到所选HTML的所有文件（CSS、图像等）是否在该位置。

   完成导 **[!UICONTROL Close]** 入后，单击按钮。

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >您必须等到收到以下消息后才关闭： **[!UICONTROL The external resources have been successfully published]** .

1. 单击选 **[!UICONTROL Properties]** 项卡。
1. 为每个 **页面输入** 标签(例如：第1页=收集，第2页=谢谢)。

   ![](assets/dce_uc1_pagelabel.png)

对在Web应用程序中插入的每个页面应用这些步骤。

>[!CAUTION]
>
>**DCE为加载的HTML页面执行JavaScript代码。** HTML模板中可能显示在Adobe Campaign界面中的JavaScript错误。 这些错误与编辑器无关。 要检查导入的文件中是否没有错误，建议先在浏览器(Internet Explorer/Firefox / Chrome)中测试这些错误，然后再将文件导入DCE。

## 第2步——配置内容 {#step-2---configuring-the-content}

在本节中，我们将调整导入的内容并将数据库的字段链接到网页的表单。 以前创建的Web应用程序是：

![](assets/dce_uc1_lp_enchainement.png)

### 修改内容 {#modifying-content}

让我们首先更改页面的颜色。 操作步骤：

1. 打开页 **[!UICONTROL Collection]** 面。
1. 单击背景。
1. 单击 **右侧的** “背景颜色”。
1. 选择新的背景色。
1. 单击 **确定** ，以确认更改。

   ![](assets/dce_uc1_changecolor.png)

1. 应用这些相同的进程以更改按钮的颜色

   ![](assets/dce_uc1_finalcolor.png)

### 链接表单字段 {#linking-form-fields}

为了保存提供的信息，我们将页面中的字段链接到数据库中的字段。

1. 选择表单字段。
1. 编辑 **[!UICONTROL Field]** 器右侧的章节。
1. 选择要链接到所选字段的数据库字段。

   ![](assets/dce_uc1_mapping.png)

1. 对页面上的每个字段重复此过程。

您可以将字段设为必填字段：例如，单击字段， **[!UICONTROL Email]** 然后启用“必 **选** ”选项。

![](assets/dce_uc1_fieldmandatory.png)

### 创建指向下一页的链接 {#creating-a-link-to-the-next-page}

此步骤是必需的，因为它将允许Web应用程序确定后续步骤的顺序：将收集的数据保存在数据库中，然后显示下一页(**感谢页** )。

1. 选择页 **[!UICONTROL Send it!]** 面的按 **[!UICONTROL Collection]** 钮。
1. 单击 **[!UICONTROL Action]** 下拉菜单。
1. 选择操 **[!UICONTROL Next page]** 作。

   ![](assets/dce_uc1_actionbouton.png)

### 插入个性化字段 {#inserting-a-personalization-field}

通过此步骤，您可以个性化“感谢”页面。 操作步骤：

1. 打开页 **[!UICONTROL Thank you]** 面。
1. 将光标放在文本区域中，您希望在该区域插入收件人的名字。
1. 在工 **[!UICONTROL Personalization field]** 具栏 **[!UICONTROL Insert]** 的菜单中选择。
1. 选择名字。

   ![](assets/dce_uc1_persochamp.png)

个性化字段在编辑器中具有黄色背景。

![](assets/dce_uc1_edit_champperso.png)

## 第3步——发布内容 {#step-3---publishing-content}

内容从Web应用程序功能板发布。 单击该 **[!UICONTROL Publish]** 按钮以运行它。

![](assets/dce_uc1_pub_dashboard.png)

在发布过程中，将显示日志。 发布系统分析Web应用程序中找到的所有内容

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>在发布日志中，警告和错误按活动排序。

表单现已可用：其URL可在应用程序功能板中访问，并可发送给收件人。
