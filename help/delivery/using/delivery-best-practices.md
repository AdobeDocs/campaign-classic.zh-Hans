---
title: 活动投放最佳实践
seo-title: 投放最佳实践
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4548eda6f87566398ddf19131b777012cbf8917b
workflow-type: tm+mt
source-wordcount: '4361'
ht-degree: 4%

---


# 投放最佳实践 {#delivery-best-practices}

了解与投放设计和与Adobe Campaign一起发送相关的最佳实践。

## 优化投放 {#optimize-delivery}

在开始创建投放之前，您可以采取多项操作来保护并优化上游发送过程。

以下部分概述了最佳Adobe Campaign配置的最佳实践和建议步骤。 遵循这些做法将最大限度地减少您可能遇到的下游问题。

### 平台性能

几个因素会直接影响服务器性能并降低平台速度：

* 个性化元素的数量和类型： 电子邮件中的个性化会为每个收件人从数据库中提取数据。 如果存在许多个性化元素，则会增加准备投放所需的数据量。  在本节中进一步了解 [个性化](../../delivery/using/about-personalization.md)

* 服务器加载： 当营销服务器同时处理许多不同的任务时，它会降低性能。 营销服务器需要协调所有投放的所有传入和传出数据，以确保数据准确、及时。

   **提示** -为避免这种情况，请与团队中的其他成员协调投放的安排以确保最佳性能。

