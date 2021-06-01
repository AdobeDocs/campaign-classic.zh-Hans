---
product: campaign
title: 与Adobe Target集成
description: 与Adobe Target集成
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 4%

---

# 与Adobe Target集成{#integrating-with-adobe-target}

Adobe Campaign与Adobe Experience Cloud中的Adobe Target（经典与标准）集成，允许您在Adobe Campaign电子邮件投放中包含来自Adobe Target的选件。

其工作原理为：当收件人打开通过Adobe Campaign发送的电子邮件时，通过调用Adobe Target可显示内容的动态版本。 此动态版本根据创建电子邮件时预先指定的规则计算。

进一步了解Adobe Campaign和Adobe Target与[这四个提示和技巧的集成](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf)。
>[!NOTE]
>
>集成仅支持静态图像。 其余内容无法进行个性化。

Adobe Target可以使用多种类型的数据：

* 来自Adobe Campaign数据集市的数据
* 与Adobe Target中的访客ID关联的区段（如果使用的数据不受法律限制）
* Adobe Target数据：用户代理， IP地址，地域化数据

>[!NOTE]
>
>您还可以在[Adobe Target帮助页面](https://docs.adobe.com/content/help/zh-Hans/target/using/integrate/campaign-and-target.html)上找到有关Adobe Campaign与Adobe Target之间集成的信息。
