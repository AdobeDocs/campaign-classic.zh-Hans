---
product: campaign
title: 配置对报告的访问权限
description: 配置对报告的访问权限
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 1e5ab922-481c-4dce-a05e-a58408002e24
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 1%

---

# 配置对报告的访问权限{#configuring-access-to-the-report}

## 报表显示上下文{#report-display-context}

使用&#x200B;**[!UICONTROL Display]**&#x200B;选项卡定义Adobe Campaign平台中报表的显示上下文。 报表的访问权限取决于其选择类型、显示条件和访问权限。

### 选择类型{#selection-type}

对报表的访问权限可以限制为特定的上下文或选件空间，例如投放、收件人、选择的收件人等。 此访问在&#x200B;**[!UICONTROL Display]**&#x200B;选项卡的&#x200B;**[!UICONTROL Selection type]**&#x200B;部分中配置。

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** :仅当选择特定实体时，才可访问报表。
* **[!UICONTROL Multiple selection]** :选择多个实体后，将访问报告。
* **[!UICONTROL Global]** :可通过选项卡中的可用报表列表访问该 **[!UICONTROL Reports]** 报表。

### 显示序列{#display-sequence}

**[!UICONTROL Sequence]**&#x200B;字段允许您输入一个数值，用于指定报表在列表中的显示顺序。

默认情况下，报表按相关性显示：在此字段中输入的值允许您将报表从最高值（最高值）排序到最低值（最小值）相关。

您可以根据需要选择要使用的比例尺：1到10、0到100、-10到10等

### 显示条件{#display-conditions}

您还可以通过查询对报表的显示设置条件。

![](assets/s_ncs_advuser_report_visibility_5.png)

在以下示例中，如果主营销活动渠道是电子邮件，则会显示报表。

![](assets/s_ncs_advuser_report_visibility_6.png)

这意味着，如果营销活动的主渠道是直邮，则营销活动报表中将不提供该报表。

### 访问授权{#access-authorization}

可以与其他运算符共享该报表。

要使报表可访问，请选择&#x200B;**[!UICONTROL Report shared with other operators]**&#x200B;选项。 如果未选择此选项，则只有创建报表的操作员才能访问报表。

还可以与通过授权窗口添加的特定操作员或操作员组共享报表。

![](assets/s_ncs_advuser_report_visibility_8.png)

### 定义筛选选项{#defining-the-filtering-options}

**[!UICONTROL Reports]**&#x200B;选项卡显示平台中所有可用的报表，连接的操作员对这些报表具有访问权限。

默认情况下，这些过滤器按相关性排序，但您可以应用其他类型的过滤器：按字母顺序、年龄等

您还可以根据报表类别过滤显示内容：

![](assets/report_ovv_select_type.png)

要定义报表的类别，请通过&#x200B;**[!UICONTROL Display]**&#x200B;选项卡选择报表，如下所示：

![](assets/report_select_category.png)

您可以在此处输入新类别，并将其添加到可用类别列表。 匹配的枚举会自动更新。

## 创建指向报表{#creating-a-link-to-a-report-}的链接

可以通过树的特定节点（如列表、收件人、投放等）访问报表。 要实现此目的，只需创建一个指向相关报告的链接，并指定要将其提供到的实体即可。

例如，我们将创建一个指向报表的链接，以便通过收件人列表访问该报表。

1. 单击&#x200B;**[!UICONTROL New]**，然后在报表创建向导中选择&#x200B;**[!UICONTROL Create a link to an existing report]**。

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. 从下拉列表中选择要创建链接的报表。 在本例中，我们将选择&#x200B;**按国家/地区**&#x200B;划分报表。

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. 输入标签并选择架构。 在本例中，我们将选择收件人列表表。

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   这意味着可通过任何收件人列表访问报告，并且统计信息将与选定列表中的收件人有关。

1. 保存和显示您的报表。
1. 输入链接键。 在这种情况下，“文件夹”链接的外键。

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. 发布报表。
1. 转到收件人列表之一，然后单击&#x200B;**[!UICONTROL Reports]**&#x200B;链接：您可以访问刚刚创建的报表。

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## 预览报表{#preview-of-the-report}

在发布报表之前，请确保该报表正确显示在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中。

![](assets/s_ncs_advuser_report_preview_01.png)

要显示报表的预览，请选择&#x200B;**[!UICONTROL Global]**&#x200B;或&#x200B;**[!UICONTROL Selection]**&#x200B;选项。

这两个选项是根据报表的显示设置选择的。 如果显示设置为&#x200B;**[!UICONTROL Global]**，则需要选择&#x200B;**[!UICONTROL Global]**&#x200B;预览选项。 如果显示设置为&#x200B;**[!UICONTROL Single selection]**&#x200B;或&#x200B;**[!UICONTROL Multiple selection]**，则必须选择&#x200B;**[!UICONTROL Selection]**&#x200B;预览选项。

有关更多信息，请参阅[报表显示上下文](#report-display-context)。

通过特定设置，您可以控制错误。 **_uuid**&#x200B;设置位于报表的URL中。 您可以向其添加&#x200B;**&amp;_preview**&#x200B;或&#x200B;**&amp;_debug**&#x200B;设置。

要了解有关这些设置的更多信息，请参阅[Web窗体](../../web/using/about-web-forms.md)章节的&#x200B;**定义Web窗体属性**&#x200B;部分。

## 发布报表{#publishing-the-report}

必须发布报表，才能与其他运算符共享并在可用报表列表中显示它们（另请参阅[报表显示上下文](#report-display-context)）。 每次更改报表时，必须再次执行此操作。

1. 单击工具栏中的&#x200B;**[!UICONTROL Publish]**&#x200B;以打开发布向导。

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. 单击&#x200B;**[!UICONTROL Start]**&#x200B;以发布。

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. 单击&#x200B;**[!UICONTROL Enlarge]**&#x200B;图标以在Web浏览器中打开报表。
