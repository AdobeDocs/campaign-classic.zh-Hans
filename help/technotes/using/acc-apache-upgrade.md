---
product: campaign
title: 技术说明 — Adobe Campaign - Apache版本安全更新
description: Adobe Campaign - Apache版本安全更新
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: a3eae4e253f66f5a651ffe0458f60b1f8bdf2258
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Campaign - Apache版本安全更新 {#apache-update}

>[!CAUTION]
>本文适用于： **Campaign Classicv7 Managed Services** 客户， **Campaign v8** 客户和 **Campaign Standard** 客户。

Adobe Campaign可与第三方工具配合使用，并且会定期更新兼容性，以仅实施受支持的版本，并从最新的修复和改进中受益。

Adobe Campaign包含Apache Tomcat，它通过HTTP作为应用程序服务器中的入口点，并与Apache Web服务器集成。 Apache Software Foundation已发布Apache HTTP Server 2.4.53。此版本解决了可能允许远程攻击者控制受影响系统的漏洞。 在 [Apache 2.4.53公告](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}。

Adobe Campaign团队将通过 **2022年6月15日** 以缓解此Apache漏洞并使实例环境更安全。 此升级适用于在易受攻击的Apache HTTP Server版本上运行的所有Campaign Classicv7 Managed Services客户、Campaign v8和Campaign Standard客户。 如果您受到影响，Adobe已与您联系，以告知您此升级。

此升级预计会在正常工作时间以外自动运行，以便您继续使用Campaign服务而不会造成任何中断。

非生产实例将首先通过Adobe进行升级，然后升级生产实例。 由于这是Adobe拥有的自动升级过程，因此不需要您的一方执行任何操作。 但是，如果您遇到任何问题，请联系 [Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>此升级需要重新启动Apache Web服务器。 在下面所述的时段内，停机时间不会超过10分钟。

## 常见问题解答 {#apache-faq}

* **为什么这是强制升级？**

   当前的Apache版本易受攻击，并且存在潜在的安全威胁。 必须将您的Campaign实例升级到最新适用的Apache版本，以解决安全风险。

* **哪些客户是安全升级的目标？**

   所有使用在旧版Apache上实施的Campaign环境的客户都将升级到适用的最新Apache版本。

* **预计停机时间是多少？**

   预计停机时间不到10分钟。

* **客户是否需要执行任何操作才能进行此安全升级？**

   由于安全升级将自动运行，因此无需执行任何操作。

* **维护时段内运行的营销活动/工作流有何影响？**

   在维护窗口期间，工作流和邮件服务将同时停止，并且计划活动将不会运行。 在停机期间，任何正在进行的活动或正在运行的进程都将停止，直到服务器重新启动为止。 活动完成并重新启动服务器后，所有服务都将恢复。

* **客户需要运行哪些验证？**

   此安全升级不需要任何特定测试。 如果发现任何问题，请联系 [Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **我是否可以请求更改计划安全升级插槽的日期/时间？**

   由于这是一项安全修复，我们强烈建议您调整以适应现有计划。


对于任何其他问题，您可以联系 [Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support).
