---
solution: Campaign Classic
product: campaign
title: 检测跟踪 URL
description: 了解有关跟踪URL的建议模式的更多信息
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 检测跟踪 URL

## 非检测示例

`<%= getURL("http://mynewsletter.com") %>` 工作，并通过电子邮件将网页的实际内容发送给收件人。但是，这些链接都不会被跟踪。 其原因是MTA在发送前对每封电子邮件执行`"<%=getURL(..."`。 它可以针对每个收件人而有所不同，因此Adobe Campaign无法知道用于跟踪的URL并为其分配一个标记ID。

当所有收件人的要下载页面相同时，最佳做法是执行以下操作：

`<%@ include url="http://mynewsletter.com" %>`

在这种情况下，页面会在分析下载，然后再进行跟踪检测。 它允许Adobe Campaign发现链接、分配标记ID并跟踪它们。

## 推荐模式

处理`<%@`指令后，要跟踪的URL的语法如下：`<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>所有其他模式都不受Adobe支持，应避免出现潜在的安全漏洞。

## 无担保模式

在向内容添加个性化链接时，请始终避免在URL的主机名部分包含任何个性化，以避免潜在的安全漏洞。 请阅读[本页](../../installation/using/privacy.md#url-personalization)了解更多信息。

例如，`<a href="http://<%=myURL%>">`语法为&#x200B;**不安全**，必须避免。

* 如果Adobe Campaign生成的链接包含一个或多个参数，则使用此语法可能导致安全问题。
* “整洁”可能会错误地修补某些链接，而这些链接可能会随机发生。 典型症状是HTML，在电子邮件验证中可见，但在预览中则不可见。
* 转义URL时出现问题，URL中的某些字符可能会导致问题。
* 不能有名为ID的参数与重定向URL中的参数冲突。
* 然后，跟踪的兴趣仅限于有关投放的统计信息，因为Adobe Campaign以不同方式跟踪“myURL”的所有可能值。
