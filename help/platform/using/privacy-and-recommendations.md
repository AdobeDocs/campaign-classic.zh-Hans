---
title: 隐私和建议
seo-title: 隐私和建议
description: 隐私和建议
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: 247d73933991047603b8d61c7489d976c448dd52
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 7%

---


# Privacy and Consent{#privacy-and-recommendations}

## 一般性建议 {#general-recommendations}

Adobe Campaign是收集和处理大量数据（包括个人信息和敏感数据）的强大工具。 这就是为什么隐私需要谨慎管理的原因。

* 始终以负责任和道德的方式使用个人信息。

* 避免发送未经请求的电子邮件、推送通知和SMS消息（“垃圾邮件”）。 Adobe坚信许可营销原则能够培养客户终身价值和忠诚度，因此严格禁止在发送未经请求的消息时使用Adobe Campaign。

请查看[安全和隐私检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)，了解有关安全和隐私方面需要检查的核心元素。

### 隐私法规 {#privacy-regulations}

要正确处理隐私和管理个人数据，请在适用于您所在地区的法规范围内开展工作。 这些规定包括：
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) （欧洲一般数据保护规定）
* [DPA](https://www.gov.uk/data-protection) （英国实施GDPR）
* [欧洲隐私和电子通信指令](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) （美国法律为商业电子邮件制定规则和要求）
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.标题(&amp;T)=1.81.5。&amp;part=4。&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) （泰国个人数据保护法）
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) （巴西一般数据保护法）-将于2020年8月16日起生效

