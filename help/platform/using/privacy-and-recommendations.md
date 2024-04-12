---
product: campaign
title: 隐私和同意
description: 进一步了解隐私和同意
feature: Privacy, Privacy Tools
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: d2451b62-bddf-4dee-8789-35aaae8348e1
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 98%

---

# 隐私和同意{#privacy-and-recommendations}



## 一般建议 {#general-recommendations}

Adobe Campaign 是一款用于收集和处理超大量数据（包括个人信息和敏感数据）的强大工具。为此需要谨慎管理隐私。

* 始终以负责任和道德的方式使用个人信息。

* 避免发送未经请求的电子邮件、推送通知和短信（“垃圾邮件”）。为了实现客户终生价值并提高客户忠诚度，Adobe 坚信许可营销原则，并因此严格禁止使用 Adobe Campaign 发送未经请求的消息。

请查看[安全和隐私检查列表](../../installation/using/get-started-security-privacy.md)，了解有关安全和隐私方面需要检查的核心元素。

### 隐私法规 {#privacy-regulations}

要正确处理隐私和管理个人数据，请在适用于您运营地区的法规范围内开展工作。这些法规包括：
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)（欧洲通用数据保护条例）
* [DPA](https://www.gov.uk/data-protection)（英国的 GDPR 实施）
* [欧洲隐私和电子通信指令](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)（规定商业电子邮件规则和要求的美国法律）
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=)（加州消费者隐私法案）
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/)（泰国个人数据保护法案）
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) （巴西通用数据保护法）

