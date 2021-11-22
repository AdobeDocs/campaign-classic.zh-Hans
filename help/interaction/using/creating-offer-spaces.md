---
product: campaign
title: 创建优惠空间
description: 创建优惠空间
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# 创建优惠空间{#creating-offer-spaces}

![](../../assets/v7-only.svg)

只能通过 **技术管理员** 具有对选件空间子文件夹的访问权限。 选件空间只能在设计环境中创建，并在选件批准期间自动复制到实时环境中。

目录选件的内容在选件空间中进行配置。 默认情况下，内容可以包含以下字段： **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** 和 **[!UICONTROL Text content]**. 字段序列在选件空间中进行配置。

高级参数允许您指定联系人标识键（例如，联系人标识键可由各种元素组成，例如名称和电子邮件字段）。 有关更多信息，请参阅 [呈现已识别的优惠](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 中。

HTML或XML渲染是通过渲染函数创建的。 呈现函数中定义的字段序列必须与内容中配置的序列相同。

![](assets/offer_space_create_009.png)

要创建新选件空间，请应用以下流程：

1. 转到选件空间列表，然后单击 **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. 选择要使用的渠道，并更改选件空间的标签。

   ![](assets/offer_space_create_002.png)

1. 检查 **[!UICONTROL Enable unitary mode]** 框中，以检查以下任一情况：

   * 您正在使用与消息中心的交互
   * 您使用的是交互的单一模式（集客交互）

1. 转到 **[!UICONTROL Content field]** 窗口，单击 **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. 转到 **[!UICONTROL Content]** 节点，然后按以下顺序选择字段： **[!UICONTROL Title]**，则 **[!UICONTROL Image URL]**，则 **[!UICONTROL HTML content]**，则 **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. 检查 **[!UICONTROL Required]** 框中，将每个字段设为必填字段。

   >[!NOTE]
   >
   >此配置用于预览，如果相关选件中缺少一个必需元素，则会使选件空间在发布时无效。 但是，如果选件已在选件空间上处于实时状态，则不会考虑这些标准。

   ![](assets/offer_space_create_005.png)

1. 单击 **[!UICONTROL Edit functions]** 创建渲染函数。

   这些函数用于在选件空间上生成选件表示形式。 有多种可能的格式：出站交互的HTML或文本，入站交互的XML。

   ![](assets/offer_space_create_006.png)

1. 转到 **[!UICONTROL HTML rendering]** 选项卡，选择 **[!UICONTROL Overload the HTML rendering function]**.
1. 插入您的渲染函数。

   ![](assets/offer_space_create_007.png)

如有必要，您可以使集客交互的XML渲染函数过载。 您还可以为出站交互使HTML和文本渲染功能过载。 有关更多信息，请参阅 [关于入站渠道](../../interaction/using/about-inbound-channels.md).

## 优惠建议状态 {#offer-proposition-statuses}

根据与目标群体的交互，选件建议可以具有各种状态。 交互附带一组值，这些值可在选件的整个生命周期中应用于该选件建议。 但是，您需要配置平台，以便在创建并接受选件建议时状态发生更改。

>[!NOTE]
>
>优惠建议的状态不会立即更新。 它由每小时触发的跟踪工作流执行。

### 状态列表 {#status-list}

交互附带以下值，可用于确定优惠建议的状态：

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

默认情况下，不会应用以下值：必须配置它们。

>[!NOTE]
>
>如果选件链接到状态为“已发送”的投放，则选件建议的状态将自动更改为“已显示”。

### 在创建建议时配置状态 {#configuring-the-status-when-the-proposition-is-created}

当交互引擎创建优惠建议时，无论它是集客交互还是出站交互，其状态都会发生更改。 这两个值之间的选择取决于 **[!UICONTROL Design]** 环境

对于每个空间，您可以根据要在选件报表中显示的信息配置在创建建议时要应用的状态。

为此，请使用以下过程：

1. 转到 **[!UICONTROL Storage]** 选项卡。
1. 选择创建建议时要应用于该建议的状态。

   ![](assets/offer_update_status_001.png)

### 在建议被接受时配置状态 {#configuring-the-status-when-the-proposition-is-accepted}

接受优惠建议后，您可以使用默认提供的值之一配置建议的新状态。 当收件人单击选件中的链接（该链接调用交互引擎）时，更新将生效。

为此，请使用以下过程：

1. 转到 **[!UICONTROL Storage]** 选项卡。
1. 选择要在建议被接受时应用于该建议的状态。

   ![](assets/offer_update_status_002.png)

**入站互动**

的 **[!UICONTROL Storage]** 选项卡，用于定义状态 **建议** 和 **接受** 仅提供建议。 对于集客交互，应直接在用于调用选件引擎的URL中指定选件主张的状态，而不是通过界面指定。 这样，您就可以指定在其他情况下应用的状态，例如，如果选件建议被拒绝。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，建议（标识符） **40004**) **家庭保险** 选件 **尼奥班克** 网站包含以下URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

当访客单击该选件（从而单击该URL）时， **[!UICONTROL Accepted]** 状态（值） **3**)，且访客将被重定向到的新页面 **尼奥班克** 地点以履行保险合同。

>[!NOTE]
>
>如果您想要在URL中指定其他状态（例如，如果选件建议被拒绝），请使用与所需状态对应的值。 示例： **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** =“1”等。
>
>可以在 **[!UICONTROL Offer propositions (nms)]** 数据架构。 有关详细信息，请参见[此页面](../../configuration/using/data-schemas.md)。

**叫客互动**

对于叫客互动，您可以自动应用 **[!UICONTROL Interested]** 投放包含链接时的选件建议状态。 只需将 **_urlType=&quot;11&quot;** 值：

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 每个空间的选件预览 {#offer-preview-per-space}

在此选项卡中，您可以通过所选方法查看收件人有资格查看的选件。 在以下示例中，收件人有资格通过邮件获得三个选件建议。

![](assets/offer_space_overview_002.png)

如果收件人不符合任何选件的条件，则会在预览中显示该选件。

![](assets/offer_space_overview_001.png)

当上下文被限制为空格时，预览可以忽略这些上下文。 当交互架构已扩展为使用集客渠道添加空间中引用的字段时，便会出现这种情况(有关更多信息，请参阅 [扩展示例](../../interaction/using/extension-example.md))。