* 工作流执行： 监控工作流对于避免平台性能问题至关重要。 请遵循本文档 [中列出的准则](../../workflow/using/workflow-best-practices.md#execution-and-performance)。

* 作为托管客户，您可以利用 [活动控制面板功能](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) ，使用性能监 [控功能监控平台](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) 。

### 检查网络配置 {#network-config}

要在处理大量电子邮件时优化投放并避免被误认为是垃圾邮件发送者，请确保您拥有合法的网络配置，该配置不会尝试隐藏服务器的标识。

**提示**:  使用与您品牌网站对应的透明发件人地址。 例如，旅行社公司管理华伦天奴连锁酒店。 它拥有其网站的valentino.com域。 为了推广巴黎的华伦天奴酒店，它使用paris.valentino.com子域。 因此，相关发件人地址可以是hotel@paris.valentino.com。

### 可交付性管理 {#deliverability-management}

要访问收件人的收件箱而不弹回或标记为垃圾邮件，您需要提高邮件的发送率。

* 什么是可交付性？

   * 它指决定电子邮件被收件人服务器接受的能力的因素。 ISP(Internet服务提供商)过滤其标识为垃圾邮件的电子邮件，或阻止图像下载。 如果他们确定某个域发送的电子邮件过多，他们将对接受该发件人的电子邮件数量设置限制。

   * 在检查电子邮件的可交付性时，您希望关注四个主要类别: 数据质量、消息和内容、发送基础架构和声誉。 有关此主题的更深入介绍，请参 [阅此部分](../../delivery/using/about-deliverability.md)。

* 应用此文档中 [详细的建议](../../delivery/using/deliverability-key-points.md)。

* 请与Adobe代表联系以获得帮助。

### 隔离管理 {#quarantine-management}

保持良好的隔离管理流程符合您的最佳利益。

开始在新平台上发送电子邮件时，您可能会使用列表未完全限定的地址。 如果您发送到无效地址或蜜罐地址（仅为欺骗垃圾邮件发送者而创建的邮箱），这将开始您平台的声誉。 良好的隔离管理流程有助于： 保持地址质量，避免因特网访问提供商的阻止列表，并降低错误率，加快投放和吞吐量。

**提示**

* 如果列表的地址无效，Adobe建议通过> >将其导入到隔离 **[!UICONTROL Administration]** 表 **[!UICONTROL Campaign Management]** 中 **[!UICONTROL Non deliverables Management]** 。 **[!UICONTROL Non deliverables and addresses]**

* 在投放分析中，默认情况下将排除其地址被隔离的收件人: 他们不是目标。 这样可加快投放速度，因为错误率对投放速度有显著的影响。可以隔离电子邮件地址，例如，当收件箱已满或地址不存在时。 [了解更多](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign根据返回的错误类型管理错误地址。 有关更多信息，请参阅[此章节](../../delivery/using/understanding-quarantine-management.md)。


* 如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离允许您避免被这些提供商添加到阻止列表。

* 隔离管理还将通过排除投放的错误电话号码来帮助降低短信发送成本。

### 多次加入机制 {#double-opt-in}

为了避免向无效地址发送消息、限制不当通信并提高发送者信誉，Adobe建议实施多次选择加入机制以进行订阅后确认。 这有助于确保收件人有意订阅。

本节概述了实施这一机制 [的详细信息](../../web/using/use-cases--web-forms.md)。

## 使用模板 {#use-templates}

投放模板为大多数常见类型的活动提供现成方案，从而提高效率。 借助模板，营销人员可以在更短的时间内以最少的自定义次数部署新活动。

在本节中进一步了 [解投放模板](../../delivery/using/creating-a-delivery-template.md)。

### 开始使用投放模板 {#gs-templates}

投放模板 [使](../../delivery/using/creating-a-delivery-template.md) 您只需定义一组技术属性和功能属性，这些属性可以满足您的需求，并且可以再用于将来的投放。 然后，您可以节省时间并在需要时实现投放标准化。

在Adobe Campaign中管理多个品牌时，Adobe建议每个品牌有一个子域。 例如，银行可以具有与其每个区域机构对应的多个子域。 如果银行拥有bluebank.com域，其子域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每个子域有一个投放模板使您始终能够为每个品牌使用正确的预配置参数，从而避免错误并节省您的时间。

**提示**:  为避免在Campaign Standard中出现配置错误，我们建议您重复本机模板并更改其属性，而不是创建新模板。

### 配置地址

* 发送者的地址是强制性的，允许发送电子邮件。

* 某些ISP(Internet服务提供商)在接受消息前检查发送者地址的有效性。

* 格式不良的地址可能导致接收服务器拒绝它。 您必须确保提供正确的地址。

* 地址必须明确标识发件人。 域必须由发送方拥有并注册。

* Adobe建议创建与为投放和回复指定的地址对应的电子邮件帐户。 请咨询邮件系统管理员。

要在活动接口中配置地址，请执行以下步骤：

1. 在投放模板 [中](../../delivery/using/creating-a-delivery-template.md)，单击该 **[!UICONTROL From]** 链接。 在窗口 **[!UICONTROL Email header parameters]** 中，填写以下字段：

   ![](assets/d_best_practices_email_header.png)

1. 在字 **[!UICONTROL Sender address]** 段中，确保地址域与您委托给Adobe的子域相同。 可以更改“@”之前的部分，但不能更改域地址。

1. 在字 **[!UICONTROL From]** 段中，使用收件人可轻松识别的名称（如您的品牌名称）来提高投放的开业率。 要进一步改善收件人的体验，您可以添加人名，例如“Emma from Megastore”。

1. 在字 **[!UICONTROL Reply address text]** 段中，发送者的地址默认用于回复。 但是，Adobe建议使用现有的真实地址，如您品牌的客户关怀。 在这种情况下，如果收件人发送回复，客户服务中心将能够处理。

### 设置对照组

发送投放后，您可以将被排除收件人的行为与收到投放的收件人进行比较。 然后，您可以衡量活动的效率。 进一步了解 [对照组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

要设置对照组，请单击链 **[!UICONTROL To]** 接。 在窗口 **[!UICONTROL Select target]** 中，选择选 **[!UICONTROL Control group]** 项卡。 您可以提取目标的一部分，例如5%的随机样本。

![](assets/d_best_practices_control_group.png)

### 使用类型应用过滤器或控制规则

类型学包含在分析阶段应用的检查规则，然后发送任何消息。

在模 **[!UICONTROL Typology]** 板属性的选项卡中，根据您的需要更改默认类型。

例如，为了更好地控制出站流量，您可以通过为每个子域定义一个关联，为每个关联创建一个类型来定义可以使用的IP地址。 关联在实例的配置文件中定义。 与Adobe Campaign管理员联系。

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## 设计和个性化 {#design-and-personalize}

在设计消息内容时，请尝试避免可能妨碍您执行投放的常见问题。 大多数时候，可能的错误都与个性化 [、格式](../../delivery/using/about-personalization.md)[和图](../../delivery/using/defining-the-email-content.md#message-content) 像相 [关](../../delivery/using/defining-the-email-content.md#adding-images)。

### 优化个性化 {#optimize-personalization}

为避免常见问题，这些问题可能会妨碍您执行投放并改善收件人体验，Adobe Campaign使您能够个性化您的信息。

您可以使用存储在Adobe Campaign数据库中或通过跟踪、登陆页、订阅等收集的收件人数据。
本节介绍个性化基 [础知识](../../delivery/using/personalization-fields.md)。

确保您的消息内容设计得正确，以避免任何与个性化一般相关的错误。

**提示**: 在来自第三方供应商提供的外部文件的个性化字段中，外部HTML内容可能出错。 要避免这种情况，请检查语法、使用标记、字符等。 例如，Adobe Campaign个性化标签始终具有以下表单： &lt;%=table.field%>。 有关更多信息，请参阅[此章节](../../delivery/using/about-personalization.md)。

在个性化块中使用参数不正确可能是个问题。 例如，JavaScript中的变量应当如下：

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

有关个性化块的详细信息，请参 [阅本部分](../../delivery/using/personalization-blocks.md)。

您可以在工作流中准备个性化数据，以提高投放准备分析。 如果个性化数据是通过联合数据访问(联合数据访问)从外部表中获得的，则应特别使用此选项。 此部分介绍此 [选项](../../delivery/using/personalization-fields.md#optimizing-personalization)

### 构建优化内容 {#optimize-content}

在构建电子邮件时，请牢记以下一般最佳实践。

* 使设计变得简单

* 让移动用户注意

* 避免完全基于图像的电子邮件

* 使用电子邮件安全字体

* 对特殊字符进行编码

**主题行** -在主题行 [上工作](../../delivery/using/defining-the-email-content.md#message-content) ，以提高开放率：

* 避开过长的科目。 最多使用50个字符

* 避免重复使用“free”或“优惠”等可能被视为垃圾邮件的词语

* 避免大写字母和特殊字符，如“!”、“£”、“€”、“$”

**镜像页面** -始终包含镜像页面链接。 首选职位是电子邮件的顶部。 [了解更多](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**退订链接** -退订链接是必需的。 它必须可见且有效，并且表单必须有效。 默认情况下，在分析消息时， [类型规则](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) 会检查是否包含退出链接，并在消息缺失时生成警告。

**提示**: 由于总是可能出现人为错误，因此在每次发送之前，请检查退出链接是否工作正常。 例如，发送验证时，请确保链接有效、表单联机且“不再与此收件人联系”字段更改为“是”。

了解如何在此部分插入 [退出链接](../../delivery/using/personalization-blocks.md#personalization-blocks-example)。

**电子邮件大小** -为避免性能或可交付性问题，建议电子邮件的最大大小约为35 **KB**。 要检查邮件大小，请转到选 **[!UICONTROL Preview]** 项卡并选择测试用户档案。 生成后，消息大小将显示在右上角。

要限制您的电子邮件，请考虑以下事项：

* 删除冗余或未使用的样式

* 将部分电子邮件内容移至登陆页

* 简化代码

确保在最终发送之前测试任何更改

**SMS长度**

默认情况下，短信的字符数应符合 GSM（全球移动通信系统）标准。使用 GSM 编码的短信消息长度上限为 160 个字符，而对于分段发送的消息，每段短信的长度上限为 153 个字符。

音译指的是，如果 GSM 标准无法识别某个短信字符，则会用另一个字符替换该字符。请注意，在SMS消息内容中插入个性化字段可能会引入GSM编码未考虑的字符。 您可以通过选中相应SMPP渠道设置选项卡中的相应框来授权字符音译 **[!UICONTROL External account]**。
在本节 [中了解更多](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

**提示**:

* 要保留SMS消息中的所有字符，如不更改正确的名称，请不启用音译。

* 但是，如果您的SMS消息包含大量GSM标准未考虑的字符，则允许音译以限制发送消息的成本。

在本节 [中了解更多](../../delivery/using/sms-channel.md#about-character-transliteration)。

### 处理格式 {#formatting}

要避免常见格式错误，请检查以下元素：

* 更正日 **期格式**: Adobe Campaign为JavaScript模板和XSL样式表提供日期格式化功能。 [了解更多](../../delivery/using/formatting.md#date-display)

* 在电子邮件 **中使用** 授权字符： 电子邮件地址的有效字符列表在“XtkEmail_Characters”选项中定义。 了解如何访问本节 [中的活动选项](../../installation/using/configuring-campaign-options.md)。 要正确处理特殊字符，需要在Unicode中安装Adobe Campaign。

* 电子邮件身 **份验证配置**: 确保电子邮件标头包含DKIM签名。 DKIM（域密钥标识邮件）身份验证允许接收电子邮件服务器验证消息确实是由其声称其发送消息的个人或实体发送的，以及消息内容在最初发送（和DKIM“签名”）到接收时间之间是否发生了更改。 此标准通常使用发件人或发件人标题中的域。 有关更多信息，请参阅[此章节](../../delivery/using/technical-recommendations.md#dkim)。

* **响应式电子邮件设计** ，可确保电子邮件在打开时的设备上呈现最佳效果。

   * 使用响应式电子邮件HTML而非Web HTML。

   * 使用预览模式并发送验证，以在尽可能多的设备上测试渲染。

   * Adobe Campaign Classic数字内容编辑器(数字内容编辑器)模块包括一些响应式设计格式模板，用于移动设 **[!UICONTROL Resources]** 备，可 **[!UICONTROL Templates]** 通过> **[!UICONTROL Content templates]**>。 在本文中 [了解更多信息](https://theblog.adobe.com/responsive-email-design-101/)。



### 管理图像 {#manage-images}

在使用图像时，请遵循以下准则。

* **防止图像阻塞** -默认情况下，某些电子邮件客户端会阻止图像，而一些用户会更改其设置以阻止图像以保存数据使用情况。 因此，如果不下载图像，则会丢失整个消息。 要避免这种情况：

   * 在内容与图像和文本之间取得平衡。 避免完全基于图像的电子邮件。

   * 如果图像中必须包含文本，请使用替代文本和标题文本来确保消息传递过来。 设置替代／标题文本的样式以改进其外观。

   * 避免使用背景图像，因为某些电子邮件客户不支持这些图像。

* **使图像成为响应式** -尝试使图像成为响应式图像并且可调整大小。 请注意，这可能会造成成本影响，因为构建时间较长。

* **使用绝对图像引用** -要从外部访问，链接到活动的电子邮件和公共资源中使用的图像必须存在于可从外部访问的服务器上。

   * 您可以检查实例配置是否启用公共资源管理。 [了解更多](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * 在该投放向导中，您可以导入包含图像的HTML页面，或直接使用HTML编辑器通过图标插入 **[!UICONTROL Image]** 图像。 [了解更多](../../delivery/using/defining-the-email-content.md#adding-images)

   * 如果未显示图像，请检查这些图像是否在服务器上可用。 为此，请单击投放中的“源”选项卡。 在Web浏览器中查找图像并复制粘贴每个图像的URL。 如果未显示图像，请与IT管理员或提供投放内容的第三方供应商联系。

### 预览您的消息 {#preview-msg}

Adobe建议预览您的消息，检查其个性化以及收件人将如何看到您的投放。

* 在投放向导中， **[!UICONTROL Preview]** 通过子选项卡可以视图收件人的每个内容的呈现。 个性化字段和内容的条件元素被替换为所选用户档案的相应信息。 [了解更多](../../delivery/using/defining-the-email-content.md#message-content)

* 在每个预览期间执行自动防垃圾邮件检查。 在子选 **[!UICONTROL Preview]** 项卡中，检查SpamAssassin [垃圾邮件](../../delivery/using/spamassassin.md) 评分。  单击 **[!UICONTROL More...]** 以进一步了解警告。  在执行此操作之前，请确保在Adobe Campaign应用程序服务器上正确安装和配置了SpamAssassin。 [了解更多](../../installation/using/configuring-spamassassin.md)

## 定义正确的目标 {#define-the-right-target}

目标人口是关键： 仔细构建列表，在流行的电子邮件客户端和移动设备上测试电子邮件，并确保电子邮件列表始终处于最新状态（没有未知或过时的地址）。 您还可以发送帮助设置完整验证周期的验证。

在本节中进一步了 [解目标群](../../delivery/using/steps-defining-the-target-population.md)

### 目标正确的受众 {#target-the-right-audience}

当您的内容准备就绪后，您需要仔细定义将收到您的消息的人。

为了使投放成功，您希望将最相关的个性化内容发送给正确的收件人。 Adobe Campaign使您能够构建最准确的目标: 您可以根据收件人的年龄、本地化、他们购买的商品，如果他们点击了先前投放中的链接，等等。 使用Adobe Campaign，您还可以定义测试用户档案、对照组和种子地址，以确保目标正确。

### 目标映射 {#target-mappings}

在Campaign Classic中，默认情况下为投放模板收件人 **目标**。 Adobe Campaign为投放优惠其他目标映射，您可以根据需要进行更改。

例如，您可以将用户档案交付给通过社交网络收集的访客或订阅信息服务的访客。

本节将介绍这 [些映射](../../delivery/using/selecting-a-target-mapping.md)。

您还可以创建和使用自定义目标映射。 有关更多信息，请参阅[此章节](../../configuration/using/target-mapping.md)。

### 外部收件人 {#external-recipients}

您可以将存储在外部文件而非保存在收件人库中的传送到该数据库。 在本节 [中了解更多](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

### 发送给您的订阅者 {#send-to-subscribers}

要向新闻稿的订阅者发送消息，您可以直接将订阅者目标到相应的信息服务。 在本节 [中了解更多](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)。


### 测试收件人和种子地址 {#test-recipients-seed-addresses}

要测试投放，请在发送到主目标前使用验证。

请确保您选择适当的验证收件人，因为它们会验证表单和消息的内容。 定义验证收件人的步骤将在 [本节中介绍](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)。

种子地址用于目标不符合定义的目标标准的收件人，以便在发送到主目标之前测试投放。 本节将介 [绍这些内容](../../delivery/using/about-seed-addresses.md)。

### 消除重复地址 {#deduplicate-addresses}

请务必避免重复电子邮件地址，因为这可能会影响您的目标:

* 在拆分目标时，可以多次发送同一消息。

* 如果收件人在收到消息后取消订阅，其重复用户档案仍将收到将来的消息。

消除重复地址可保护您的发送信誉并确保良好的隔离管理。

通过此用 [例了解更多信息](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)。


### 索引电子邮件地址 {#index-addresses}

要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

本节将介绍向电子邮件地址添加索引 [的步骤](../../configuration/using/database-mapping.md#indexed-fields)。

## 发送前执行所有检查 {#perform-all-checks}

消息准备就绪后，请确保其内容在所有设备上均正确显示，且不包含任何错误，如错误的个性化或中断的链接。

在发送消息之前，还应确保参数和配置与投放一致。

### 验证为何重要 {#validation-is-key}

在发送投放之前，您需要确保收件人将收到您真正希望发送的消息。 为此，您需要验证消息内容和投放参数。

通过此步骤，您可以检测可能的错误并修复它们，然后再将其传送到主目标。

本节介绍验证投放 [的步骤](../../delivery/using/steps-validating-the-delivery.md)。

### 收件箱呈现 {#inbox-and-email-rendering}

收件箱呈现使您能够在主要电子邮件客户端预览邮件、扫描内容和声誉、发现收件人阅读邮件的方式。

**提示**:

* 您可以在收到邮件的不同视图中上下文发送的邮件： Web邮件、邮件服务、移动等。

* 收件箱呈现功能对于确定您的电子邮件活动是否成功地使其超过主要ISP(Internet服务提供商)和Web邮件服务的过滤器至关重要。 此类工具会将电子邮件的预检副本发送到测试收件箱网络，以便您能够查看消息在这些服务中的显示或呈现方式。 它们还可能包括报告和代码更正选项，可帮助您快速识别并进行可改进交付性的修复。

在本节 [中了解更多](../../delivery/using/inbox-rendering.md)。

### 验证消息 {#proof-messages}

发送验证使您能够检查退出链接、镜像页面和任何其他链接、验证消息、验证图像是否显示、检测可能的错误等。 您可能还希望检查在不同设备上的设计和渲染。

在本节 [中了解更多](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 设置A/B测试投放 {#a-b-testing-deliveries}

如果电子邮件投放有多个内容，则可以使用A/B测试找出哪个版本对目标人群的影响最大。

**提示**:

* 将不同版本发送给您的某些收件人

* 选择成功率最高的目标，并将其发送至其他

在本节 [中了解更多](../../workflow/using/a-b-testing.md)。

### 确保您的消息已送达 {#make-sure-your-message-is-delivered}

最后一步，充分利用你的机会，利用Adobe Campaign Classic的力量，确保你的信息真正传递给相关收件人。

**执行验证流程** -您可以定义一个包含Adobe Campaign运算符和组的完整验证流程，以验证目标和消息内容。 这将确保全面监测和控制该活动的各种进程： 定位、内容、预算、提取和发送验证。 根据用户的权限，用户将收到通知、接收验证并能够验证或拒绝消息。 在本节 [中了解更多](../../campaign/using/marketing-campaign-approval.md#approval-process)。

**使用批次** -您可以逐步增加使用批次发送的音量。 这将避免您的邮件被标记为垃圾邮件，或者您希望限制每天的邮件数。 使用批次，您可以将投放分为几批，而不是同时发送大量消息。 在本节 [中了解更多](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

**排定消息** 优先级——您可以通过声明优先级来设置投放的发送顺序。 为实现此操作，请执行以下步骤：

1. 编辑投放属性，然后选择选 **[!UICONTROL Delivery]** 项卡。

1. 定义投放从到的比例的优先级 **[!UICONTROL Very low]** 别 **[!UICONTROL Very high]**。

>[!NOTE]
>
>无法从投放中定义发送消息的顺序。

**设置IP关联** -要更好地控制出站SMTP通信，可通过定义每个关联可使用哪些特定IP地址来管理关联。 这样，您就可以将特定投放的电子邮件数量限制到计算机或输出地址。 例如，您可以在每个国家／地区或子域使用一个关联。 然后，您可以为每个国家／地区创建一种类型学，并将每种关联关联到相应的类型学。

您可以：

* 在serverConf.xml配置文件中定义IP关联。 [了解更多](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 对于每个IPAfinity元素，声明可使用的IP地址。 [了解更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在您 [选择](../../campaign/using/about-campaign-typologies.md) 的排版中，使用 **[!UICONTROL Managing affinities with IP addresses]** 该字段将投放链接到投放服务器(MTA)，该服务器管理所述关联。 [了解更多](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* 发送电子邮件后，检查标题以验证投放从哪个IP地址发送。 电子邮件管理员应帮助您获取标题信息。

>[!NOTE]
>
>这些步骤大多只能由专家用户执行。

**使用类型规则** -您可以使用目标根据特定条件排除部分。 这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。例如，您可以从新闻稿的目标中过滤未达到规定的收件人。 通过此示 [例了解更多信息](../../campaign/using/filtering-rules.md)。

**避免附件** -附件仍然是导致恶意软件激增的最常见的矢量之一，尤其是当它们批量发送时。 包括指向文档的安全链接，而不是附加它。 这确保了额外的安全层以防止意外的重新分发，并且极大地降低了由于邮件大小或安全原因在入站电子邮件网关处拒绝邮件的可能性。

## 跟踪和监视 {#track-and-monitor}

您单击了“发送”按钮？ 让我们看看会发生什么。 发送投放后，Adobe Campaign使您能够跟踪已发送的消息并了解收件人对投放的反应。 这将帮助您改进未来发送并优化您的下一活动。

### 监视投放 {#monitoring-deliveries}

要控制活动，您必须确保消息确实已送达收件人。

从活动投放仪表板中，您可以检查已处理的消息和投放审计日志。
您还可以控制投放日志中消息的状态。 [了解更多](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

如果投放未被发送，且其状态仍为“待 **定”**?

* 执行过程正在等待某些资源的可用性。 MTA可能尚未启动。
检查您的mta@instance模块是否已在MTA服务器上启动，并在必要时开始MTA模块。 [了解更多](../../production/using/administration.md).

* 投放可能正在使用尚未在发送实例上配置的关联。
提示： 检查流量管理(IP关联)的配置。 有关详细信息，请参阅控制传出SMTP通信。

>[!NOTE]
>
>这些步骤只能由专家用户执行。

### 跟踪 {#tracking-deliveries}

要更好地了解收件人的行为，您可以跟踪他们对投放的反应： 接收、打开、点击链接、退订等。 在Campaign Classic中，此信息显示在投放所定位的收件人的“跟踪”选项卡和投放的“跟踪”选项卡中。 在Campaign Standard中，它显示在投放的跟踪日志选项卡中。

**提示**: 默认情况下，消息跟踪处于启用状态。 要配置URL，请选择投放向导下半部分的“显示URL”选项。 对于邮件的每个URL，您可以选择是否激活跟踪。

有关此方面的详细信息，请参 [阅配置跟踪](../../delivery/using/how-to-configure-tracked-links.md) 部分和跟踪 [指示器说明](../../reporting/using/delivery-reports.md#tracking-indicators) 。

### 投放性能 {#delivery-performances}

要测量消息的传送速度，您可以控制投放吞吐量。 标准是每小时发送的消息数和消息的大小（以位／秒为单位）。 有关详细信息，请参阅 [投放吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 请勿在实例上使投放处于失败状态，因为这会维护临时表并影响性能。

* 从投放库中删除不再需要的收件人和非活动的，以保持地址质量。

* 不要试着计划大投放。 请注意，可能需要5到10分钟才能将负载均匀分布到系统上。

### 投放疑难解答 {#delivery-troubleshooting}

遇到投放问题时，可以执行特定操作：

* [可交付性问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [图像显示问题](../../production/using/image-display-issues.md)

* [投放性能问题](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [临时文件问题](../../production/using/temporary-files.md) - *仅限预置型客户*
