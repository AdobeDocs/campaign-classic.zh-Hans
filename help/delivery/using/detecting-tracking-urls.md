---
product: campaign
title: 检测跟踪URL
description: 详细了解推荐的跟踪URL模式
feature: Monitoring
role: User, Developer, Data Engineer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 2%

---

# 检测跟踪 URL

## 非检测示例

`<%= getURL("http://mynewsletter.com") %>` 会工作，并通过电子邮件将网页的实际内容发送给收件人。 但这些链接都未被跟踪。 原因是MTA执行 `"<%=getURL(..."` 每封电子邮件发送前的ID。 由于每个收件人的名称可能不同，因此Adobe Campaign无法知道用于跟踪的URL并为他们分配标记ID。

当所有收件人的下载页面都相同时，最佳实践是执行以下操作：

`<%@ include url="http://mynewsletter.com" %>`

在这种情况下，页面将在分析期间以及跟踪检测之前下载。 它允许Adobe Campaign发现链接、分配标记ID并跟踪它们。

## 推荐的模式

处理之后 `<%@` 说明，要跟踪的URL具有以下语法： `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Adobe不支持所有其他模式，应避免使用它们，以防止潜在的安全漏洞。

## 不安全的模式

向内容添加个性化链接时，请始终避免在URL的主机名部分进行任何个性化设置，以避免潜在的安全缺口。 请参阅[此页面](../../installation/using/privacy.md#url-personalization)以了解详情。

例如， `<a href="http://<%=myURL%>">` 语法为 **不安全** 必须避免。

* 如果Adobe Campaign生成的链接包含一个或多个参数，则使用此语法可能会导致安全问题。
* Tidy可能会错误地修补某些链接，这可能会随机发生。 典型症状是一段HTML，可在电子邮件验证中看到，但在预览中不可见。
* URL的转义存在问题，URL中的某些字符可能会导致问题。
* 名为ID的参数不能与重定向URL中的参数冲突。
* 然后，跟踪兴趣仅限于投放统计信息，因为Adobe Campaign会以不一样的方式跟踪“myURL”的所有可能值。
