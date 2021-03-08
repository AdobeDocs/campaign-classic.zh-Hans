---
solution: Campaign Classic
product: campaign
title: 创建优惠
description: 创建优惠
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 2%

---


# 创建优惠{#creating-an-offer}

## 创建优惠{#creating-the-offer}

要创建优惠，请应用以下步骤：

1. 转到&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡并单击&#x200B;**[!UICONTROL Offers]**&#x200B;链接。

   ![](assets/offer_create_001.png)

1. 单击 **[!UICONTROL Create]** 按钮。

   ![](assets/offer_create_005.png)

1. 更改标签并选择优惠应属于的类别。

   ![](assets/offer_create_002.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建优惠。

   ![](assets/offer_create_003.png)

   该优惠在平台中可用，并且可以配置其内容。

   ![](assets/offer_create_004.png)

## 配置优惠资格{#configuring-offer-eligibility}

在&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡中，定义优惠的有效期，并可显示该期间、要应用于目标和优惠权重的过滤器。

### 定义优惠{#defining-the-eligibility-period-of-an-offer}的资格期

要定义优惠的资格期，请使用下拉列表，然后在日历中选择开始和结束日期。

![](assets/offer_eligibility_create_002.png)

在这些日期之外，交互引擎不会选择优惠。 如果您还为优惠类别配置了资格日期，则限制最严格的期限将适用。

### 过滤器目标{#filters-on-the-target}

您可以将过滤器应用于优惠目标。

要执行此操作，请单击&#x200B;**[!UICONTROL Edit query]**&#x200B;链接，然后选择要应用的筛选器。 （请参阅[此部分](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)）。

![](assets/offer_eligibility_create_003.png)

如果已创建预定义过滤器，则可以从用户过滤器的列表中选择。 有关详细信息，请参阅[创建预定义过滤器](../../interaction/using/creating-predefined-filters.md)。

![](assets/offer_eligibility_create_004.png)

### 优惠权重{#offer-weight}

要使引擎能够在目标符合的优惠之间做出决定，您需要为优惠分配一个或多个权重。 如有必要，您还可以将过滤器应用于目标，或限制权重将应用到的优惠空间。 较之权重较少的优惠，更青睐具有更显着权重的优惠。

您可以为同一优惠配置多个权重，例如，区分子时段、特定目标甚至优惠空间。

例如，优惠可以具有A权重（对于年龄在18到25岁之间的联系人）和B权重（对于超过该范围的联系人）。 如果优惠在整个夏季都符合条件，它还可以在7月获得A权重，在8月获得B权重。

>[!NOTE]
>
>可以根据权重所属类别的参数临时修改指定的优惠。 有关详细信息，请参阅[创建优惠类别](../../interaction/using/creating-offer-categories.md)。

要在优惠中创建权重，请应用以下步骤：

1. 单击 **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. 更改标签并分配权重。 默认情况下，它为1。

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >如果未输入权重(0)，则目标将不被视为有资格获得优惠。

1. 如果您希望权重在给定期间内应用，请定义资格日期。

   ![](assets/offer_weight_create_002.png)

1. 如有必要，将权重限制为特定优惠空间。

   ![](assets/offer_weight_create_003.png)

1. 对目标应用滤镜。

   ![](assets/offer_weight_create_004.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;保存权重。

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >如果目标有资格对所选优惠进行多个权重，引擎将保持最佳（最高）权重。 在调用优惠引擎时，每个联系人的优惠最多被选择一次。

### 优惠合格规则{#a-summary-of-offer-eligibility-rules}摘要

配置完成后，合格规则摘要将在优惠仪表板上可用。

要视图它，请单击&#x200B;**[!UICONTROL Schedule and eligibility rules]**&#x200B;链接。

![](assets/offer_eligibility_create_005.png)

## 创建优惠内容{#creating-the-offer-content}

1. 单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Content]**&#x200B;选项卡。

   ![](assets/offer_content_create_001.png)

1. 填写优惠内容的各个字段。

   * **[!UICONTROL Title]** :指定要在优惠中显示的标题。警告：这不是引用优惠的标签，该标签在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中定义。
   * **[!UICONTROL Destination URL]** :指定优惠的URL。要正确处理，它必须开始为“http://”或“https://”。
   * **[!UICONTROL Image URL]** :指定优惠图像的URL或访问路径。
   * **[!UICONTROL HTML content]** /  **[!UICONTROL Text content]** :在要使用的选项卡中输入优惠的正文。要生成跟踪，**[!UICONTROL HTML content]**&#x200B;必须由HTML元素组成，这些元素可以包含在`<div>`类型元素中。 例如，HTML页中`<table>`元素的结果将如下所示：

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

   [配置接受主题时的状态](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted)部分中显示定义接受URL。

   ![](assets/offer_content_create_002.png)

   要查找在优惠空间配置过程中定义的必填字段，请单击&#x200B;**[!UICONTROL Content definitions]**&#x200B;链接以显示列表。 有关详细信息，请参阅[创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_content_create_003.png)

   在此示例中，优惠必须包括标题、图像、HTML内容和目标URL。

## 预览优惠{#previewing-the-offer}

一旦配置了优惠内容，您就可以预览优惠，就像的收件人一样。 操作步骤：

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。

   ![](assets/offer_preview_create_001.png)

1. 选择要视图的优惠的表示形式。

   ![](assets/offer_preview_create_002.png)

1. 如果您已个性化了优惠内容，请选择优惠目标以实现视图个性化。

   ![](assets/offer_preview_create_003.png)

## 在优惠{#creating-a-hypothesis-on-an-offer}上创建假设验证

您可以在优惠建议上创建假设验证。 这样，您就可以确定优惠对为相关产品进行的购买的影响。

>[!NOTE]
>
>这些假设验证通过响应管理器执行。 请核实您的许可协议。

在优惠建议上执行的假设验证在其&#x200B;**[!UICONTROL Measure]**&#x200B;选项卡中引用。

创建假设验证详见[此页](../../campaign/using/about-response-manager.md)。

![](assets/offer_hypothesis_001.png)

