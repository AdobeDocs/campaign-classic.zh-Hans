---
solution: Campaign Classic
product: campaign
title: 检测跟踪URL
description: 了解有关跟踪URL的建议模式的更多信息。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# 检测跟踪URL

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

## http://&lt;%=myURL%>模式上的警告

`<a href="http://<%=myURL%>">`语法不安全，因为：

* “整洁”可能会错误地修补某些链接，而这些链接可能会随机发生。 典型症状是HTML，在电子邮件验证中可见，但在预览中则不可见。
* 转义URL时出现问题，URL中的某些字符可能会导致问题。
* 不能有名为ID的参数与重定向URL中的参数冲突。
* 然后，跟踪的兴趣仅限于有关投放的统计信息，因为Adobe Campaign以不同方式跟踪“myURL”的所有可能值。

请参阅[本页](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy)以了解更多信息。

