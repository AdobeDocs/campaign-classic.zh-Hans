---
solution: Campaign Classic
product: campaign
title: 关于种子地址
description: 关于种子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---


# 关于种子地址{#about-seed-addresses}

种子地址用于定位不符合既定目标标准的收件人。这样，超出投放范围的收件人可以像任何其他目标收件人一样接收投放。

使用它们的主要原因之一是&#x200B;**您的邮寄列表保护**。 将种子地址插入邮件列表后，第三方使用时会注意到您的注意力，因为其包含的种子地址将收到发送给您的邮件列表的投放。

此外，种子地址还允许您在发送投放之前通过向其发送验证(请参阅[将种子地址用作验证](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof))，对其进行&#x200B;**预览和测试个性化和渲染**。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

种子地址功能具有以下优点：

* 使用从收件人用户档案获取的数据随机替换字段：这样，您只能输入电子邮件地址（例如，在种子地址部分），并让活动自动填写用户档案中其他字段(请参阅[用例：配置字段替换](../../delivery/using/use-case--configuring-the-field-substitution.md))。
* 使用具有投放管理功能的工作流时，可以在种子地址级别输入在数据中处理的附加数据以强制值：这会绕过随机值替换。
* 种子地址会自动从有关以下投放统计信息的报告中排除：**[!UICONTROL Clicks]**、**[!UICONTROL Opens]**、**[!UICONTROL Unsubscriptions]**。

种子地址通过导入或直接在投放或活动中创建来添加到投放的目标。

>[!NOTE]
>
>种子地址不属于收件人表，它们是在单独的表中创建的。 如果用新数据扩展收件人表，则必须同时扩展种子地址表和使用相同数据。 否则，扩展字段将不会被考虑在种子地址中。
>
>本节介绍如何扩展种子地址表的示例：[用例：选择标准](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)上的种子地址

对于直邮投放,种子地址在提取期间添加并混合在输出文档中。

>[!IMPORTANT]
>
>对于直邮投放,提取文件格式必须符合以下限制：
>
>* 它不得使用选项&#x200B;**[!UICONTROL Handle groupings (GROUP BY+HAVING)]**。
>* 如果提取了元素集合，则这些字段的种子地址值将为空，除非选择了&#x200B;**[!UICONTROL Single row (expert user)]**&#x200B;选项。 如需详细信息，请参阅[此部分](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。

>


