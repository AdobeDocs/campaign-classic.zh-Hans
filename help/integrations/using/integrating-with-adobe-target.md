---
product: campaign
title: 使用Adobe Campaign和Adobe Target
description: 了解如何将Adobe Campaign与Adobe Target集成
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 使用Campaign和Target{#integrating-with-adobe-target}



将Adobe Campaign与Adobe Target结合使用可优化电子邮件内容。

要优化电子邮件内容，您可以在Adobe Target中创建重定向选件，然后使用Adobe Campaign管理电子邮件选件。 例如，您可以为男性收件人和女性收件人显示不同的选件。

该集成在电子邮件打开时发生。 客户打开电子邮件时，会对Target发起调用，并显示内容的动态版本。 内容包含所有浏览器都支持的静态图像。 Target会跟踪受众或会话级别对选件的反应，并且这些数据会在Target报表中可用。 [请参阅Adobe Target文档以了解详情](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>该集成仅支持静态图像。 内容的其余部分无法进行个性化。

Adobe Target可使用以下几种类型的数据：

* 来自Adobe Campaign数据集市的数据
* 与Adobe Target中的访客ID关联的区段（如果所用的数据不受法律限制）
* Adobe Target数据：用户代理、IP地址、地理位置数据
