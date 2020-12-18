---
solution: Campaign Classic
product: campaign
title: 事件回收
description: 事件回收
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# 事件回收{#event-recycling}

如果某个特定渠道上的消息投放失败，Adobe Campaign可以使用其他渠道重新发送该消息。 例如，如果SMS渠道上的投放失败，则使用电子邮件渠道重新发送消息。

为此，您需要配置一个工作流，该工作流将重新创建所有具有&#x200B;**事件错误**&#x200B;状态的投放，并为其分配一个不同的渠道。

>[!CAUTION]
>
>此步骤只能使用工作流执行，因此保留给专家用户。 有关详细信息，请与Adobe客户经理联系。

