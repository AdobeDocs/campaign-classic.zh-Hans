---
product: campaign
title: 技术说明 — Adobe Campaign - Apache版本安全更新
description: Adobe Campaign - Apache版本安全更新
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 854278e3e2013293888ea194c12ec1a75e70d981
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# Adobe Campaign - Apache版本安全更新 {#apache-update}

>[!NOTE]
>本文适用于：
> * Campaign Classicv7 Managed Services客户
> * Campaign v8客户
> * Campaign Standard客户



Adobe Campaign可与第三方工具配合使用，并且会定期更新兼容性，以仅实施受支持的版本，并从最新的修复和改进中受益。

Adobe Campaign包含Apache Tomcat，它通过HTTP作为应用程序服务器中的入口点，并与Apache Web服务器集成。 Apache Software Foundation已发布Apache HTTP Server 2.4.53。此版本解决了可能允许远程攻击者控制受影响系统的漏洞。 在 [Apache 2.4.53公告](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}。

Adobe Campaign团队将通过 **2022年5月31日** 以缓解此Apache漏洞并使实例环境更安全。 此升级适用于在易受攻击的Apache HTTP Server版本上运行的所有Campaign Classicv7 Managed Services客户、Campaign v8和Campaign Standard客户。 如果您受到影响，Adobe已与您联系，以告知您此升级。

此升级预计会在正常工作时间以外自动运行，以便您继续使用Campaign服务而不会造成任何中断。

在我们升级您的生产实例之前，我们的团队将首先升级您的非生产实例。 由于这是Adobe拥有的自动升级过程，因此不需要您的一方执行任何操作。 但是，如果您遇到任何问题，请联系 [Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support).


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

* **客户需要运行哪些验证？**

   此安全升级不需要任何特定测试。 如果发现任何问题，请联系 [Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **我是否可以请求更改计划安全升级插槽的日期/时间？**

   由于这是一项安全修复，我们强烈建议您调整以适应现有计划。


对于任何其他问题，您可以联系 [Adobe客户关怀](https://experienceleague.adobe.com/?support-solution=Campaign#support).
