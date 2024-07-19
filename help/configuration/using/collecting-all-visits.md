---
product: campaign
title: 收集所有访问
description: 收集所有访问
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '296'
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

通过重载&#x200B;**serverConf.xml**&#x200B;文件的某些元素来配置服务器。 这些文件保存在Adobe Campaign安装目录的&#x200B;**conf**&#x200B;子目录中。

### 重定向服务器 {#redirection-server}

对于重定向服务器，将&#x200B;**重定向**&#x200B;元素的&#x200B;**trackWebVisitors**&#x200B;属性设置为&#x200B;**true**。

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 配置默认匹配营销活动 {#configuring-a-default-matching-campaign}

要通过客户端控制台查看跟踪信息，您必须：

* 创建&#x200B;**虚拟投放**（投放映射必须与目标架构的映射相同），
* 在&#x200B;**NmsTracking_WebTrackingDelivery**&#x200B;选项中输入此投放的&#x200B;**内部名称**。

可以在创建的虚拟投放中查看并非直接在电子邮件点击之后的所有网站跟踪信息。
