---
solution: Campaign Classic
product: campaign
title: 安全性和隐私入门
description: 了解有关安全性和隐私的要检查的关键元素的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 922603492d2c98d751683d3aa481e9ab19bca70c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---


# 安全性和隐私{#get-started-security-privacy}入门

本节将向您介绍要检查的有关安全性和隐私的关键元素。 某些配置只能由预置型客户执行。

## 隐私

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

隐私配置和强化是安全优化的关键要素。 以下是有关隐私的一些最佳实践：

* Protect客户PII（使用HTTPS而不是HTTP）
* 使用PII视图限制保护隐私并防止数据被滥用。
* 确保加密密码受限。
* Protect可能包含镜像页面、Web应用程序等个人信息的页面。

[阅读更多](../../installation/using/privacy.md)

## 访问管理

<img src="assets/do-not-localize/icon_access.svg" width="60px">

访问管理是加强安全的一个重要部分。 以下是一些主要的最佳实践：

* 创建足够的安全组
* 检查每个运营商是否拥有适当的访问权限
* 避免使用管理员操作员，并避免管理员组中的操作员过多

[阅读更多](../../installation/using/access-management.md)

## 脚本和编码指南

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

在Adobe Campaign(工作流、Javascript、JSSP等)中进行开发时，始终遵循以下准则：

* **脚本**:尝试避免SQL语句，使用参数化函数而不是字符串连接，通过向允许列表添加要使用的SQL函数来避免SQL注入。

* **保护数据模型**:使用已命名权限限制操作符操作，添加系统过滤器(sysFilter)

* **在Web应用程序中添加捕捉**:了解如何在您的公共登陆页和订阅页面中添加捕捉。

[阅读更多](../../installation/using/scripting-coding-guidelines.md)

## 网络、数据库和SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

部署内部部署类型的架构时需要检查的一个非常重要的事情是网络配置。

您还必须遵循数据库引擎的安全性。

[阅读更多](../../installation/using/network-database.md)

## 服务器配置

<img src="assets/do-not-localize/icon_server.svg" width="60px">

必须在所有服务器上执行配置。 配置文件的类型为&#x200B;**serverConf.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**。 以下是需要验证的关键元素：

* **安全区域**:配置安全区域，以便它们直接考虑代理客户端的IP地址。

* **文件上传保护**:使用新的uploadAllowList属性限制可上载到Adobe Campaign服务器的文件类型。这可以在服务器配置文件中使用。

* **中继**:通过取消激活未使用的模块/应用程序的中继规则来微调中继配置。

* **传出连** 接保 **护和命** 令限制（服务器端）

* 您还可以添加额外的HTTP头、激活checkIPConsistent、enableTLS、sessionTimeOutSec等。 有关详细信息，请参阅[活动服务器配置文档](../../installation/using/configuring-campaign-server.md)和[服务器配置文件说明](../../installation/using/the-server-configuration-file.md)。

[阅读更多](../../installation/using/server-configuration.md)

## Web服务器配置

<img src="assets/do-not-localize/icon_web.svg" width="60px">

配置Web服务器(Apache/IIS)时，应遵循以下几种最佳实践：

* 禁用旧SSL版本和密码
* 删除TRACE方法
* 删除横幅
* 限制查询大小以阻止上传重要文件

[阅读更多](../../installation/using/web-server-configuration.md)
