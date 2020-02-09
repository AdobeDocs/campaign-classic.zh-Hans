---
title: 收集所有访问
seo-title: 收集所有访问
description: 收集所有访问
seo-description: null
page-status-flag: never-activated
uuid: c2869b3d-33bb-4a22-a8e6-ac037f0665d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 7f841368-3867-4d6e-9720-c038d9bea0ce
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 收集所有访问{#collecting-all-visits}

通过Adobe Campaign提供的Web跟踪模块，您可以在消息中单击后在站点跟踪上下文中收集对收件人执行的站点特定页面的访问。

但是，您可以配置平台，以便它通过Web跟踪标记收集平台已知用户对页面的所有访问。

该平台已知的用户是已经被传送定位并且已经点击了至少一次接收消息的接收者。 永久Cookie用于标识此收件人。

>[!CAUTION]
>
>Adobe Campaign平台不适用于在消息中单击后访问网站的上下文之外用作网站跟踪工具。 启用此选项后，可能会导致在承载服务器的计算机（重定向、应用程序和数据库）上对资源的高度使用。 建议您确保硬件架构能够支持此负载，并避免在最频繁访问的页面（如主页）中放置Web跟踪标记。

## 服务器配置 {#server-configuration}

通过使serverConf.xml文件的某些元素过载 **来配置服务器** 。 这些文件保存在Adobe Campaign安 **装目录** 的conf子目录中。

### 重定向服务器 {#redirection-server}

对于重定向服务器，将重 **定向元素的trackWebVisitors** 属性 **设置为** true ****。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 配置默认匹配营销活动 {#configuring-a-default-matching-campaign}

要通过客户端控制台查看跟踪信息，您必须：

* 创建 **虚拟交付** （交付映射必须与目标架构的映射相同）,
* 在 **NmsTracking_WebTrackingDelivery选项中** ，输入此交付的 **内部名称** 。

并非在电子邮件中单击之后直接查看的所有站点跟踪信息都可以在创建的虚拟分发中查看。
