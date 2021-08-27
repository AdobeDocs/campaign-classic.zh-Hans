---
product: campaign
title: 收集所有访问
description: 收集所有访问
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 收集所有访问{#collecting-all-visits}

![](../../assets/v7-only.svg)

通过Adobe Campaign提供的Web跟踪模块，您可以收集收件人在消息中单击后进行网站跟踪的上下文中对网站特定页面的访问。

但是，您可以配置您的平台，以便该平台收集具有Web跟踪标记的页面所有访问次数，该标记由平台已知用户执行。

平台已知的用户是已被投放定向且已至少单击一次接收消息的收件人。 永久Cookie用于标识此收件人。

>[!IMPORTANT]
>
>Adobe Campaign平台不适用于消息中单击后访问网站的上下文之外的网站跟踪工具。 启用此选项后，可能会导致在托管服务器的计算机上（重定向、应用程序和数据库）大量使用资源。 建议您确保硬件架构能够支持此负载，并避免在最常访问的页面（如主页）中放置Web跟踪标记。

## 服务器配置 {#server-configuration}

通过过载&#x200B;**serverConf.xml**&#x200B;文件的某些元素来配置服务器。 这些文件保存在Adobe Campaign安装目录的&#x200B;**conf**&#x200B;子目录中。

### 重定向服务器 {#redirection-server}

对于重定向服务器，将&#x200B;**redirection**&#x200B;元素的&#x200B;**trackWebVisitors**&#x200B;属性设置为&#x200B;**true**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 配置默认匹配的营销活动 {#configuring-a-default-matching-campaign}

要通过客户端控制台查看跟踪信息，您必须：

* 创建&#x200B;**虚拟投放**（投放映射必须与目标架构的映射相同），
* 在&#x200B;**NmsTracking_WebTrackingDelivery**&#x200B;选项中输入此投放的&#x200B;**内部名称**。

在创建的虚拟投放中，可以查看并非直接在电子邮件中单击之后显示的所有网站跟踪信息。
