---
product: campaign
title: 技术说明 — Adobe Campaign系统升级
description: Adobe Campaign系统升级
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Adobe Campaign 2023环境升级 {#ac-system-upgrade}

Campaign基础架构依赖于第三方系统，这些系统必须定期使用最新版本和修复进行更新。 必须执行这些更新，以确保服务的连续性，并确保Campaign环境免受安全风险的影响。 此外，需要升级Campaign，以确保与第三方系统更改兼容。

作为 **托管或托管Cloud Service客户**，Adobe会通知您何时需要这些升级。 您将需要根据建议升级环境以确保法规遵从性。

作为 **内部部署或混合型客户**，Adobe强烈建议您根据同一日程表升级系统版本和Campaign版本。

出于安全原因，您必须 [安装最新的Campaign内部版本](#ac-upgrade)，然后升级您的 [操作系统](#os-upgrade) 和/或您的 [关系数据库管理系统(RDBMS)](#pg-upgrade).

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). 另请参阅 [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md).
>

## Campaign内部版本升级 {#ac-upgrade}

**您是否受影响？**

如果您受 [操作系统升级](#os-upgrade) 和/或 [数据库系统升级](#pg-upgrade) 有关详细信息，您必须将Campaign环境升级到 [最新的7.3.2版本](../../rn/using/latest-release.md#release-7-3-2)，它与这些系统兼容。

**如何更新？**

* 作为托管或托管Cloud Service的客户，Adobe将联系您并升级您的Campaign版本。
* 作为混合型客户，Adobe将通知您中间源环境的计划内部版本升级日期。 您还必须将营销环境升级到同一版本。
* 作为内部部署客户，您需要将Campaign环境升级到最新的7.3.2内部版本。


## 操作系统升级 {#os-upgrade}

**您是否受影响？**

如果您在Debian操作系统上运行Campaign，则要受益于最新的Debian安全更新，您需要将Campaign基础设施移至 **Debian 11**. 请注意，Debian 9的安全支持将持续到2023年6月30日。

**如何更新？**

* 作为托管或托管Cloud Service的客户，Adobe将与您联系并升级您的环境。
* 作为混合型客户，Adobe将通知您中间源环境的计划升级日期。 如果您的营销环境也在Debian上运行，则还必须将其升级到Debian 11。
* 作为内部部署客户，您需要将环境升级到Debian 11。

## 数据库系统升级 {#pg-upgrade}

**您是否受影响？**

如果您的Campaign数据库系统是PostgreSQL，则为了从最新的PostgreSQL创新和安全更新中获益，您需要升级到 **PostgreSQL 14**. 请注意，PostgreSQL 11将于2023年11月9日终止生命周期。

**如何更新？**

* 作为托管或托管Cloud Service客户，Adobe将与您联系，并将您的数据库系统从PostgreSQL 11升级到PostgreSQL 14。
* 作为混合型客户，如果您的营销数据库系统是PostgreSQL，则必须将其升级到PostgreSQL 14。
* 作为内部部署客户，您需要将数据库系统升级到PostgreSQL 14。


## 有用的链接

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [下载最新的Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
* [使用户可以使用新的客户端控制台](../../installation/using/client-console-availability-for-windows.md)
