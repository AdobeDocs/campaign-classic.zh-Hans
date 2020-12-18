---
solution: Campaign Classic
product: campaign
title: 创建优惠空间
description: 创建优惠空间
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---


# 创建优惠空间{#creating-offer-spaces}

优惠空间创建只能由具有访问优惠空间子文件夹权限的&#x200B;**技术管理员**&#x200B;执行。 优惠空间只能在设计环境中创建，并在优惠批准过程中自动复制到实时环境中。

目录优惠的内容在优惠空间中配置。 默认情况下，内容可以包含以下字段：**[!UICONTROL Title]**、**[!UICONTROL Destination URL]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**&#x200B;和&#x200B;**[!UICONTROL Text content]**。 字段序列在优惠空间中配置。

高级参数允许您指定联系人标识键（例如，该标识键可由各种元素组成，名称和电子邮件字段等）。 有关详细信息，请参阅[演示已识别的优惠](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer)部分。

HTML或XML渲染是通过渲染函数创建的。 呈现函数中定义的字段序列必须与内容中配置的序列相同。

![](assets/offer_space_create_009.png)

要创建新优惠空间，请应用以下流程：

1. 转到优惠空间列表并单击&#x200B;**[!UICONTROL New]**。

   ![](assets/offer_space_create_001.png)

1. 选择要使用的渠道并更改优惠空间的标签。

   ![](assets/offer_space_create_002.png)

1. 如果以下情况之一适用于您，请选中&#x200B;**[!UICONTROL Enable unitary mode]**&#x200B;框：

   * 您正在使用与消息中心的交互
   * 您使用的是交互的酉模式（入站交互）

1. 转到&#x200B;**[!UICONTROL Content field]**&#x200B;窗口并单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/offer_space_create_003.png)

1. 转至&#x200B;**[!UICONTROL Content]**&#x200B;节点，按以下顺序选择字段：**[!UICONTROL Title]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**、**[!UICONTROL Destination URL]**。

   ![](assets/offer_space_create_004.png)

1. 选中&#x200B;**[!UICONTROL Required]**&#x200B;框，将每个字段设为必填字段。

   >[!NOTE]
   >
   >此配置在预览中使用，如果相关优惠中缺少某个必需元素，则会使优惠空间在发布时无效。 但是，如果优惠已在优惠空间上生存，则不会考虑这些标准。

   ![](assets/offer_space_create_005.png)

1. 单击&#x200B;**[!UICONTROL Edit functions]**&#x200B;可创建渲染函数。

   这些函数用于在优惠呈现上生成优惠空间。 可能有多种格式：用于出站交互的HTML或文本，用于入站交互的XML。

   ![](assets/offer_space_create_006.png)

1. 转到&#x200B;**[!UICONTROL HTML rendering]**&#x200B;选项卡并选择&#x200B;**[!UICONTROL Overload the HTML rendering function]**。
1. 插入您的渲染功能。

   ![](assets/offer_space_create_007.png)

如有必要，您可以使入站交互的XML渲染功能过载。 您还可以使出站交互的HTML和文本渲染功能过载。 有关详细信息，请参阅[关于入站渠道](../../interaction/using/about-inbound-channels.md)。

## 优惠建议状态{#offer-proposition-statuses}

优惠建议可以具有各种状态，具体取决于与目标群体的交互。 交互附带一组值，这些值可在优惠建议的整个生命周期中应用到该客户。 但是，您需要配置平台，以便在创建并接受优惠建议时状态发生变化。

>[!NOTE]
>
>优惠建议的状态不会立即更新。 它由每小时触发的跟踪工作流执行。

### 状态列表{#status-list}

交互附带以下可用于限定优惠建议状态的值：

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

默认情况下不应用这些值：它们必须配置。

>[!NOTE]
>
>如果优惠建议链接到状态为“已发送”的投放，则优惠的状态将自动更改为“已演示”。

### 配置创建命题时的状态{#configuring-the-status-when-the-proposition-is-created}

当交互引擎创建优惠建议时，其状态会发生更改，无论是入站交互还是出站交互。 这两个值之间的选择取决于在&#x200B;**[!UICONTROL Design]**&#x200B;优惠空间中配置环境的方式

对于每个空间，您可以根据要在优惠报表中显示的信息，配置创建命题时要应用的状态。

为此，请使用以下流程：

1. 转到所需空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡。
1. 选择要在建议创建时应用到的状态。

   ![](assets/offer_update_status_001.png)

### 配置接受命题时的状态{#configuring-the-status-when-the-proposition-is-accepted}

接受优惠建议后，您可以使用默认提供的值之一配置提议的新状态。 当收件人单击优惠中的链接（该链接调用交互引擎）时，更新会生效。

为此，请使用以下流程：

1. 转到所需空间的&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡。
1. 选择接受提案时要应用到的状态。

   ![](assets/offer_update_status_002.png)

**入站交互**

**[!UICONTROL Storage]**&#x200B;选项卡仅允许您定义&#x200B;**建议的**&#x200B;和&#x200B;**接受的**&#x200B;优惠建议的状态。 对于入站交互，应直接在URL中指定优惠建议的状态以调用优惠引擎，而不是通过接口。 这样，您就可以指定在其他情况下(例如，拒绝优惠建议)应用的状态。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，与&#x200B;**Neobank**&#x200B;站点上显示的&#x200B;**家庭保险**&#x200B;优惠符匹配的命题（标识符&#x200B;**40004**）包含以下URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

一旦访客单击优惠，从而将该URL应用于该提议，该访客被重定向到&#x200B;**[!UICONTROL Accepted]** Neobank **站点的新页面以履行保险合同。******

>[!NOTE]
>
>如果要在url中指定其他状态(例如，拒绝优惠建议)，请使用与所需状态对应的值。 示例：**[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot;等。
>
>状态及其值可以在&#x200B;**[!UICONTROL Offer propositions (nms)]**&#x200B;数据模式中检索。 有关详细信息，请参见[此页面](../../configuration/using/data-schemas.md)。

**出站交互**

如果出站交互，当优惠建议包含链接时，您可以自动将&#x200B;**[!UICONTROL Interested]**&#x200B;状态应用于投放。 只需将&#x200B;**_urlType=&quot;11&quot;**&#x200B;值添加到链接：

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 优惠预览每空间{#offer-preview-per-space}

在此选项卡中，您可以通过选定的方法视图收件人符合条件的优惠。 在以下示例中，收件人有资格通过邮件获得三个优惠建议。

![](assets/offer_space_overview_002.png)

如果收件人没有资格获得任何优惠，则预览中会显示此信息。

![](assets/offer_space_overview_001.png)

当预览被限制在空间时，上下文可以忽略这些数据。 这是当交互模式已扩展以使用入站渠道添加空间中引用的字段时（有关详细信息，请参阅[扩展示例](../../interaction/using/extension-example.md)）。
