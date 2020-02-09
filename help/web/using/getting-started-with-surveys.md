---
title: 调查入门
seo-title: 调查入门
description: 调查入门
seo-description: null
page-status-flag: never-activated
uuid: 62ca684c-94a7-465a-9536-75e8a96b1c0e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 2df82006-dcc3-4b07-bc36-b646b1c27aaa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 调查入门{#getting-started-with-surveys}

以下是使用以下模板创建简单调查的主要步骤的快速概述：

![](assets/s_ncs_admin_survey_result.png)

这些步骤是：

1. [第1步——创建调查](#step-1---creating-a-survey),
1. [第2步——选择模板](#step-2---selecting-the-template),
1. [第3步——构建调查](#step-3---building-the-survey),
1. [第4步——创建页面内容](#step-4---creating-the-page-content),
1. [第5步——存储调查数据](#step-5---storing-the-survey-data-),
1. [第6步——发布页面](#step-6---publishing-the-pages),
1. [第7步——共享您的在线调查](#step-7---sharing-your-online-survey)。

## 第1步——创建调查 {#step-1---creating-a-survey}

要创建新调查，请转到或选项 **[!UICONTROL Campaigns]** 卡并 **[!UICONTROL Profiles and targets]** 单击菜 **[!UICONTROL Web Applications]** 单。 单击表 **[!UICONTROL Create]** 单列表上方的按钮。

![](assets/s_ncs_admin_survey_create.png)

## 第2步——选择模板 {#step-2---selecting-the-template}

选择调查模板，然后为调查提供一个名称。 此名称不会被最终用户看到，但允许在Adobe Campaign中识别调查。 单 **[!UICONTROL Save]** 击以将调查添加到Web应用程序列表。

![](assets/s_ncs_admin_survey_wz_00.png)

## 第3步——构建调查 {#step-3---building-the-survey}

调查以下元素所在的图形构建：创建内容的页面、数据预加载和保存步骤以及测试阶段。 脚本和查询也可以插入。

要构建图表，请单击 **[!UICONTROL Edit]** 调查的表单。

调查必须至 **少包含** 以下三个组件：页面、存储框和结束页面。

* 要创建页面，请在编辑 **[!UICONTROL Page]** 器的左侧部分选择该对象，然后将其放入中间部分，如下所示：

   ![](assets/s_ncs_admin_survey_new_page.png)

* 接下来，选 **[!UICONTROL Storage]** 择该对象，并将其放置在页面的输出过渡效果上。
* 最后，选择 **[!UICONTROL End]** 对象并将其放置在存储框的输出过渡的末尾，以获得以下图：

   ![](assets/s_ncs_admin_survey_end.png)

## 第4步——创建页面内容 {#step-4---creating-the-page-content}

在以下示例中，我们使用的是类 **[!UICONTROL Page (v5 compatibility)]** 型页面。 此类型的页面可通过选项卡的高级菜单 **[!UICONTROL Edit]** 访问。

![](assets/s_ncs_admin_survey_pagev5.png)

* 添加输入字段

   要创建页面内容，您必须编辑它：为此，请双击该对 **[!UICONTROL Page]** 象。 单击工具栏中的第一个图标以打开字段创建向导。 要为要存储在收件人配置文件的匹配字段中的用户名创建输入字段，请选择 **[!UICONTROL Edit a recipient]**。

   ![](assets/s_ncs_admin_survey_add_field_menu.png)

   单击按 **[!UICONTROL Next]** 钮以选择数据库中数据存储的字段。 在这种情况下，为“姓”字段。

   ![](assets/s_ncs_admin_survey_choose_field.png)

   单击 **[!UICONTROL Finish]** 以确认字段创建。

   默认情况下，当信息存储在数据库中已存在的字段中时，该字段将使用选定字段的名称，即本例中为“姓”。 您可以修改此标签，如下所示：

   ![](assets/s_ncs_admin_survey_change_label.png)

   现在，为用户帐户号码创建一个条目字段。 重复该操作，然后选择“帐户编号”。 字段。

   应用相同的过程，为用户添加一个字段以输入电子邮件地址。

* 要创建问题，请右键单击树中的最后一个元素，然后选择 **[!UICONTROL Containers > Question]** ，或单击图 **[!UICONTROL Containers]** 标并选择 **[!UICONTROL Question]**。

   ![](assets/s_ncs_admin_survey_add_qu.png)

   输入问题的标签并插入答案字段作为问题的子分支。 为此，在创建答案字段时，必须选择与问题链接的节点。 使用图 **[!UICONTROL drop-down listx]** 标或通 **[!UICONTROL Selection controls]** 过右键单击添加，如下所示：

   ![](assets/s_ncs_admin_survey_add_list.png)

   选择存储空间：选择一个枚举字段以自动检索值（本例中为电子邮件格式）。

   ![](assets/s_ncs_admin_survey_add_itz_list.png)

   在选项 **[!UICONTROL General]** 卡中，单击链 **[!UICONTROL Initialize the list of values from the database]** 接：将自动输入值表。

   ![](assets/s_ncs_admin_survey_add_value.png)

   单击 **[!UICONTROL OK]** 以关闭编辑器，并 **[!UICONTROL Save]** 保存更改。

   >[!NOTE]
   >
   >由于选项卡中的选项，您可以针对每个字段或问题调整页面布局以满足您的需 **[!UICONTROL Advanced]** 求。 本节详细介绍了调查屏幕 [的布局](../../web/using/about-web-forms.md)。

   在详细信息屏幕中，单 **[!UICONTROL Preview]** 击选项卡以查看您刚刚创建的调查的呈现。

   ![](assets/s_ncs_admin_survey_preview.png)

## 第5步——存储调查数据 {#step-5---storing-the-survey-data-}

通过存储框，可以将用户响应保存在数据库中。 必须选择对帐密钥以标识数据库中已有的配置文件。

为此，请编辑该框，然后选择存储数据时将用作对帐密钥的字段。

在以下示例中，在进行保存（确认）时，如果将配置文件保存在数据库中，并且其帐户编号与表单中的一个输入相同，则配置文件将会更新。 如果配置文件不存在，则将创建该配置文件。

![](assets/s_ncs_admin_survey_save_edit.png)

单击 **[!UICONTROL OK]** 以确认，然后单击 **[!UICONTROL Save]** 以保存调查

## 第6步——发布页面 {#step-6---publishing-the-pages}

要使用户能够访问HTML页，应用程序必须可用。 它不再处于编辑阶段，而是在生产阶段。 要将调查投放到生产中，您必须发布该调查。 操作步骤：

* 单击位于 **[!UICONTROL Publish]** 调查功能板上方的按钮。
* 单击 **[!UICONTROL Start]** 以启动发布并关闭向导。

   ![](assets/s_ncs_admin_survey_start_publ.png)

   调查的状态将更改为：在 **线**。

   ![](assets/survey_published.png)

## 第7步——共享在线调查 {#step-7---sharing-your-online-survey}

调查生产完毕后，即可在服务器上访问，并且您可以提交该调查。 用于访问调查的URL显示在功能板上。

![](assets/survey_url_from_dashboard.png)

要传送调查，您可以发送一条消息，其中包含指向目标人群的访问链接，或将调查访问URL放在网页上。

然后，您可以通过报告和日志监视用户响应。 请参阅 [响应跟踪](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。

>[!CAUTION]
>
>公共URL包括调查的内部名称。 修改内部名称后，URL会自动更新：必须同时更新指向调查的所有链接。
>
>如果已发送包含指向表单的链接的分发，则此链接将不再有效。

