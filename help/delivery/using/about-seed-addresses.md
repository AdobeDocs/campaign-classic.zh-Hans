---
product: campaign
title: 关于种子地址
description: 种子地址入门
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 8%

---

# 关于种子地址{#about-seed-addresses}



种子地址用于定位不符合既定目标标准的收件人。这样，超出投放范围的收件人就可以像任何其他目标收件人一样接收投放。

使用它们的主要原因是 **邮件列表保护**. 将种子地址插入邮件列表中会引起第三方的注意，因为其包含的种子地址将接收发送到邮件列表的投放内容。

此外，种子地址允许您 **预览和测试投放的个性化和渲染** 在发送之前，通过发送校样(请参阅 [使用种子地址作为证明](steps-defining-the-target-population.md#using-seed-addresses-as-proof))。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](steps-defining-the-target-population.md#seeds-and-proofs-video)

种子地址功能具有以下优势：

* 使用从收件人用户档案获取的数据随机替换字段：这允许您仅输入电子邮件地址（例如在种子地址部分），并让Campaign自动填写用户档案的其他字段(请参阅 [用例：配置字段替换](use-case--configuring-the-field-substitution.md))。
* 使用具有数据管理功能的工作流时，可以在种子地址级别输入投放中处理的附加数据以强制使用以下值：这会绕过随机值替换。
* 种子地址会自动从有关以下投放统计信息的报告中排除： **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

种子地址通过导入或直接在投放或营销活动中创建来添加到投放目标。

>[!NOTE]
>
>种子地址不属于收件人表，它们将在单独的表中创建。 如果使用新数据扩展收件人表，则还必须使用相同的数据扩展种子地址表。 否则，种子地址将不考虑这些扩展字段。
>
>本节介绍了如何扩展种子地址表的示例： [用例：根据条件选择种子地址](use-case--selecting-seed-addresses-on-criteria.md).

对于直邮投放，种子地址会在提取期间添加，并混合在输出文档中。

>[!IMPORTANT]
>
>对于直邮投放，提取文件格式必须符合以下限制：
>
>* 它不得使用选项 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* 如果提取了元素集合，则这些字段的种子地址值将为空，除非 **[!UICONTROL Single row (expert user)]** 选项。 如需详细信息，请参阅[此部分](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。
>

