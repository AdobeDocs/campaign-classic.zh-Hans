---
solution: Campaign Classic
product: campaign
title: 中间源部署
description: 中间源部署
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# 中间源部署{#mid-sourcing-deployment}

此配置是托管(ASP)配置与内部化之间的最佳中间解决方案。 向外执行组件在托管于Adobe Campaign的“中间源”服务器上执行。

>[!NOTE]
>
>要设置此类型的部署，您需要获取相应的选项。 请检查您的许可合同。

服务器和进程之间的通用通信按以下模式进行：

![](assets/s_ncs_install_midsourcing.png)

* 实例上禁用了执行和跳出管理模块。
* 应用程序配置为在使用SOAP调用（通过HTTP或HTTPS）驱动的远程“中间源”服务器上执行消息执行。

## 功能{#features}

### 优势{#advantages}

* 简化的服务器配置：客户无需配置面向外的模块（mta和inMail）。
* 带宽使用有限：由于执行由中间源服务器执行，因此只需要足够的带宽即可向中间源服务器发送个性化数据。
* 高可用性不再是一个内部问题：问题转移到中间源服务器(重定向、镜像页面、执行服务器等)。
* 数据库不会离开公司:只有汇编消息所必需的中间源才会被发送到服务器（HTTPS可用于此）。
* 此类部署可以是大容量体系结构(数据库中的许多收件人)的解决方案，具有显着的投放吞吐量。

### 缺点{#disadvantages}

* 查看消息执行信息和报告功能时稍有延迟，因为从中间源服务器获取信息所花费的时间。
* 调查和web表单仍保留在客户端平台上。

### 建议的设备{#recommended-equipment}

* 应用程序服务器：2 Ghz四核CPU、4 GB RAM、软件RAID 1 80 GB SATA硬盘。
* 数据库服务器：3 GHz双四核CPU，最低4 GB RAM，硬件RAID 10 15000RPM SAS硬盘，数字取决于数据库的大小和预期性能。

>[!NOTE]
>
>重定向和中间源是单独的元素，但通常跟踪服务器将与中间源服务器共享。

## 安装和配置步骤{#installation-and-configuration-steps-}

### 先决条件{#prerequisites}

* 应用程序服务器上的JDK。
* 访问应用程序服务器上的数据库服务器。
* 防火墙配置为打开HTTP(80)或HTTPS(443)端口至中间源服务器。

### 安装和配置(中间源部署){#installing-and-configuring--mid-sourcing-deployment-}

请参阅[中间源服务器](../../installation/using/mid-sourcing-server.md)。
