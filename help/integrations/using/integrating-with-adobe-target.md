---
solution: Campaign Classic
product: campaign
title: 与Adobe Target集成
description: 与Adobe Target集成
audience: integrations
content-type: reference
topic-tags: adobe-target
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 4%

---


# 与Adobe Target集成{#integrating-with-adobe-target}

Adobe Experience Cloud中Adobe Campaign与Adobe Target（经典版和标准版）之间的集成允许您将Adobe Target的优惠包含在Adobe Campaign电子邮件投放中。

其工作原则如下：当收件人打开通过Adobe Campaign发送的电子邮件时，通过对Adobe Target的调用可显示内容的动态版本。 根据创建电子邮件时预先指定的规则计算此动态版本。

进一步了解Adobe Campaign和Adobe Target与[这四个提示与技巧的集成](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf)。
>[!NOTE]
>
>集成仅支持静态图像。 其余内容无法个性化。

Adobe Target可以利用多种类型的数据：

* 来自Adobe Campaign数据库的数据
* 链接到Adobe Target中访客ID的区段（如果使用的数据不受法律限制）
* Adobe Target数据：用户代理， IP地址，地理定位数据

>[!NOTE]
>
>您还可以在[Adobe Target帮助页面](https://docs.adobe.com/content/help/zh-Hans/target/using/integrate/campaign-and-target.html)中找到有关Adobe Campaign与Adobe Target之间集成的信息。
