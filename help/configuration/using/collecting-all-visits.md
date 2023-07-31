---
product: campaign
title: 收集所有访问
description: 收集所有访问
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 3%

---

# 收集所有访问{#collecting-all-visits}

通过Adobe Campaign提供的Web跟踪模块，您可以收集收件人单击消息后，在网站跟踪的上下文中对网站某些页面执行的访问次数。

但是，您可以配置平台，使其收集该平台已知的用户对带有Web跟踪标记的页面的所有访问。

平台已知的用户是已被投放定位并已至少单击一次已接收消息的收件人。 永久Cookie用于标识此收件人。

>[!IMPORTANT]
>
>Adobe Campaign平台仅用作在单击消息后访问网站的上下文之外的网站跟踪工具。 启用此选项后，可能会导致托管服务器的计算机上资源的使用率非常高（重定向、应用程序和数据库）。 建议您确保硬件架构可以支持此加载，并避免将Web跟踪标记放在访问频率最高的页面（如主页）中。

## 服务器配置 {#server-configuration}

通过重载 **serverConf.xml** 文件。 这些文件保存在 **会议** Adobe Campaign安装目录的子目录。

### 重定向服务器 {#redirection-server}

对于重定向服务器，设置 **trackWebVisitors** 的属性 **重定向** 元素至 **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 配置默认匹配营销活动 {#configuring-a-default-matching-campaign}

要通过客户端控制台查看跟踪信息，您必须：

* 创建 **虚拟投放** （投放映射必须与目标架构的映射相同），
* 输入 **内部名称** 此投放的 **NmsTracking_WebTrackingDelivery** 选项。

可以在创建的虚拟投放中查看并非直接在电子邮件点击之后的所有网站跟踪信息。
