---
product: campaign
title: 技术说明 — Adobe Campaign - Apache版本安全更新
description: Adobe Campaign - Apache版本安全更新
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Adobe Campaign - Apache版本安全更新 {#apache-update}

>[!CAUTION]
>本文适用于：**Campaign Classicv7 Managed Services**&#x200B;客户、**Campaign v8**&#x200B;客户和&#x200B;**Campaign Standard**&#x200B;客户。

Adobe Campaign可与第三方工具配合使用，并且会定期更新兼容性，以仅实施受支持的版本，并从最新的修复和改进中受益。

Adobe Campaign包括Apache Tomcat，它通过HTTP充当应用程序服务器中的入口点，并与Apache Web Server集成。 Apache Software Foundation已发布Apache HTTP Server 2.4.53。此版本解决了可能允许远程攻击者控制受影响系统的漏洞。 在[Apache 2.4.53公告](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}中了解详情。

Adobe Campaign团队将在2022年6月15日之前执行Apache版本安全升级活动&#x200B;****，以缓解此Apache漏洞并提高实例环境的安全。 此升级适用于在易受攻击的Apache HTTP Server版本上运行的所有Campaign Classic v7 Managed Services客户、Campaign v8和Campaign Standard客户。 如果您受到影响，Adobe已联系您，告知您有关此次升级的信息。

此升级预计在正常工作时间之外自动运行，以便您能够继续使用Campaign服务而不会造成任何中断。

您的非生产实例将首先由Adobe升级，然后您的生产实例将升级。 由于这是由Adobe拥有的自动升级过程，因此无需您执行任何操作。 但是，如果您遇到任何问题，请联系[Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support)。


>[!NOTE]
>此升级需要重新启动Apache Web Server。 停机时间不超过10分钟，具体时间如下。
> 

## 常见问题解答 {#apache-faq}

* **为什么这是强制升级？**

  当前的Apache版本易受攻击，并存在潜在的安全威胁。 请务必将Campaign实例升级到最新适用的Apache版本以解决安全风险。

* **安全升级的目标客户是哪些客户？**

  所有使用在旧版Apache上实施的Campaign环境的客户均已升级到最新适用的Apache版本。

* **预计停机时间是多少？**

  预计停机时间不到10分钟。

* **客户是否需要执行任何安全升级操作？**

  由于安全升级将自动运行，因此无需执行任何操作。

* **在维护期间对正在运行的营销活动/工作流有何影响？**

  在维护窗口中，工作流和邮件服务将同时停止，并且计划的活动不会运行。 在停机期间，任何正在进行的活动或正在运行的进程将暂停，直到服务器重新启动。 一旦活动完成并重新启动服务器，所有服务都将恢复。

* **客户需要运行哪些验证？**

  此安全升级不需要任何特定测试。 如果发现任何问题，请联系[Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support)。


* **我可以请求更改计划的安全升级槽的日期/时间吗？**

  由于这是安全修复，因此我们强烈建议您调整到现有计划。


如有任何其他问题，请联系[Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support)。
