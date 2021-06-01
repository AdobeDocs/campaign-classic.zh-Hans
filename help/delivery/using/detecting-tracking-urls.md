---
product: campaign
title: 检测跟踪 URL
description: 进一步了解跟踪URL的推荐模式
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 检测跟踪 URL

## 非检测示例

`<%= getURL("http://mynewsletter.com") %>` 工作，并通过电子邮件将网页的实际内容发送给收件人。但是，这些链接均未被跟踪。 原因是MTA在发送之前会对每封电子邮件执行`"<%=getURL(..."`。 由于每个收件人的URL可能各不相同，因此Adobe Campaign无法知道用于跟踪的URL并为其分配一个标记ID。

如果要下载的页面与所有收件人的页面相同，则最佳实践是执行以下操作：

`<%@ include url="http://mynewsletter.com" %>`

在这种情况下，将在分析期间在跟踪检测之前下载页面。 它允许Adobe Campaign发现链接、分配标记ID并跟踪它们。

## 推荐模式

处理`<%@`说明后，要跟踪的URL具有以下语法：`<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>所有其他模式都不受Adobe支持，应避免出现这种模式，以防出现潜在的安全漏洞。

## 不安全模式

在向内容添加个性化链接时，应始终避免在URL的主机名部分进行任何个性化，以避免潜在的安全漏洞。 请参阅[此页面](../../installation/using/privacy.md#url-personalization)以了解详情。

例如，`<a href="http://<%=myURL%>">`语法为&#x200B;**不安全**，必须避免使用。

* 如果Adobe Campaign生成的链接包含一个或多个参数，则使用此语法可能会导致安全问题。
* “整洁”可能会错误地修补某些链接，这些链接可能会随机发生。 典型症状是一段HTML，该HTML在电子邮件校样中可见，但在预览中不可见。
* 转义URL时出现问题，URL中的某些字符可能会导致问题。
* 重定向URL中的参数名为ID的参数不能与参数冲突。
* 随后，对跟踪的兴趣将限于投放的统计信息，因为Adobe Campaign会以不同的方式跟踪“myURL”的所有可能值。
