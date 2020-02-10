---
title: 关于种子地址
seo-title: 关于种子地址
description: 关于种子地址
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# 关于种子地址{#about-seed-addresses}

种子地址用于定位不符合既定目标标准的收件人。这样，超出传送范围的接收者可以像任何其他目标接收者一样接收传送。

使用它们的主要原因之一是您的邮 **寄列表保护**。 将种子地址插入到邮寄列表中可让您注意到第三方是否正在使用它，因为它包含的种子地址将收到发送到您的邮寄列表的递送。

此外，种子地址还允许您在 **发送之前通过发送证明来预览和测试交付的个性化和呈现** (请参阅使用种 [子地址作为证明](../../delivery/using/steps-validating-the-delivery.md#using-seed-addresses-as-proof))。

种子地址功能具有以下优点：

* 使用从收件人配置文件获取的数据随机替换字段：这样，您只能输入电子邮件地址（例如，在种子地址部分），并让Campaign自动填写配置文件中的其他字段(请参阅使 [用案例：配置字段替换](../../delivery/using/use-case--configuring-the-field-substitution.md))。
* 使用具有数据管理功能的工作流时，可以在种子地址级别输入交付中处理的附加数据以强制使用以下值：这会绕过随机值替换。
* 种子地址会自动排除在有关以下交付统计信息的报告之外： **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**。

通过导入或直接在分发或营销活动中创建种子地址，将种子地址添加到分发目标。

>[!NOTE]
>
>种子地址不属于收件人表，它们是在单独的表中创建的。 如果用新数据扩展收件人表，则必须同时扩展种子地址表和同一数据。 否则，种子地址将不会考虑扩展字段。
>
>本节介绍如何扩展种子地址表的示例：用 [例：在条件上选择种子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

对于直接邮件发送，种子地址在提取期间添加并混合在输出文档中。

>[!CAUTION]
>
>对于直邮发送，提取文件格式必须符合以下限制：
>
>* 它不得使用此选项 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**。
>* 如果提取了元素集合，则这些字段的种子地址值将为空，除非选 **[!UICONTROL Single row (expert user)]** 择了此选项。 如需详细信息，请参阅[此部分](../../platform/using/exporting-data.md#step-7---data-formatting)。
>


