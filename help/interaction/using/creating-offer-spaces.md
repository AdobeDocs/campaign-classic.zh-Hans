---
title: 创建选件空间
seo-title: 创建选件空间
description: 创建选件空间
seo-description: null
page-status-flag: never-activated
uuid: 2ad38697-db14-4dc0-abb8-9b71d57e0e35
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 0fae2149-0980-466d-ac9e-8afec2e278be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# 创建选件空间{#creating-offer-spaces}

只有有权访问选件空间子文件夹的 **技术管理员** ，才能创建选件空间。 优惠空间只能在设计环境中创建，并在优惠批准过程中自动复制到实时环境中。

目录选件的内容在选件空间中进行配置。 默认情况下，内容可以包括以下字段： **[!UICONTROL Title]**、 **[!UICONTROL Destination URL]****[!UICONTROL Image URL]**、 **[!UICONTROL HTML content]** 和 **[!UICONTROL Text content]**。 字段序列在选件空间中进行配置。

高级参数允许您指定联系人标识键（例如，该标识键可由各种元素组成，例如名称和电子邮件字段）。 有关详细信息，请参阅演 [示已识别的优惠](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 。

HTML或XML渲染是通过渲染函数创建的。 渲染函数中定义的字段序列必须与内容中配置的序列相同。

![](assets/offer_space_create_009.png)

要创建新的选件空间，请应用以下流程：

1. 转到选件空间列表并单击 **[!UICONTROL New]**。

   ![](assets/offer_space_create_001.png)

1. 选择要使用的渠道并更改选件空间的标签。

   ![](assets/offer_space_create_002.png)

1. 如果以 **[!UICONTROL Enable unitary mode]** 下情况之一适用于您，请选中此框：

   * 您正在使用与消息中心的交互
   * 您使用的是交互的酉模式（入站交互）

1. 转到窗 **[!UICONTROL Content field]** 口并单击 **[!UICONTROL Add]**。

   ![](assets/offer_space_create_003.png)

1. 转到节 **[!UICONTROL Content]** 点并按以下顺序选择字段： **[!UICONTROL Title]**&#x200B;然后 **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]**&#x200B;然后 **[!UICONTROL Destination URL]**。

   ![](assets/offer_space_create_004.png)

1. 选中该 **[!UICONTROL Required]** 框可将每个字段设为必填字段。

   >[!NOTE]
   >
   >此配置用于预览，如果相关选件中缺少某个必需元素，则发布时会使选件空间无效。 但是，如果选件已在选件空间上实时，则不会考虑这些条件。

   ![](assets/offer_space_create_005.png)

1. 单击 **[!UICONTROL Edit functions]** 可创建渲染功能。

   这些函数用于在选件空间上生成选件表示。 有几种可能的格式：用于出站交互的HTML或文本，用于入站交互的XML。

   ![](assets/offer_space_create_006.png)

1. 转到选项卡 **[!UICONTROL HTML rendering]** 并选择 **[!UICONTROL Overload the HTML rendering function]**。
1. 插入您的渲染功能。

   ![](assets/offer_space_create_007.png)

如有必要，您可以使入站交互的XML渲染功能过载。 您还可以使出站交互的HTML和文本渲染功能过载。 有关详细信息，请参阅关于 [入站渠道](../../interaction/using/about-inbound-channels.md)。

## 优惠主张状态 {#offer-proposition-statuses}

根据与目标人群的交互情况，选件主张可以具有各种状态。 交互附带一组值，这些值可在产品的整个生命周期中应用于该选件。 但是，您需要配置平台，以便在创建并接受选件主张时，状态会发生变化。

>[!NOTE]
>
>优惠提议的状态不会立即更新。 它由每小时触发的跟踪工作流执行。

### 状态列表 {#status-list}

交互包含以下值，这些值可用于确定优惠主张的状态：

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

默认情况下不应用这些值：它们必须进行配置。

>[!NOTE]
>
>如果选件链接到具有“已发送”状态的交付，则选件主张的状态将自动更改为“已演示”。

### 配置创建主张时的状态 {#configuring-the-status-when-the-proposition-is-created}

当交互引擎创建选件主题时，其状态会发生更改，无论是入站交互还是出站交互。 这两个值之间的选择取决于在环境中配置选件空间的方 **[!UICONTROL Design]** 式

对于每个空间，您可以根据要在选件报告中显示的信息，配置在创建命题时要应用的状态。

为此，请使用以下过程：

1. 转到所需 **[!UICONTROL Storage]** 空间的选项卡。
1. 选择要在建议创建时应用到的状态。

   ![](assets/offer_update_status_001.png)

### 配置接受主张时的状态 {#configuring-the-status-when-the-proposition-is-accepted}

一旦某个选件提案被接受，您就可以使用默认提供的值之一配置该提案的新状态。 当收件人单击选件中的链接（该链接调用交互引擎）时，更新会生效。

为此，请使用以下过程：

1. 转到所需 **[!UICONTROL Storage]** 空间的选项卡。
1. 选择您要在建议被接受时应用到的状态。

   ![](assets/offer_update_status_002.png)

**入站交互**

该选 **[!UICONTROL Storage]** 项卡仅允许您为建议和已接受 **的选** 件命 **题定义状态** 。 对于入站交互，应直接在URL中指定选件主张的状态，以调用选件引擎，而不是通过界面。 这样，您就可以指定在其他情况下（例如，如果优惠主张被拒绝）应用的状态。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，与Neobank站点上显示的 **Home insurance** offer（家庭保险产品）匹配的主张(标识符 **40004****** )包含以下URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

访客一旦单击优惠并因此单击URL，状态( **[!UICONTROL Accepted]** value **3**)便会应用于该主张，访客会被重定向到 **Neobank** 网站的新页面以签订保险合同。

>[!NOTE]
>
>如果要在url中指定其他状态（例如，如果选件提议被拒绝），请使用与所需状态对应的值。 示例： **[!UICONTROL Rejected]** =&quot;5&quot;, **[!UICONTROL Presented]** =&quot;1&quot;等。
>
>可以在数据架构中检索状态及其 **[!UICONTROL Offer propositions (nms)]** 值。 有关详细信息，请参见[此页面](../../configuration/using/data-schemas.md)。

**出站交互**

在出站交互的情况下，当分发包含链接时，您 **[!UICONTROL Interested]** 可以自动将状态应用于选件主张。 只需将 **_urlType=&quot;11&quot;值添加到链接** :

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 按空间提供预览 {#offer-preview-per-space}

在此选项卡中，您可以通过选择的方法查看收件人有资格获得的选件。 在以下示例中，收件人有资格通过邮件获得三个优惠建议。

![](assets/offer_space_overview_002.png)

如果收件人没有资格获得任何选件，预览中将显示此信息。

![](assets/offer_space_overview_001.png)

当上下文被限制在某个空间时，预览可以忽略这些上下文。 当交互架构已扩展到使用入站渠道添加空间中引用的字段时，即为此情况(有关详细信息，请参阅 [扩展示例](../../interaction/using/extension-example.md))。
