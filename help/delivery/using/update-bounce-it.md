---
product: campaign
title: 在Italia Online中断后更新退件资格
description: 了解如何在Italia Online服务中断后更新退回资格
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 3cf6ffb2b69d44b56615492dd9db8965ae3cf4e1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 在意大利在线服务中断后更新错误的硬退回 {#update-bounce-italia}

![](../../assets/common.svg)

## 上下文{#outage-context}

自1月22日（当地时间）以来，Italia Online发生了中断，导致多次延迟和拒绝电子邮件。 服务于1月26日开始恢复，容量有限。

受影响的域包括： **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**&#x200B;和 **blu.it**.

此问题发生在1/22/2023到1/26/2023之间，但大多数错误的隔离发生在1月26日。

在官方通信中了解详情 [此处](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}。


## 影响{#outage-impact}

如果ISP发生中断，则无法成功将通过Campaign发送的电子邮件发送给其收件人：这些电子邮件将被错误地标记为退回。 这不仅影响Adobe，还影响到所有试图向Italia Online发送电子邮件的人。

症状包括：

* **延期退回** 消息 `452 requested action aborted: try again later` 正在观察 — 这些操作将自动重试，无需执行任何操作。 当ISP恢复完整容量时，应该会有所改进。

* **硬退回** 消息 `550 <email address> recipient rejected` ISP已于当地时间1月26日早8点至晚2点返回，以防止发送方继续使其服务器过载。 正如意大利在线邮递员所确认的，这些地址并非真正的硬退回，因此我们建议取消对因该邮件而于2023年1月26日被排除的所有电子邮件地址的隔离。

## 更新流程{#outage-update}

根据标准退回处理逻辑，Adobe Campaign会通过 **[!UICONTROL Status]** 设置 **[!UICONTROL Quarantine]**. 要更正此问题，您需要通过查找和删除这些收件人，或更改其 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 以便夜间清理工作流将删除它们。

要查找受此问题影响的收件人，或者如果在其他ISP中再次出现此问题，请参阅相关说明 [本页](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
