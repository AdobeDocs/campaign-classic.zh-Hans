---
product: campaign
title: 安全和隐私检查清单
description: 了解有关安全和隐私方面需要检查的关键元素的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 6%

---

# 安全和隐私检查清单{#get-started-security-privacy}

![](../../assets/v7-only.svg)

本节将介绍有关安全和隐私方面需要检查的关键元素。 某些配置只能由内部部署客户执行。

## 隐私

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

隐私配置和强化是安全优化的关键要素。 以下是有关隐私的一些最佳实践：

* 使用HTTPS而不是HTTP来Protect客户PII
* 使用PII视图限制来保护隐私并防止数据被误用。
* 确保加密密码受限。
* Protect可能包含个人信息（如镜像页面、Web应用程序等）的页面。

[阅读更多](../../installation/using/privacy.md)

## 访问管理

<img src="assets/do-not-localize/icon_access.svg" width="60px">

访问管理是加强安全性的重要环节。 以下是一些主要的最佳实践：

* 创建足够的安全组
* 检查每个操作员是否拥有适当的访问权限
* 避免使用管理员操作员，并避免管理员组中的运算符过多

[阅读更多](../../installation/using/access-management.md)

## 脚本和编码准则

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

在Adobe Campaign中进行开发（工作流、Javascript、JSSP等）时，请始终遵循以下准则：

* **脚本**:请尝试避免使用SQL语句，使用参数化函数而不是字符串连接，通过将要使用的SQL函数添加到来避免SQL允许列表注入。

* **保护数据模型**:使用命名权限限制运算符操作，添加系统过滤器(sysFilter)

* **在Web应用程序中添加捕获**:了解如何在公共登陆页面和订阅页面中添加捕获。

[阅读更多](../../installation/using/scripting-coding-guidelines.md)

## 网络、数据库和 SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

部署内部部署类型架构时需要检查的一个非常重要的事项是网络配置。

您还必须遵循数据库引擎安全性。

[阅读更多](../../installation/using/network-database.md)

>[!CAUTION]
>
>自2021年7月14日起，任何不支持TLS 1.2协议的客户端系统都将失去对所有Adobe产品和服务的访问权限。 在此日期之前，请确保所有用户和客户端系统均符合TLS 1.2。 [了解详情](https://helpx.adobe.com/in/x-productkb/multi/eol-tls-support.html)

## 服务器配置

<img src="assets/do-not-localize/icon_server.svg" width="60px">

必须在所有服务器上执行配置。 配置文件的类型为&#x200B;**serverConf.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**。 以下是需要验证的关键元素：

* **安全区**:配置安全区，以便它们直接考虑代理客户端的IP地址。

* **文件上传保护**:使用新的uploadAllowList属性限制可上传到Adobe Campaign服务器的文件类型。这可在服务器配置文件中使用。

* **中继**:通过取消激活未使用模块/应用程序的中继规则来优化中继配置。

* **外连接** 保护 **和命令限制** （服务器端）

* 您还可以添加额外的HTTP标头、激活checkIPConsitent、enableTLS、sessionTimeOutSec等。 有关更多信息，请参阅[Campaign服务器配置文档](../../installation/using/configuring-campaign-server.md)和[服务器配置文件描述](../../installation/using/the-server-configuration-file.md)。

[阅读更多](../../installation/using/server-configuration.md)

## Web服务器配置

<img src="assets/do-not-localize/icon_web.svg" width="60px">

配置Web服务器(Apache/IIS)时，应遵循以下几项最佳实践：

* 禁用旧SSL版本和密码
* 删除TRACE方法
* 删除横幅
* 限制查询大小以阻止上载重要文件

[阅读更多](../../installation/using/web-server-configuration.md)
