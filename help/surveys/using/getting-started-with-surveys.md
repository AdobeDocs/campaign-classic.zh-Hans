---
product: campaign
title: 创建调查的关键步骤
description: 使用Campaign创建您的第一个调查
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 22e14b24-59ba-4a92-8ffb-f5336793d64f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# 创建调查的关键步骤{#getting-started-with-surveys}

![](../../assets/v7-only.svg)

以下是使用以下内置模板创建简单调查的主要步骤的快速概述：

![](assets/s_ncs_admin_survey_result.png)

这些步骤包括：

1. [步骤1 — 创建调查](#step-1---creating-a-survey),
1. [第2步 — 选择模板](#step-2---selecting-the-template),
1. [步骤3 — 构建调查](#step-3---building-the-survey),
1. [第4步 — 创建页面内容](#step-4---creating-the-page-content)、
1. [步骤5 — 存储调查数据](#step-5---storing-the-survey-data-),
1. [第6步 — 发布页面](#step-6---publishing-the-pages)、
1. [步骤7 — 共享您的在线调查](#step-7---sharing-your-online-survey)。

## 步骤1 — 创建调查 {#step-1---creating-a-survey}

要创建新调查，请转到&#x200B;**[!UICONTROL Campaigns]**&#x200B;或&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Web Applications]**&#x200B;菜单。 单击表单列表上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

![](assets/s_ncs_admin_survey_create.png)

## 第2步 — 选择模板 {#step-2---selecting-the-template}

选择调查模板，然后为调查提供一个名称。 最终用户将看不到此名称，但它允许在Adobe Campaign中识别调查。 单击&#x200B;**[!UICONTROL Save]**&#x200B;将调查添加到Web应用程序列表。

![](assets/s_ncs_admin_survey_wz_00.png)

## 步骤3 — 构建调查 {#step-3---building-the-survey}

在图表中构建调查，其中放置了以下元素：将创建内容的页面、数据预加载和保存步骤以及测试阶段。 脚本和查询也可以插入。

要构建图表，请单击调查的&#x200B;**[!UICONTROL Edit]**&#x200B;表单。

调查必须至少包含以下三个组件：****:页面、存储框和结束页面。

* 要创建页面，请在编辑器的左侧部分选择&#x200B;**[!UICONTROL Page]**&#x200B;对象，并将其放入中间部分，如下所示：

   ![](assets/s_ncs_admin_survey_new_page.png)

* 接下来，选择&#x200B;**[!UICONTROL Storage]**&#x200B;对象，并将其置于页面的输出过渡中。
* 最后，选择&#x200B;**[!UICONTROL End]**&#x200B;对象，并将其放在存储盒的输出过渡的末尾，以获得下图：

   ![](assets/s_ncs_admin_survey_end.png)

## 第4步 — 创建页面内容 {#step-4---creating-the-page-content}

在以下示例中，我们使用的是&#x200B;**[!UICONTROL Page (v5 compatibility)]**&#x200B;类型的页面。 可通过&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡的高级菜单访问此类页面。

![](assets/s_ncs_admin_survey_pagev5.png)

* **添加输入字段**

   要创建页面内容，必须对其进行编辑：为此，请双击&#x200B;**[!UICONTROL Page]**&#x200B;对象。 单击工具栏中的第一个图标以打开字段创建向导。 要为要存储在收件人用户档案匹配字段中的用户名创建条目字段，请选择&#x200B;**[!UICONTROL Edit a recipient]**。

   ![](assets/s_ncs_admin_survey_add_field_menu.png)

   单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮以选择数据库中数据存储的字段。 在本例中，为“姓氏”字段。

   ![](assets/s_ncs_admin_survey_choose_field.png)

   单击&#x200B;**[!UICONTROL Finish]**&#x200B;以确认字段创建。

   默认情况下，当信息存储在数据库中已存在的字段中时，该字段会使用选定字段的名称，即此示例中的“姓氏”。 您可以修改此标签，如下所示：

   ![](assets/s_ncs_admin_survey_change_label.png)

   现在，为用户帐号创建一个条目字段。 重复该操作并选择“帐户否”。 字段。

   应用相同的过程，以添加一个字段供用户输入电子邮件地址。

* **创建问题**

   要创建问题，请右键单击树中的最后一个元素，然后选择&#x200B;**[!UICONTROL Containers > Question]** ，或单击&#x200B;**[!UICONTROL Containers]**&#x200B;图标并选择&#x200B;**[!UICONTROL Question]**。

   ![](assets/s_ncs_admin_survey_add_qu.png)

   输入问题的标签并插入答案字段作为问题的子分支。 为此，在创建答案字段时必须选择链接到问题的节点。 使用&#x200B;**[!UICONTROL Selection controls]**&#x200B;图标或通过右键单击添加&#x200B;**[!UICONTROL drop-down listx]**，如下所示：

   ![](assets/s_ncs_admin_survey_add_list.png)

   选择存储空间：选择枚举字段以自动检索值（本例中为电子邮件格式）。

   ![](assets/s_ncs_admin_survey_add_itz_list.png)

   在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Initialize the list of values from the database]**&#x200B;链接：将自动输入值表。

   ![](assets/s_ncs_admin_survey_add_value.png)

   单击&#x200B;**[!UICONTROL OK]**&#x200B;以关闭编辑器，单击&#x200B;**[!UICONTROL Save]**&#x200B;以保存更改。

   >[!NOTE]
   >
   >由于&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中的选项，您可以针对每个字段或问题调整页面布局以满足您的需求。 [此部分](../../web/using/about-web-forms.md)中详细描述了调查屏幕的布局。

   在详细信息屏幕中，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以查看刚刚创建的调查的呈现。

   ![](assets/s_ncs_admin_survey_preview.png)

## 步骤5 — 存储调查数据 {#step-5---storing-the-survey-data-}

利用存储框，可在数据库中保存用户响应。 必须选择协调键值以标识数据库中已存在的用户档案。

要实现此目的，请编辑方框并选择在存储数据时用作协调键值的字段。

在以下示例中，在进行保存（确认）时，如果某个用户档案保存在与表单中输入的一个帐号相同的数据库中，则该用户档案将会更新。 如果用户档案不存在，则将创建该用户档案。

![](assets/s_ncs_admin_survey_save_edit.png)

单击&#x200B;**[!UICONTROL OK]**&#x200B;进行确认，然后单击&#x200B;**[!UICONTROL Save]**&#x200B;保存调查

## 第6步 — 发布页面 {#step-6---publishing-the-pages}

要使用户能够访问HTML页面，必须使应用程序可用。 它必须不再处于编辑阶段，而是在生产阶段。 要在生产中放置调查，必须发布该调查。 操作步骤：

* 单击位于调查仪表板上方的&#x200B;**[!UICONTROL Publish]**&#x200B;按钮。
* 单击&#x200B;**[!UICONTROL Start]**&#x200B;以启动发布并关闭向导。

   ![](assets/s_ncs_admin_survey_start_publ.png)

   调查的状态将更改为：**联机**。

   ![](assets/survey_published.png)

## 步骤7 — 共享您的在线调查 {#step-7---sharing-your-online-survey}

调查投放到生产环境后，即可在服务器上访问并提交该调查。 用于访问调查的URL显示在功能板上。

![](assets/survey_url_from_dashboard.png)

要传送调查，您可以发送包含目标群体访问链接的消息，或将调查访问URL放在网页上。

然后，您可以通过报告和日志监控用户响应。 请参阅[响应跟踪](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)。

>[!CAUTION]
>
>公共URL包含调查的内部名称。 修改内部名称后，URL会自动更新：还必须更新指向调查的所有链接。
>
>如果已发送包含表单链接的投放，则此链接将不再有效。
