---
product: campaign
title: 与Adobe Campaign和Adobe Target合作
description: 了解如何将Adobe Campaign与Adobe Target集成
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: af40fe822c69979a478604595790d4deefd6d5b0
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 使用Campaign和Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

将Adobe Campaign与Adobe Target结合使用可优化电子邮件内容。

要优化电子邮件内容，您可以在Adobe Target中创建重定向选件，然后使用Adobe Campaign管理电子邮件选件。 例如，您可以为男性和女性收件人显示不同的选件。

集成在打开电子邮件时进行。 当客户打开电子邮件时，将对Target发起调用，并显示内容的动态版本。 内容由所有浏览器支持的静态图像组成。 Target会跟踪受众或会话级别对选件的反应，并且该数据可在Target报表中使用。 [在Adobe Target文档中了解详情](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>集成仅支持静态图像。 其余内容无法进行个性化。

Adobe Target可以使用多种类型的数据：

* 来自Adobe Campaign数据集市的数据
* 与Adobe Target中的访客ID关联的区段（如果使用的数据不受法律限制）
* Adobe Target数据：用户代理， IP地址，地理位置数据
