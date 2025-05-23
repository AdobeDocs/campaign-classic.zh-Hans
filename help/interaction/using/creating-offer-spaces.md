---
product: campaign
title: 创建优惠空间
description: 创建优惠空间
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# 创建优惠空间{#creating-offer-spaces}



优惠空间创建只能由有权访问优惠空间子文件夹的&#x200B;**技术管理员**&#x200B;执行。 优惠空间只能在设计环境中创建，并在优惠批准期间自动复制到实时环境中。

目录选件的内容是在选件空间中配置的。 默认情况下，内容可以包含以下字段： **[!UICONTROL Title]**、**[!UICONTROL Destination URL]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**&#x200B;和&#x200B;**[!UICONTROL Text content]**。 字段序列在选件空间中配置。

高级参数允许您指定联系人标识键（例如，可同时由各种元素、名称和电子邮件字段组成）。 有关更多信息，请参阅[呈现已识别的选件](../../interaction/using/integration-via-javascript-client-side.md#presenting-an-identified-offer)部分。

HTML或XML渲染是通过渲染函数创建的。 渲染函数中定义的字段序列必须与内容中配置的序列相同。

![](assets/offer_space_create_009.png)

要创建新的选件空间，请应用以下流程：

1. 转到优惠空间列表，然后单击&#x200B;**[!UICONTROL New]**。

   ![](assets/offer_space_create_001.png)

1. 选择要使用的渠道并更改优惠空间的标签。

   ![](assets/offer_space_create_002.png)

1. 如果以下情况之一适用于您，请选中&#x200B;**[!UICONTROL Enable unitary mode]**&#x200B;框：

   * 您正在使用与消息中心的交互
   * 您使用的是交互的单一模式（入站交互）

1. 转到&#x200B;**[!UICONTROL Content field]**&#x200B;窗口并单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/offer_space_create_003.png)

1. 转到&#x200B;**[!UICONTROL Content]**&#x200B;节点并按以下顺序选择字段： **[!UICONTROL Title]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**、**[!UICONTROL Destination URL]**。

   ![](assets/offer_space_create_004.png)

1. 选中&#x200B;**[!UICONTROL Required]**&#x200B;框使每个字段成为必填字段。

   >[!NOTE]
   >
   >此配置在预览中使用，如果相关选件中缺少其中一个必需元素，则在发布时会使选件空间无效。 但是，如果优惠空间中已存在优惠，则不会考虑这些标准。

   ![](assets/offer_space_create_005.png)

1. 单击&#x200B;**[!UICONTROL Edit functions]**&#x200B;以创建渲染函数。

   这些函数用于在优惠空间上生成优惠呈现。 有多种可能的格式：出站交互的HTML或文本，以及入站交互的XML。

   ![](assets/offer_space_create_006.png)

1. 转到&#x200B;**[!UICONTROL HTML rendering]**&#x200B;选项卡并选择&#x200B;**[!UICONTROL Overload the HTML rendering function]**。
1. 插入渲染函数。

   ![](assets/offer_space_create_007.png)

如有必要，您可以重载入站交互的XML渲染函数。 您还可以重载出站交互的HTML和文本渲染函数。 有关详情，请参阅[关于入站渠道](../../interaction/using/about-inbound-channels.md)。

## 优惠建议状态 {#offer-proposition-statuses}

根据与目标群体的交互，优惠建议可以具有各种状态。 交互附带一组值，可在优惠建议整个生命周期中应用于这些值。 但是，您将需要配置平台，以便在创建和接受优惠建议时状态会更改。

>[!NOTE]
>
>优惠建议的状态不会立即更新。 跟踪由跟踪工作流执行，跟踪工作流每小时触发一次。

### 状态列表 {#status-list}

交互附带以下值，这些值可用于确定优惠建议的状态：

* **[!UICONTROL Accepted]**。
* **[!UICONTROL Scheduled]**。
* **[!UICONTROL Generated]**。
* **[!UICONTROL Interested]**。
* **[!UICONTROL Presented]**。
* **[!UICONTROL Rejected]**。

默认情况下不应用这些值：必须配置这些值。

>[!NOTE]
>
>如果优惠与状态为“已发送”的投放关联，则优惠建议的状态将自动更改为“已呈现”。

### 创建建议时配置状态 {#configuring-the-status-when-the-proposition-is-created}

当交互引擎创建优惠建议时，其状态会发生变化，无论它是入站还是出站交互。 这两个值之间的选择取决于&#x200B;**[!UICONTROL Design]**&#x200B;环境中选件空间的配置方式

对于每个空间，您可以根据要在选件报表中显示的信息，配置在创建建议时要应用的状态。

为此，请使用以下流程：

1. 转到所需空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡。
1. 选择创建建议时要应用于建议的状态。

   ![](assets/offer_update_status_001.png)

### 接受建议时配置状态 {#configuring-the-status-when-the-proposition-is-accepted}

接受优惠建议后，您可以使用默认提供的值之一来配置建议的新状态。 当收件人单击优惠中的链接（这将调用交互引擎）时，更新将生效。

为此，请使用以下流程：

1. 转到所需空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡。
1. 选择建议被接受时您希望应用于该建议的状态。

   ![](assets/offer_update_status_002.png)

**入站交互**

**[!UICONTROL Storage]**&#x200B;选项卡允许您仅定义&#x200B;**建议的**&#x200B;和&#x200B;**接受的优惠建议**&#x200B;的状态。 对于入站交互，应直接在用于调用优惠引擎的URL中指定优惠建议的状态，而不是通过界面指定。 这样，您将能够指定在其他情况下要应用的状态，例如，如果优惠建议被拒绝。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，与&#x200B;**Neobank400045&rbrace;网站上显示的**&#x200B;家庭保险&#x200B;**优惠匹配的建议（标识符**&#x200B;**）包含以下URL：**

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

只要访客单击了选件并因此单击了URL，就会将&#x200B;**[!UICONTROL Accepted]**&#x200B;状态（值&#x200B;**3**）应用于建议，并且访客将被重定向到&#x200B;**Neobank**&#x200B;网站的新页面以取消保险合同。

>[!NOTE]
>
>如果要在URL中指定其他状态（例如，如果优惠建议被拒绝），请使用与所需状态对应的值。 示例： **[!UICONTROL Rejected]** = &quot;5&quot;，**[!UICONTROL Presented]** = &quot;1&quot;，依此类推。
>
>可在&#x200B;**[!UICONTROL Offer propositions (nms)]**&#x200B;数据架构中检索状态及其值。 有关详细信息，请参见[此页面](../../configuration/using/data-schemas.md)。

**出站交互**

在叫客交互中，当投放包含链接时，您可以自动将&#x200B;**[!UICONTROL Interested]**&#x200B;状态应用于优惠建议。 只需将&#x200B;**_urlType=&quot;11&quot;**&#x200B;值添加到链接即可：

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 每个空间的优惠预览 {#offer-preview-per-space}

在此选项卡中，您可以查看收件人通过所选方法符合条件的优惠。 在下面的示例中，收件人可以通过邮件获得三个优惠建议。

![](assets/offer_space_overview_002.png)

如果收件人不符合任何优惠的条件，则会在预览中显示。

![](assets/offer_space_overview_001.png)

当上下文限制为空格时，预览可以忽略上下文。 当交互架构已扩展，使用入站渠道添加空间中所引用的字段时，就是这种情况（有关更多信息，请参阅[扩展示例](../../interaction/using/extension-example.md)）。
