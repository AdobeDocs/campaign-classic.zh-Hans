---
product: campaign
title: 检测跟踪 URL
description: 详细了解推荐的跟踪URL模式
feature: Monitoring
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 检测跟踪 URL

## 非检测示例

`<%= getURL("http://mynewsletter.com") %>` 会工作，并通过电子邮件将网页的实际内容发送给收件人。 但没有任何链接被跟踪。 原因是MTA执行 `"<%=getURL(..."` 每封电子邮件发送前的ID值。 每个收件人的标签可能不同，因此Adobe Campaign无法知道用于跟踪的URL并为他们分配标签ID。

当所有收件人的下载页面都相同时，最佳实践是执行以下操作：

`<%@ include url="http://mynewsletter.com" %>`

在这种情况下，页面将在分析期间、跟踪检测之前下载。 它允许Adobe Campaign发现链接、分配标记ID并跟踪它们。

## 推荐的模式

处理之后 `<%@` 说明，要跟踪的URL具有以下语法： `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>所有其他模式均不受Adobe支持，应避免使用，以防止潜在的安全漏洞。

## 不安全的模式

向内容添加个性化链接时，请始终避免在URL的主机名部分进行任何个性化设置，以避免潜在的安全漏洞。 请参阅[此页面](../../installation/using/privacy.md#url-personalization)以了解详情。

例如， `<a href="http://<%=myURL%>">` 语法为 **不安全** 必须避免。

* 如果Adobe Campaign生成的链接包含一个或多个参数，则使用此语法可能会导致安全问题。
* Tidy可能会错误地修补某些链接，这可能发生在随机情况下。 典型症状是一段HTML，可在电子邮件验证中看到，但在预览中不可见。
* URL的转义存在问题，URL中的某些字符可能会导致问题。
* 名为ID的参数不能与重定向URL中的参数冲突。
* 然后，跟踪的兴趣仅限于投放统计数据，因为Adobe Campaign会以不变的方式跟踪“myURL”的所有可能值。
