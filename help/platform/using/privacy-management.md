---
title: 隐私管理
description: 了解有关隐私管理的更多信息
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: 9240b6e194dbc26fbf37a9ecf88a1ae03f9e7a75
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 1%

---


# 隐私管理 {#privacy-management}

Adobe Campaign优惠一组工具，帮助您遵守隐私权规定（包括GDPR、CCPA、PDPA、LGPD）。

* 本节提供有关隐私管理的一般信息以及Adobe Campaign为管理访问权 [和被遗忘权而提供的功能](#right-access-forgotten)。

* 它还包含有关管理隐私(同意、保留[和角色](#consent-retention-roles))的重要功能的信息，以及在使用Adobe Campaign时帮助您遵守隐私的最佳实践。

## 隐私管理法规 {#privacy-management-regulations}

Adobe Campaign的功能可帮助您遵守以下法规：

* **GDPR** ([一般合并保护规定](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en))是欧洲(EU)隐私法，它协调欧盟国家的数据保护要求并使其现代化。
* **CCPA** (California Consumer Privacy Act[](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.标题(&amp;T)=1.81.5。&amp;part=4。&amp;chapter=&amp;article=))为加利福尼亚州居民提供与其个人信息相关的新权利，并对在加利福尼亚开展业务的特定实体强加数据保护责任。
* **PDPA** (个[人数据保护法](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/))是新的隐私法，旨在协调泰国的数据保护要求并使之现代化。
* **LGPD** ([Lei Geral de Proteção de Dados](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf))将于2021年初对巴西收集或处理个人数据的所有公司生效。

所有这些法规均适用于为居住在上述地区或国家（欧盟、加利福尼亚、泰国、巴西）的数据主体持有数据的Adobe Campaign客户。

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>有关个人数据以及管理数据的不同实体（数据控制者、数据处理者和数据主体）的详细信息，请参 [阅个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)。

## 访问权与被遗忘权 {#right-access-forgotten}

为了帮助您提高隐私准备程度，Adobe Campaign允许您处理访 **问** 和删 **除请求** 。

* 访问 **权是** ，数据主体有权从数据管理者那里获得关于是否正在处理与其有关的个人数据的确认，其目的和地点。 数据管理人应当以电子格式免费提供个人数据副本。

* 被遗忘权( **删除请求** )也称为数据擦除，使数据主体能够让数据控制者擦除其个人数据，停止进一步散发数据，并可能让第三方停止处理数据。

要了解如何创建 **Access** 和 **Delete请求以** 及Adobe Campaign如 [何处理请求，请参](../../platform/using/privacy-requests.md)阅实施步骤。

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## 同意、保留和角色 {#consent-retention-roles}

除了最新的访问 **权和被遗忘权****** 功能外，Adobe Campaign还优惠了对隐私至关重要的其他重要功能：

* [同意管理](#consent-management):订阅首选项管理功能
* [数据保留](#data-retention):所有标准日志表上的数据保留期，可以使用工作流设置其他保留期
* [权限管理](#rights-management):指定权限管理的数据访问

### 同意管理 {#consent-management}

同意表示数据主体同意处理与数据主体相关的个人数据。 数据主管负责为该处理获得必要的同意。 虽然Adobe Campaign可能提供一些功能来帮助客户管理与服务相关的同意，但Adobe不负责同意。 客户应与自己的法律部门合作，确定自己的流程和做法，以便获得必要的同意。

从一开始，帮助管理同意的某些方面的功能就是Adobe Campaign的核心。 通过订阅管理流程，客户可以跟踪哪些收件人已选择使用哪类订阅，无论是新闻稿、每日或每周促销，还是任何其他类型的营销项目。

![](assets/privacy-consent-management.png)

有关同意管理的详细信息，请参阅详 [细文档](../../delivery/using/managing-subscriptions.md)。

除了Adobe Campaign提供的同意管理工具之外，您还可以跟踪消费者是否已选择出售个人信息。 请参阅[此章节](../../platform/using/privacy-requests.md##sale-of-personal-information-ccpa) 。

### 数据保留 {#data-retention}

关于保留，活动中内置的日志表具有预先设置的保留期，通常将其存储限制为六个月或更短。

以下是内置表的默认保留值。 请注意，保留配置由Adobe技术管理员在实施过程中设置，每项实施的值可能因客户要求而异。

* **统一跟踪**:1年
* **投放日志**:6个月
* **跟踪日志**:1年
* **已删除投放**:1周
* **导入拒绝**:6个月
* **访客用户档案**:1个月
* **优惠建议**:1年
* **事件**:1个月
* **事件处理统计**:1年
* **存档事件**:1年
* **忽略管道事件**:1个月

与删除类似，使用标准工作流功能，可以为任何自定义表设置保留期。

联系Adobe顾问或技术管理员，进一步了解客户保留情况或您是否需要为自定义表设置保留情况。

### 权限管理 {#rights-management}

Adobe Campaign允许您通过不同的预建或自定义角色管理分配给各种活动操作符的权限。

一个好处是，这允许您管理公司内谁可以访问不同类型的数据。 例如，您可能有不同的营销人员覆盖不同的地域，每个营销人员只能访问其地域的数据。

同样，此功能还允许您为每个用户配置不同的功能，例如限制哪些用户可以发送投放，或限制哪些用户可以修改或导出数据与隐私管理更相关。

![](assets/privacy-user-management.png)

有关访问管理的详细信息，请参阅详 [细文档](../../platform/using/access-management.md)。