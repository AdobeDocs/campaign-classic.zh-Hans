---
title: 创建优惠
seo-title: 创建优惠
description: 创建优惠
seo-description: null
page-status-flag: never-activated
uuid: 9e8b0351-e2a5-4043-be86-e275d2f849ea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 010c88f4-9444-448f-bb7b-7191517d2e23
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 2%

---


# 创建优惠{#creating-an-offer}

## 创建优惠 {#creating-the-offer}

要创建优惠，请应用以下步骤：

1. 转到宇宙 **[!UICONTROL Campaigns]** 并单击链 **[!UICONTROL Offers]** 接。

   ![](assets/offer_create_001.png)

1. 单击 **[!UICONTROL Create]** 按钮。

   ![](assets/offer_create_005.png)

1. 更改标签并选择优惠应属于的类别。

   ![](assets/offer_create_002.png)

1. 单击 **[!UICONTROL Save]** 以创建优惠。

   ![](assets/offer_create_003.png)

   该优惠在平台中可用，并且可以配置其内容。

   ![](assets/offer_create_004.png)

## 配置优惠资格 {#configuring-offer-eligibility}

在选 **[!UICONTROL Eligibility]** 项卡中，定义优惠的有效期，并可显示要应用于目标和优惠权重的过滤器。

### 定义优惠的资格期 {#defining-the-eligibility-period-of-an-offer}

要定义优惠的资格期，请使用下拉列表，并在日历中选择开始和结束日期。

![](assets/offer_eligibility_create_002.png)

在这些日期之外，交互引擎不会选择优惠。 如果您还为优惠类别配置了资格日期，则限制最严格的期限将适用。

### 过滤器目标 {#filters-on-the-target}

您可以将过滤器应用于优惠目标。

为此，请单击链 **[!UICONTROL Edit query]** 接，然后选择要应用的筛选器。 (Refer to [this section](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

如果已创建预定义过滤器，则可以从用户过滤器的列表中选择它们。 有关此内容的详细信息，请参阅 [创建预定义过滤器](../../interaction/using/creating-predefined-filters.md)。

![](assets/offer_eligibility_create_004.png)

### 优惠权重 {#offer-weight}

要使引擎能够在优惠符合条件的目标之间做出决定，您需要为优惠分配一个或多个权重。 如有必要，您还可以将过滤器应用于目标，或限制权重将应用于的优惠空间。 具有更重要权重的优惠将优先于权重较少的优惠。

您可以为同一优惠配置多个权重，例如，区分子、特定目标甚至优惠空间。

例如，优惠可以具有A权重（对于年龄在18到25岁的联系人）和B权重（对于高于该范围的联系人）。 如果优惠在整个夏天都符合条件，则还可在7月获得A权重，在8月获得B权重。

>[!NOTE]
>
>可以根据权重所属类别的参数临时修改指定的优惠。 有关此内容的详细信息，请参阅 [创建优惠类别](../../interaction/using/creating-offer-categories.md)。

要在权重中创建优惠，请应用以下步骤：

1. 单击 **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. 更改标签并分配权重。 默认情况下，它为1。

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >如果未输入权重(0)，则目标将不被视为符合优惠资格。

1. 如果希望权重在给定期间应用，请定义资格日期。

   ![](assets/offer_weight_create_002.png)

1. 如有必要，将权重限制为特定优惠空间。

   ![](assets/offer_weight_create_003.png)

1. 对目标应用过滤器。

   ![](assets/offer_weight_create_004.png)

1. Click **[!UICONTROL OK]** to save the weight.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >如果目标有资格获得所选优惠的多个权重，引擎将保持最佳（最高）权重。 调用优惠引擎时，每个联系人最多选择一次优惠。

### 优惠合格规则 {#a-summary-of-offer-eligibility-rules}

配置完成后，合格规则仪表板中将显示该优惠的摘要。

要视图它，请单击 **[!UICONTROL Schedule and eligibility rules]** 链接。

![](assets/offer_eligibility_create_005.png)

## 创建优惠内容 {#creating-the-offer-content}

1. 单击选 **[!UICONTROL Edit]** 项卡，然后单击选 **[!UICONTROL Content]** 项卡。

   ![](assets/offer_content_create_001.png)

1. 填写优惠内容的各个字段。

   * **[!UICONTROL Title]** :指定要在优惠中显示的标题。 警告：这不是指优惠的标签，该标签在选项卡中定 **[!UICONTROL General]** 义。
   * **[!UICONTROL Destination URL]** :指定优惠的URL。 要正确处理，它必须开始为“http://”或“https://”。
   * **[!UICONTROL Image URL]** :指定优惠图像的URL或访问路径。
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** :在要使用的选项卡中输入优惠的正文。 要生成跟踪， **[!UICONTROL HTML content]** 必须由HTML元素组成，这些元素可以包含在类型 `<div>` 元素中。 例如，HTML页面中 `<table>` 元素的结果将如下所示：

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

   在接受建议时，配置状 [态部分会显示定义接受URL](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) 。

   ![](assets/offer_content_create_002.png)

   要查找在优惠空间配置过程中定义的必填字段，请单击链 **[!UICONTROL Content definitions]** 接以显示列表。 有关此内容的详细信息，请参阅 [创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_content_create_003.png)

   在此示例中，优惠必须包括标题、图像、HTML内容和目标URL。

## 预览优惠 {#previewing-the-offer}

一旦配置了优惠内容，您就可以预览优惠，就像收件人显示时一样。 操作步骤：

1. 单击选 **[!UICONTROL Preview]** 项卡。

   ![](assets/offer_preview_create_001.png)

1. 选择要优惠的表示形式。

   ![](assets/offer_preview_create_002.png)

1. 如果您已经个性化了优惠内容，请选择优惠目标以实现视图个性化。

   ![](assets/offer_preview_create_003.png)

## 在假设验证上创建优惠 {#creating-a-hypothesis-on-an-offer}

您可以在假设验证上创建优惠建议。 这样，您可以确定优惠对相关产品进行的购买的影响。

>[!NOTE]
>
>这些假设验证通过响应管理器进行。 请核实您的许可协议。

在假设验证上执行的优惠建议在其标签中被引 **[!UICONTROL Measure]** 用。

创建假设验证在本页 [中有详细介绍](../../campaign/using/about-response-manager.md)。

![](assets/offer_hypothesis_001.png)

