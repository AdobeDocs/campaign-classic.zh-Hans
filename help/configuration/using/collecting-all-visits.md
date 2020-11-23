---
solution: Campaign Classic
product: campaign
title: 收集所有访问
description: 收集所有访问
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---


# 收集所有访问{#collecting-all-visits}

由Adobe Campaign提供的Web跟踪模块允许您在消息中单击后在站点跟踪上下文中收集收件人对站点的特定页面的访问。

但是，您可以配置您的平台，以便它通过Web跟踪标签收集平台所知用户对页面的所有访问。

该平台所知的用户是已被收件人瞄准并且已点击至少一次所接收消息的投放。 永久cookie用于标识此收件人。

>[!IMPORTANT]
>
>Adobe Campaign平台不适用于在消息中点击后访问网站的上下文之外用作网站跟踪工具。 启用此选项后，可能会在承载服务器的计算机（重定向、应用程序和数据库）上引起资源的高使用率。 建议您确保硬件架构能够支持此负载，并避免将Web跟踪标签放置到最频繁访问的页面(如主页)中。

## 服务器配置 {#server-configuration}

通过重载serverConf.xml文件的某 **些元素来配置服** 务器。 这些文件保存在 **Adobe Campaign** 安装目录的conf子目录中。

### 重定向服务器 {#redirection-server}

对于重定向服务器，将重 **定向元素** trackWebVisitors **属性设** 置为 **true**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 配置默认匹配活动 {#configuring-a-default-matching-campaign}

要通过客户端控制台视图跟踪信息，您必须：

* 创建 **伪投放** (投放映射必须与目标模式的映射相同),
* 在NmsTracking_ **WebTrackingDelivery** 选项中输入此 **投放的内** 部名称。

并非直接在电子邮件中单击之后查看的所有站点跟踪信息都可以在创建的虚拟投放中查看。