>[!NOTE]
>
>有关 GDPR、CCPA 、PDPA 和 LGPD 如何应用于 Adobe Campaign 的更多信息，请参阅[此页面](../../platform/using/privacy-management.md#privacy-management-regulations)。

### Adobe Experience Cloud 隐私 {#experience-cloud-privacy}

Adobe Campaign 是 Adobe Experience Cloud 解决方案的一部分。Campaign 中处理隐私的方式遵循如下 Experience Cloud 一般原则：

* **使用 Adobe Experience Cloud 时收集哪些信息**

  作为使用 Adobe Experience Cloud 解决方案的公司，您可以选择要收集哪些信息并将其发送到您的 Adobe Experience Cloud 帐户。可能收集的信息类型示例包括 Web 浏览活动、IP 地址、移动设备的位置信息、活动成功率、购买或放入购物车的商品等。

  >[!NOTE]
  >
  >至于所有 Adobe 产品，Campaign 会收集有关应用程序和网站用户的信息。有关此内容的更多信息，请参阅 [Adobe 隐私策略](https://www.adobe.com/cn/privacy/policy.html)。

* **如何使用 Adobe Experience Cloud 收集信息**

   * Adobe Experience Cloud 解决方案使用 cookie 及网络信标（也称为标记或像素）之类的类似技术使您能够收集信息。有关 Adobe Campaign 的 cookie 和跟踪功能的更多信息，请参阅[此部分](#tracking-capabilities)。
   * 您还可以在移动应用程序中使用 Adobe Experience Cloud 技术。有关使用 Campaign 发送移动投放的详细信息，请参阅[短信渠道](../../delivery/using/sms-channel.md)和[移动应用程序渠道](../../delivery/using/about-mobile-app-channel.md)。

* **用户对您使用 Adobe Experience Cloud 的隐私选择**

  Adobe 要求您提供客户隐私政策，其中描述：

   * 关于 Adobe Experience Cloud 的隐私条例
   * 用户如何可为收集或使用与 Adobe Experience Cloud 有关的信息设置首选项

  >[!NOTE]
  >
  >至于所有 Adobe 产品，Campaign 用户可以选择不共享通过应用程序和网站收集到的关于它们的信息。有关此内容的更多信息，请参阅 [Adobe Experience Cloud 使用信息常见问题解答](https://www.adobe.com/cn/privacy/experience-cloud-usage-info-faq.html)。

有关A dobe Experience Cloud 隐私的更多详细信息，请参阅[此页面](https://www.adobe.com/cn/privacy/marketing-cloud.html)。

## 个人数据和角色 {#personal-data}

在管理隐私时，必须明确应当谨慎处理哪些数据以及由谁处理。
* **个人数据**&#x200B;是指可以直接或间接识别生命个体的信息。
* **敏感个人数据**&#x200B;是与个人的种族、政治观点、宗教信仰、犯罪背景、遗传信息、健康数据、性取向、生物识别信息以及贸易联盟会员资格相关的信息。

在将 Campaign 与可将受众一个系统转移到另一个系统的其他 Experience Cloud 解决方案（例如 [Adobe Analytics](../../platform/using/gs-aa.md)、[Audience Manager 或 People 核心服务](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md)、[Campaign Standard](../../integrations/using/synchronizing-audiences.md)）集成时，或通过 [CRM 连接器](../../platform/using/crm-connectors.md)将 Campaign 与其他解决方案集成时，需要格外注意个人数据保护。

[主要法规](#privacy-regulations)是指管理数据的不同实体，如下所示：
* **数据控制者**&#x200B;是确定收集、使用和共享个人数据的方式和目的权威。
* **数据处理者**&#x200B;是按照数据控制者的指示收集、使用或共享个人数据的任何个人或一方。
* **数据主体**&#x200B;是指对其个人数据进行收集、使用或共享，并可通过参考该个人数据来直接或间接进行识别的任何生命个体。

因此，作为收集和共享个人数据的公司，您是数据控制者，您的客户是数据主体，Adobe Campaign 在按照您的指示处理其个人数据时充当数据处理者。请注意，作为数据控制者，您责任处理与数据主体的关系，例如管理[隐私请求](#privacy-requests)。

### 用例方案 {#use-case-scenario}

为了说明不同角色如何互动，以下提供了一个高级 GDPR 客户体验用例的示例。

在本例中，某航空公司是 Adobe Campaign 客户。该公司是&#x200B;**数据控制者**，而航空公司的所有客户都是&#x200B;**数据主体**。此特定案例中的 Laura 是航空公司的一名客户。

以下是此示例中使用的不同角色：

* **Laura** 是&#x200B;**数据主体**。她是接收来自航空公司的消息的收件人。Laura 可能是飞行常客，但在某个时刻可能会决定，她不希望航空公司提供任何个性化的广告或营销消息。她将要求航空公司（根据其流程）删除她的飞行常客编号。

* **Anne** 是航空公司的&#x200B;**数据控制者**。她收到Laura的请求，检索为识别数据主体而请求的有用ID，并在Adobe Campaign中提交请求。

* **Adobe Campaign** 是&#x200B;**数据处理者**。

![](assets/privacy-gdpr-flow.png)

以下是此用例的一般流程：

1. **数据主体** (Laura) 通过电子邮件、客户关怀或网站向&#x200B;**数据控制者**&#x200B;发送 GDPR 请求。

1. **数据控制者** (Anne) 通过界面或使用 API 将 GDPR 请求推送给 Campaign。

1. 一旦&#x200B;**数据处理者** (Adobe Campaign) 收到该信息，就会对 GDPR 请求采取操作，并向&#x200B;**数据控制者** (Anne) 发送响应或确认。

1. 然后，**数据控制者** (Anne) 审查该信息，并将其发回至&#x200B;**数据主体** (Laura)。

## 数据采集 {#data-acquisition}

通过 Adobe Campaign，您可以收集数据，包括个人信息和敏感信息。因此，获得并监控收件人的同意至关重要。

* 始终让收件人同意接收通信。为此，请尽快保持遵守选择退出请求并通过双重选择加入流程来验证同意。有关此内容的更多信息，请参阅[使用双重选择加入创建订阅表单](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in)。
* 请勿导入欺诈性列表，并使用种子地址确认您的客户端文件未被用于欺诈用途。有关此内容的更多信息，请参阅[关于种子地址](../../delivery/using/about-seed-addresses.md)。
* 通过同意和权限管理，您可以跟踪收件人的偏好，以及管理组织内谁可以访问哪些数据。有关更多信息，请参阅[此章节](#consent)。
* 促进和管理收件人的隐私请求。有关更多信息，请参阅[此章节](#privacy-requests)。

## 隐私管理 {#privacy-management}

隐私管理是指可帮助您遵守隐私法规（GDPR 和 CCPA 等）的所有流程和工具。在[此页面](privacy-and-recommendations.md)上获取隐私管理概念的概述。

Adobe Campaign 为您提供专门用于隐私管理的各种功能集：
* 同意管理、数据保留和用户角色。请参阅[此章节](#consent)。
* 隐私请求（访问权和被遗忘权）。请参阅[此章节](#privacy-requests)。
* 选择退出个人信息销售（特定于 CCPA）请参阅[此章节](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa)。

[此部分](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow)中介绍 Campaign 中的主要隐私功能以及所涉及角色的示例。

### 同意、保留和角色 {#consent}

Adobe Campaign 最初提供对隐私至关重要的重要功能：

* **同意管理**：通过订阅管理流程，您可以管理收件人的偏好并跟踪哪些收件人已选择加入哪种类型的订阅。有关此内容的更多信息，请参阅[关于订阅](../../delivery/using/about-services-and-subscriptions.md)。
* **数据保留**：所有内置标准日志表都具有预设的保留期，通常将其数据存储限制为 6 个月或更短时间。可以使用工作流设置其他保留期。有关此内容更多信息，请联系 Adobe 顾问或技术管理员。
* **权限管理**：Adobe Campaign 使您能够通过不同的预建或自定义角色来管理分配给各种 Campaign 操作员的权限。这允许您管理公司内可以访问、修改或导出不同类型数据的人员。有关此内容的更多信息，请参阅[关于访问管理](../../platform/using/access-management.md)。

有关这些功能以及如何在 Adobe Campaign 中管理这些功能的更多信息，请参阅[此部分](../../platform/using/privacy-management.md#consent-retention-roles)。

### 隐私请求 {#privacy-requests}

Adobe Campaign 提供其他功能来促使您作为数据控制者为特定隐私请求做好准备：

* **访问权**&#x200B;是数据主体从数据控制者处就与其有关的个人数据是否正在进行处理、处理位置和处理原因获得确认的权限。

* **被遗忘权**（删除请求）允许数据主体通过数据控制者擦除其个人数据。

**访问**&#x200B;和&#x200B;**删除**&#x200B;请求将显示在[此部分](../../platform/using/privacy-management.md#right-access-forgotten)中。

[此部分](../../platform/using/privacy-requests.md)中详细描述了创建这些请求的实施步骤。

## 跟踪功能 {#tracking-capabilities}

### Cookie {#cookies}

凭借其跟踪功能，Adobe Campaign 可让您使用三种类型的 Cookie 跟踪投放对象的浏览情况：会话 Cookie 和两种永久 Cookie。

* **会话** Cookie：**nlid** Cookie 包含发送到联系人的电子邮件的标识符 (**broadlogId**)，以及消息模板的标识符 (**deliveryId**)。联系人单击由 Adobe Campaign 发送的电子邮件中包含的 URL 后即可添加标识符，让您能够跟踪他们在网络上的行为。关闭浏览器时，将自动擦除会话 Cookie。联系人可以将浏览器配置为拒绝 Cookie。

* 两种&#x200B;**永久** Cookie：
   * **UUID**（通用唯一标识符）Cookie 在 Adobe Experience Cloud 解决方案之间共享。它仅会被设置一次并直到生成新值时才从客户端浏览器中消失。通过使用这种 Cookie，您可以识别访问网站时与 Experience Cloud 解决方案发生交互的用户。它可以通过登陆页（将未知客户活动关联到收件人）或投放进行存放。这种 Cookie 的说明可在[此页面](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html#ec-cookies)中找到。
   * **nllastdelid** Cookie（在 Campaign Classic 20.3 中引入）是永久 Cookie，包含用户在其中单击了链接的上一次投放的 **deliveryId**。当缺失会话 Cookie 时，会使用此 Cookie 来标识将使用的跟踪表。

《通用数据保护条例》(GDPR) 等法规规定，公司在安装任何 Cookie 之前必须获得网站用户的同意。

* 您必须通过授权请求（有时出现在页面上方）告知用户，您的网站配备了 Web 跟踪工具并要求用户选中复选框来授权使用 Cookie，或者在用户登陆的第一个页面顶端添加横幅等。
* 应避免使用弹出窗口，因为浏览器通常会拦截此类窗口。

### 消息跟踪 {#message-tracking}

Adobe Campaign 允许您跟踪已发送的电子邮件和投放对象的行为：打开、点击链接、取消订阅等。有关此内容的更多信息，请参阅[关于消息跟踪](../../delivery/using/about-message-tracking.md)。

为此，请在您的消息中添加[跟踪链接](../../delivery/using/how-to-configure-tracked-links.md)以便在投放仪表板的 [Tracking](../../delivery/using/delivery-dashboard.md#tracking-logs) 选项卡中衡量您的投放产生的影响以及投放对象的行为。跟踪数据会在[跟踪指标](../../reporting/using/delivery-reports.md#tracking-indicators)报告中得到说明。

### Web 跟踪 {#web-tracking}

使用 Adobe Campaign，您还可以监控收件人浏览网站的方式：插入跟踪标签，以收集信息并衡量 Web 应用程序页面的访问量。有关此内容的更多信息，请参阅[跟踪 Web 应用程序](../../web/using/tracking-a-web-application.md)。

[此部分](../../configuration/using/about-web-tracking.md)介绍了如何配置 Web 跟踪。

为了进一步管理跟踪，Adobe Campaign 允许您显示一个选择退出横幅，来停止跟踪选择退出行为跟踪的最终用户的 Web 行为。有关此内容的更多信息，请参阅[选择退出 Web 应用程序跟踪](../../web/using/web-application-tracking-opt-out.md)。
