---
product: campaign
title: 安全和隐私检查清单
description: 了解有关安全和隐私方面需要检查的关键元素的更多信息
feature: Installation, Privacy, Access Management, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 7%

---

# 安全和隐私检查清单{#get-started-security-privacy}



本节将向您介绍有关安全和隐私需要检查的关键元素。 某些配置只能由内部部署客户执行。

## 隐私

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

隐私配置和强化是安全优化的关键元素。 以下是有关隐私的一些可遵循的最佳实践：

* 使用HTTPS而不是HTTPProtect您的客户PII
* 使用PII视图限制保护隐私并防止数据被滥用。
* 确保加密密码受到限制。
* Protect可能包含个人信息的页面，如镜像页面、Web应用程序等。

[了解更多信息](../../installation/using/privacy.md)

## 访问管理

<img src="assets/do-not-localize/icon_access.svg" width="60px">

访问管理是安全加固的重要组成部分。 以下是一些主要的最佳实践：

* 创建足够的安全组
* 检查每个操作员是否具有适当的访问权限
* 避免使用管理员操作员，并避免在管理员组中拥有过多操作员

[了解更多信息](../../installation/using/access-management.md)

## 脚本和编码准则

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

在Adobe Campaign（工作流、Javascript、JSSP等）中进行开发时，请始终遵循以下准则：

* **脚本**&#x200B;列入允许列表 ：尝试避免SQL语句，使用参数化函数而不是字符串连接，通过将要使用的SQL函数添加到语句来避免SQL注入。

* **保护数据模型**：使用已命名权限限制操作员操作，添加系统过滤器(sysFilter)

* **在Web应用程序中添加captcha**：了解如何在公共登陆页面和订阅页面中添加captcha。

[了解更多信息](../../installation/using/scripting-coding-guidelines.md)

## 网络、数据库和 SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

在部署内部部署类型的架构时，要检查的一件非常重要的事情是网络配置。

您还必须遵循数据库引擎的安全性。

[了解更多信息](../../installation/using/network-database.md)

>[!CAUTION]
>
>从2021年7月14日开始，任何不支持TLS 1.2协议的客户端系统将无法访问所有Adobe产品和服务。 在此日期之前，请确保所有用户和客户端系统都符合TLS 1.2。 [了解详情](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## 服务器配置

<img src="assets/do-not-localize/icon_server.svg" width="60px">

必须在所有服务器上执行配置。 配置文件的类型为 **serverConf.xml** 和 **`config-<instance>.xml`**. 以下是需要验证的关键元素：

* **安全区域**：配置安全区域，以便它们直接考虑代理的客户端的IP地址。

* **文件上传保护**：限制可使用新的uploadAllowList属性上载到Adobe Campaign服务器的文件类型。 这可以在服务器配置文件中使用。

* **中继**：通过停用未使用的模块/应用程序的中继规则来优化中继配置。

* **外连接保护** 和 **命令限制** （服务器端）

* 您还可以添加额外的HTTP标头、激活checkIPConsistent、enableTLS、sessionTimeOutSec等。 请参阅 [Campaign服务器配置文档](../../installation/using/configuring-campaign-server.md) 和 [服务器配置文件说明](../../installation/using/the-server-configuration-file.md) 以了解更多信息。

[了解更多信息](../../installation/using/server-configuration.md)

## Web服务器配置

<img src="assets/do-not-localize/icon_web.svg" width="60px">

配置Web服务器(Apache/IIS)时应遵循几个最佳实践：

* 禁用旧的SSL版本和密码
* 删除TRACE方法
* 删除横幅
* 限制查询大小以防止上载重要文件

[了解更多信息](../../installation/using/web-server-configuration.md)
