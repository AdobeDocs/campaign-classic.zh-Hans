---
solution: Campaign Classic
product: campaign
title: 配置对报告的访问权限
description: 配置对报告的访问权限
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---


# 配置对报告的访问权限{#configuring-access-to-the-report}

## 报告显示上下文{#report-display-context}

使用&#x200B;**[!UICONTROL Display]**&#x200B;选项卡定义Adobe Campaign平台中报表的显示上下文。 对报告的访问权限取决于其选择类型、显示条件和访问授权。

### 选择类型{#selection-type}

对报告的访问可限于特定的上下文或优惠空间，例如投放、收件人、选择收件人等。 此访问在&#x200B;**[!UICONTROL Display]**&#x200B;选项卡的&#x200B;**[!UICONTROL Selection type]**&#x200B;部分进行配置。

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** :仅当选择特定实体时，才可访问报告。
* **[!UICONTROL Multiple selection]** :选择多个实体时，将访问报告。
* **[!UICONTROL Global]** :可以通过“报告”(Reports)范围中可用报告的列表访问报告。

### 显示序列{#display-sequence}

在&#x200B;**[!UICONTROL Sequence]**&#x200B;字段中，可以输入一个数值，指定列表中报表的显示顺序。

默认情况下，报表按相关性显示：在此字段中输入的值允许您将报表从最大（最高值）排序到最小（最小值）相关。

您可以根据需要选择要使用的比例：1到10,0到100,-10到10，等等。

### 显示条件{#display-conditions}

您还可以通过查询对报告的显示进行条件设置。

![](assets/s_ncs_advuser_report_visibility_5.png)

在以下示例中，如果主活动渠道是电子邮件，则显示报表。

![](assets/s_ncs_advuser_report_visibility_6.png)

这意味着，如果活动的主要渠道是直接邮寄，则活动报告中将不提供此报告。

### 访问授权{#access-authorization}

报告可以与其他操作符共享。

要使报告可访问，请选择&#x200B;**[!UICONTROL Report shared with other operators]**&#x200B;选项。 如果未选择此选项，则只有创建报表的操作员才能访问报表。

还可以与通过授权窗口添加的特定操作符或操作员组共享报告。

![](assets/s_ncs_advuser_report_visibility_8.png)

### 定义过滤选项{#defining-the-filtering-options}

**[!UICONTROL Reports]**&#x200B;范围显示平台中所有可用的报告，并且所连接的操作员对其具有访问权限。

默认情况下，它们按相关性排序，但您可以应用其他类型的过滤器:按年龄排列

您还可以根据报表类别筛选显示内容：

![](assets/report_ovv_select_type.png)

要定义报表的类别，请通过&#x200B;**[!UICONTROL Display]**&#x200B;选项卡选择它，如下所示：

![](assets/report_select_category.png)

您可以在此处输入新类别，并将其添加到可用类别的列表。 匹配明细列表会自动更新。

## 创建指向报告{#creating-a-link-to-a-report-}的链接

可以通过树的特定节点(如列表、收件人、投放等)访问报告。 为此，只需创建指向相关报告的链接并指定要提供该报告的实体。

例如，我们将创建一个指向报表的链接，以便通过列表收件人访问该报表。

1. 单击&#x200B;**[!UICONTROL New]**&#x200B;并在报告创建向导中选择&#x200B;**[!UICONTROL Create a link to an existing report]**。

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. 选择要使用下拉列表创建链接的报表。 在此示例中，我们将选择&#x200B;**按国家／地区**&#x200B;划分报表。

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. 输入标签并选择模式。 在此示例中，我们将选择收件人列表表。

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   这意味着报告可以通过任何收件人列表访问，而统计将涉及选定列表的收件人。

1. 保存和显示报表。
1. 输入链接键。 在这种情况下，“文件夹”链接的外键。

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. 发布报告。
1. 转到您的收件人列表之一并单击&#x200B;**[!UICONTROL Reports]**&#x200B;链接：您刚刚创建的报告可访问。

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## 报告的预览{#preview-of-the-report}

在发布报告之前，请确保报告在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中正确显示。

![](assets/s_ncs_advuser_report_preview_01.png)

要显示报告的预览，请选择&#x200B;**[!UICONTROL Global]**&#x200B;或&#x200B;**[!UICONTROL Selection]**&#x200B;选项。

根据报告的显示设置选择这两个选项。 如果显示设置为&#x200B;**[!UICONTROL Global]**，则需要选择&#x200B;**[!UICONTROL Global]**&#x200B;预览选项。 如果显示设置为&#x200B;**[!UICONTROL Single selection]**&#x200B;或&#x200B;**[!UICONTROL Multiple selection]**，则必须选择&#x200B;**[!UICONTROL Selection]**&#x200B;预览选项。

有关详细信息，请参阅[报告显示上下文](#report-display-context)。

通过特定设置，您可以控制错误。 报告的URL中有&#x200B;**_uuid**&#x200B;设置。 可以向其添加&#x200B;**&amp;_预览**&#x200B;或&#x200B;**&amp;_debug**&#x200B;设置。

要进一步了解这些设置，请参阅&#x200B;**Web 窗体[一章的“定义Web表单属性”**&#x200B;一节。](../../web/using/about-web-forms.md)

## 发布报告{#publishing-the-report}

必须发布报告，才能与其他运算符共享它们并在可用报告的列表中显示它们（也请参阅[报告显示上下文](#report-display-context)）。 每次更改报告时，都必须再次执行此操作。

1. 单击工具栏中的&#x200B;**[!UICONTROL Publish]**&#x200B;打开发布向导。

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. 单击&#x200B;**[!UICONTROL Start]**&#x200B;进行发布。

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. 单击&#x200B;**[!UICONTROL Enlarge]**&#x200B;图标以在Web浏览器中打开报告。

