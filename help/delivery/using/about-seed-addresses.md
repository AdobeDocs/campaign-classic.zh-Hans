---
product: campaign
title: 关于种子地址
description: 种子地址入门
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 9%

---

# 关于种子地址{#about-seed-addresses}

种子地址用于定位不符合既定目标标准的收件人。这样，超出投放范围的收件人可以像任何其他目标收件人一样接收投放。

使用它们的主要原因之一是 **您的邮件列表保护**. 如果在邮寄列表中插入种子地址，并且第三方正在使用它，您会注意到这一点，因为种子地址包含的种子地址将收到发送到邮寄列表的投放。

此外，种子地址允许您 **预览和测试投放个性化和呈现** 发送之前，通过向用户发送验证(请参阅 [使用种子地址作为证明](steps-defining-the-target-population.md#using-seed-addresses-as-proof))。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](steps-defining-the-target-population.md#seeds-and-proofs-video)

种子地址功能具有以下优点：

* 使用收件人用户档案中的数据随机替换字段：例如，您可以在种子地址部分仅输入电子邮件地址，并让Campaign自动填写用户档案的其他字段(请参阅 [用例：配置字段替换](use-case--configuring-the-field-substitution.md))。
* 使用具有数据管理功能的工作流时，可在种子地址级别输入投放中已处理的其他数据，以强制使用该值：这可以作为随机值替代的另一做法。
* 系统会自动从以下投放统计信息的报表中排除种子地址： **[!UICONTROL Clicks]**， **[!UICONTROL Opens]**， **[!UICONTROL Unsubscriptions]**.

种子地址可通过导入或直接在投放或营销活动中创建来添加到投放目标。

>[!NOTE]
>
>种子地址不属于收件人表，会在单独的表中创建。 如果使用新数据扩展收件人表，则还必须使用相同数据扩展种子地址表。 否则，种子地址将不考虑这些扩展字段。
>
>本节中介绍了如何扩展种子地址表的示例： [用例：根据条件选择种子地址](use-case--selecting-seed-addresses-on-criteria.md).

对于直邮投放，种子地址会在提取期间添加，并在输出文档中混合。

>[!IMPORTANT]
>
>对于直邮投放，提取文件格式必须符合以下限制：
>
>* 它不得使用选项 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* 如果提取了元素集合，则这些字段的种子地址将具有空值，除非 **[!UICONTROL Single row (expert user)]** 已选中选项。 如需详细信息，请参阅[此部分](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。
>
