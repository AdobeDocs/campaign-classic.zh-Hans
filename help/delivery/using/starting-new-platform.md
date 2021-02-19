---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic启动新平台
description: 了解有关在使用Adobe Campaign Classic启动新平台时管理交付性的更多信息。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 1%

---


# 启动新平台 {#starting-new-platform}

在设置新平台时，维护域和IP地址信誉至关重要。

* 开始发送电子邮件是一个敏感步骤，因为平台没有任何使用历史记录，而且当发送的IP从未用于此目的时，就没有声誉。

* ISP自然会怀疑从未用来发送电子邮件的IP地址，并突然开始发送大量电子邮件流量。 事实上，垃圾邮件发送者通常使用“未知”IP地址（从未过的地址）阻止列表在检测前发送尽可能多的邮件。

* 在生产阶段的开始，您不能期望在输出方面达到操作速度。 此外，您不应尝试以此速率发送消息，因为这可能会导致ISP阻止发送地址，并严重危害其余开始阶段。

下面列出了启动新平台时应遵循的主要原则：

* 如果您有此信息，**将无效地址导入隔离表**。
首次使用地址列表时，启动平台通常会发生，但该地址可能未经完全限定。 如果发送到无效地址或蜜罐地址，这会降低平台的声誉。

   * 如果列表的地址无效，在首次发送之前将其导入隔离表（可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;菜单访问）符合您的最大利益。
   * 但是，如果您仍希望重新指定无效地址，则最好在平台信誉建立后再逐位执行此操作，以便随着时间的推移“稀释”使用不良地址。

   有关详细信息，请参阅[通过隔离优化投放](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines)。
* **通过限制** mtachild数来限制吞吐量速率。有关调整此类技术设置的详细信息，请与Adobe Campaign管理员联系。
* **逐步增加发送的** 卷，以避免标记为垃圾邮件。不要从整个开始中目标整个列表库，而是每次发送时都额外添加一部分。 这样，您就可以在每一步增加音量，同时降低无效地址的总体速率。 为确保开始阶段的顺利开发，您可以使用批次。 有关详细信息，请参阅[使用多个批次发送](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。
* **定期发送**。在某种程度上，最好定期发送小照片，而不是偶尔发送大活动。
* **要密切关注投放报告**。高错误指示器可能意味着技术设置配置错误。 有关详细信息，请参阅[监视投放](../../delivery/using/about-delivery-monitoring.md)。

**相关主题**：
* [利用IP升温提高您的电子邮件声誉](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [关于垃圾邮件陷阱](https://helpx.adobe.com/campaign/kb/spam-traps.html)