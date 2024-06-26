---
product: campaign
title: 创建优惠
description: 创建优惠
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: c6dd2709-06e3-4227-bbec-99f3d80144fe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---

# 创建优惠{#creating-an-offer}



## 创建选件 {#creating-the-offer}

要创建选件，请应用以下步骤：

1. 转到 **[!UICONTROL Campaigns]** 选项卡，然后单击 **[!UICONTROL Offers]** 链接。

   ![](assets/offer_create_001.png)

1. 单击 **[!UICONTROL Create]** 按钮。

   ![](assets/offer_create_005.png)

1. 更改标签并选择选件应属于的类别。

   ![](assets/offer_create_002.png)

1. 单击 **[!UICONTROL Save]** 以创建选件。

   ![](assets/offer_create_003.png)

   该选件可在平台中使用，并且可以配置其内容。

   ![](assets/offer_create_004.png)

## 配置优惠资格 {#configuring-offer-eligibility}

在 **[!UICONTROL Eligibility]** 选项卡，定义优惠的有效期限和可以显示的时间、要应用于目标的过滤器和优惠权重。

### 定义优惠的资格期限 {#defining-the-eligibility-period-of-an-offer}

要定义优惠的资格期限，请使用下拉列表并在日历中选择开始日期和结束日期。

![](assets/offer_eligibility_create_002.png)

在这些日期之外，交互引擎将不会选择选件。 如果您还为优惠类别配置了资格日期，则将应用最严格的时段。

### 目标上的过滤器 {#filters-on-the-target}

您可以将过滤器应用于选件目标。

要执行此操作，请单击 **[!UICONTROL Edit query]** 链接并选择要应用的过滤器。 (请参阅 [本节](../../platform/using/steps-to-create-a-query.md#step-4---filter-data))。

![](assets/offer_eligibility_create_003.png)

如果已经创建了预定义过滤器，则可以从用户过滤器列表中选择它们。 有关详细信息，请参见 [创建预定义过滤器](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### 优惠权重 {#offer-weight}

要使引擎能够在目标有资格使用的多个优惠之间做出决定，您需要为该优惠分配一个或多个权重。 如有必要，您还可以将过滤器应用于目标，或限制将应用权重的选件空间。 权重较高的选件优先于权重较低的选件。

您可以为同一选件配置多个权重，例如为了区分超周期、特定目标甚至选件空间。

例如，选件可以具有18至25岁的触点的重量A和高于该范围的触点的重量B。 如果某个选件在整个夏季都符合条件，则它在7月份的权重可以是A，在8月份的权重可以是B。

>[!NOTE]
>
>分配的权重可以根据优惠所属的类别的参数临时修改。 有关详细信息，请参见 [创建优惠类别](../../interaction/using/creating-offer-categories.md).

要在选件中创建权重，请应用以下步骤：

1. 单击 **[!UICONTROL Add]**。

   ![](assets/offer_weight_create_001.png)

1. 更改标签并分配权重。 默认情况下，该值为1。

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >如果未输入权重(0)，则目标将不被视为符合优惠条件。

1. 如果要将加权应用于给定期间，请定义资格日期。

   ![](assets/offer_weight_create_002.png)

1. 如有必要，请将权重限制为特定优惠空间。

   ![](assets/offer_weight_create_003.png)

1. 将过滤器应用于目标。

   ![](assets/offer_weight_create_004.png)

1. 单击 **[!UICONTROL OK]** 以减轻重量。

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >如果目标符合选定优惠的多重资格，则引擎将保留最佳（最高）权重。 调用选件引擎时，最多为每个联系人选择一个选件。

### 优惠资格规则摘要 {#a-summary-of-offer-eligibility-rules}

配置完成后，资格规则的摘要将显示在优惠仪表板上。

要查看它，请单击 **[!UICONTROL Schedule and eligibility rules]** 链接。

![](assets/offer_eligibility_create_005.png)

## 创建选件内容 {#creating-the-offer-content}

1. 单击 **[!UICONTROL Edit]** 选项卡，然后单击 **[!UICONTROL Content]** 选项卡。

   ![](assets/offer_content_create_001.png)

1. 填写选件内容的各个字段。

   * **[!UICONTROL Title]** ：指定要显示在选件中的标题。 警告：这不是指优惠的标签，该标签在 **[!UICONTROL General]** 选项卡。
   * **[!UICONTROL Destination URL]** ：指定选件的URL。 要正确处理，必须以“http://”或“https://”开头。
   * **[!UICONTROL Image URL]** ：指定选件图像的URL或访问路径。
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** ：在所需的选项卡中输入选件正文。 要生成跟踪，请 **[!UICONTROL HTML content]** HTML必须由可以包含在 `<div>` 键入元素。 例如，的结果 `<table>` HTML页面中的元素如下所示：

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   有关定义接受URL的信息，请参见 [接受建议时配置状态](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) 部分。

   ![](assets/offer_content_create_002.png)

   要查找在优惠空间配置期间定义的必填字段，请单击 **[!UICONTROL Content definitions]** 用于显示列表的链接。 有关详细信息，请参见 [创建优惠空间](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   在此示例中，选件必须包含标题、图像、HTML内容和目标URL。

## 预览选件 {#previewing-the-offer}

配置优惠内容后，您可以预览该优惠对其收件人显示的内容。 操作步骤：

1. 单击 **[!UICONTROL Preview]** 选项卡。

   ![](assets/offer_preview_create_001.png)

1. 选择要查看的优惠的表示形式。

   ![](assets/offer_preview_create_002.png)

1. 如果您已个性化优惠内容，请选择优惠目标以查看个性化。

   ![](assets/offer_preview_create_003.png)

## 对优惠创建假设验证 {#creating-a-hypothesis-on-an-offer}

您可以在优惠建议上创建假设验证。 这使您可以确定优惠对相关产品执行购买的影响。

>[!NOTE]
>
>这些假设将通过响应管理器执行。 请核实您的许可协议。

有关优惠建议作出的假设，请参阅 **[!UICONTROL Measure]** 选项卡。

有关创建假设验证的详情，请参见 [此页面](../../response/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)