>[!NOTE]
>
>有关GDPR、CCPA、PDPA和LGPD如何应用于Adobe Campaign的更多信息，请参 [阅本页](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy-overview.html#whatisgdpr)。

### Adobe Experience Cloud privacy {#experience-cloud-privacy}

Adobe Campaign是Adobe Experience Cloud解决方案的一部分。 隐私在活动中的处理遵循Experience Cloud的一般原则，如：

* **使用Adobe Experience Cloud时会收集哪些信息**

   作为使用Adobe Experience Cloud解决方案的公司，您可以选择要收集哪些信息并将其发送到您的Adobe Experience Cloud帐户。 可能收集的信息类型示例包括Web浏览活动、IP地址、移动设备的位置信息、活动成功率、购买或放入购物车的物品等。

   >[!NOTE]
   >
   >对于所有Adobe产品，活动会收集有关应用程序和网站用户的信息。 有关此方面的详细信息，请参阅 [Adobe隐私策略](https://www.adobe.com/privacy/policy.html)。

* **如何使用Adobe Experience Cloud收集信息**

   * Adobe Experience Cloud解决方案使用cookies及类似技术，如网络信标（也称为标签或像素），使您能够收集信息。 有关使用Adobe Campaign的cookie和跟踪功能的更多信息，请参 [阅此部分](#tracking-capabilities)。
   * 您还可在移动应用程序中使用Adobe Experience Cloud技术。 有关使用活动发送移动投放的更多信 [息，请参阅SMS渠道](../../delivery/using/sms-channel.md) 和移 [动应用渠道](../../delivery/using/about-mobile-app-channel.md)。

* **您用户对您使用Adobe Experience Cloud的隐私权选择**

   Adobe要求您提供客户隐私政策，其中描述：

   * 您与Adobe Experience Cloud相关的隐私权惯例
   * 用户如何为收集或使用与Adobe Experience Cloud有关的信息设置首选项

   >[!NOTE]
   >
   >对于所有Adobe产品，活动用户可以选择不共享通过应用程序和网站收集到的关于他们的信息。 有关此的详细信息，请参阅 [Adobe Experience Cloud使用信息常见问题解答](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html)。

有关Adobe Experience Cloud隐私的更多详细信息，请 [参阅本页](https://www.adobe.com/privacy/marketing-cloud.html)。

## 个人数据和角色 {#personal-data}

在管理隐私时，必须明确应当谨慎处理哪些数据以及由谁处理哪些数据。
* **个人数据** ，是指可以直接或间接识别活人的信息。
* **敏感个人数据** 是与个人的种族、政治视图、宗教信仰、犯罪背景、遗传信息、健康数据、性偏好、生物识别信息以及贸易合并会员资格相关的信息。

主 [要法规](#privacy-regulations) ，是指管理数据的不同实体，具体如下：
* 数 **据控制** 器是决定收集、使用和共享个人数据的手段和目的的权威。
* 数 **据处理者** ，是指按照数据管理者的指示收集、使用或共享个人数据的任何个人或一方。
* 数 **据主体** ，是指收集、使用或共享个人数据，并可以直接或间接地参照该个人数据识别的任何活人。

因此，作为收集和共享个人数据的公司，您是数据管理者，您的客户是数据主体，Adobe Campaign在按照您的指示处理其个人数据时充当数据处理者。 请注意，您作为数据管理者有责任处理与数据主体的关系，例如管理隐私 [请求](#privacy-requests)。

当将活动与其他Experience Cloud解决方案集成时，您需要为个人受众保护支付额外的费用。在其他解决方案中，可以从一个系统传输到 [另一个系统](../../platform/using/adobe-analytics-data-connector.md)，如 [Adobe Analytics、Audience Manager或人员核心服务](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md)、 [](../../integrations/using/synchronizing-audiences.md)[](../../platform/using/crm-connectors.md)Campaign Standard或通过CRM连接器与其他解决方案集成。

## 数据采集 {#data-acquisition}

Adobe Campaign使您能够收集数据，包括个人和敏感信息。 因此，您必须获得并监控收件人的同意。

* 始终让收件人同意接收通信。 为此，请继续尽快遵守退出请求并通过多次选择加入流程验证同意。 有关此内容的详细信息，请 [参阅创建包含订阅选择加入的多次表单](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。
* 请勿导入欺诈性列表并使用种子地址来检查您的客户文件是否未被欺骗性地使用。 有关此内容的详细信息，请参 [阅关于种子地址](../../delivery/using/about-seed-addresses.md)。
* 通过同意和权限管理，您可以跟踪收件人的偏好，并管理组织内谁可以访问哪些数据。 有关更多信息，请参阅[此章节](#consent)。
* 方便和管理收件人的隐私请求。 有关更多信息，请参阅[此章节](#privacy-requests)。

## 隐私管理 {#privacy-management}

隐私管理是指可帮助您遵守隐私法规（GDPR、CCPA等）的所有流程和工具。 获取本页隐私管理概 [述](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy-overview.html)。

Adobe Campaign为您提供了专门用于隐私管理的各种功能：
* 同意管理、数据保留和用户角色。 请参阅[此章节](#consent)。
* 隐私请求（访问权和被遗忘权）。 请参阅[此章节](#privacy-requests)。
* 选择退出销售个人信息(CCPA-specific)。 请参阅[此章节](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html#ccpa)。

本节介绍活动中的主要隐私功能以及相关角色 [的示例](https://helpx.adobe.com/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow)。


### 同意、保留和角色 {#consent}

Adobe Campaign优惠最初包含对隐私至关重要的重要功能：

* **同意管理**:通过订阅管理流程，您可以管理收件人偏好并跟踪哪些收件人已选择了哪类订阅。 有关此内容的详细信息，请参 [阅关于订阅](../../delivery/using/about-services-and-subscriptions.md)。
* **数据保留**:所有内置的标准日志表都具有预设的保留期，通常将其数据存储限制在6个月或更短。 可以通过工作流设置额外的保留期。 要了解更多信息，请联系Adobe顾问或技术管理员。
* **权限管理**:Adobe Campaign允许您通过不同的预建或自定义角色管理分配给各种活动操作符的权限。 这允许您管理公司内可以访问、修改或导出不同类型数据的人员。 有关此方面的详细信息，请参 [阅关于访问管理](../../platform/using/access-management.md)。

有关这些功能以及如何在Adobe Campaign中管理这些功能的更多信息，请参 [阅本页](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#consent)。

### 隐私请求 {#privacy-requests}

Adobe Campaign提供了其他功能，帮助您作为数据管理者，为特定隐私请求做好准备：

* 访问 **权是** ，数据主体有权从数据管理者那里获得关于是否正在处理与其有关的个人数据的确认，其地点和原因。

* 被 **遗忘权** （删除请求）赋予数据主体让数据管理者擦除其个人数据的权利。

>[!NOTE]
>
>这套工具可帮助您遵守GDPR、CCPA、PDPA和LGPD的隐私权。 有关这些不同法规的更多信息，请 [参阅本页](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy-overview.html#whatisgdpr)。

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

访问 **和** 删除请 **求将显示在** 此页上 [](https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess)。 创建这些请求的实施步骤详见 [本节](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)。 <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## 跟踪功能 {#tracking-capabilities}

### Cookie {#cookies}

凭借其跟踪功能，Adobe Campaign使您能够使用三种类型的cookies跟踪投放收件人的浏览：会话cookie和两个永久cookie。

* A **session cookie**: the **nlid** cookie contains the identifier of the email sent to the contact (**broadlogId**) and the identifier of the message template (**deliveryId**). 联系人单击由 Adobe Campaign 发送的电子邮件中包含的 URL 后即可添加标识符，让您能够跟踪他们在网络上的行为。关闭浏览器时，将自动擦除会话 Cookie。联系人可以将浏览器配置为拒绝 Cookie。

* 永 **久Cookie**:UUID **** （通用唯一标识符）cookie在Adobe Experience Cloud解决方案之间共享。 它设置一次，直到生成新值时它从客户端浏览器中消失。 此Cookie使您能够识别访问网站时与Experience Cloud解决方案交互的用户。 它可由登陆页(将未知客户活动与收件人关联)或投放存放。 此处提供此Cookie的说 [明](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-mc.html)。

<!--The **nllastdelid** cookie (introduced in Campaign Classic 20.3) is a permanent cookie which contains the **deliveryId** of the last delivery that user clicked the link from. This cookie is used - when the session cookie is missing - to identify the tracking table that will be used.-->

《一般数据保护规定》(GDPR)等法规规定，公司在安装任何Cookie之前必须获得网站用户的同意。

* 您必须通过授权请求（例如，页面上出现的请求）通知用户您的网站已配备Web跟踪工具，该请求中带有一个复选框，用于授权使用Cookie，或在登录的首页顶部添加横幅等。
* 弹出窗口应避免出现，因为它们经常被浏览器阻止。

### 消息跟踪 {#message-tracking}

Adobe Campaign允许您跟踪已发送的电子邮件和投放收件人的行为：打开、单击链接、退订等。 有关此方面的详细信息，请参 [阅关于消息跟踪](../../delivery/using/about-message-tracking.md)。

为此，请向消 [息中](../../delivery/using/how-to-configure-tracked-links.md) 添加跟踪链接 [，以便在投放仪表板的“跟踪”选项卡中衡量投放和](../../delivery/using/monitoring-a-delivery.md#tracking-logs) 收件人行为的影响。 跟踪数据在“跟踪指示器”报 [告中进行解](../../reporting/using/delivery-reports.md#tracking-indicators) 释。

### Web 跟踪 {#web-tracking}

Adobe Campaign还允许您监视收件人浏览网站的方式：插入跟踪标签以收集信息并衡量Web应用程序页面上的访问量。 有关此方面的详细信息，请 [参阅跟踪Web应用程序](../../web/using/tracking-a-web-application.md)。

本节介绍Web跟踪的 [配置](../../configuration/using/about-web-tracking.md)。

为了进一步管理跟踪，Adobe Campaign允许您显示退出横幅，以停止跟踪退出行为跟踪的最终用户的Web行为。 有关此内容的详细信息，请 [参阅Web 应用程序跟踪退出](../../web/using/web-application-tracking-opt-out.md)。
