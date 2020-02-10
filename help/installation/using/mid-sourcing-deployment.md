---
title: 中部署
seo-title: 中部署
description: 中部署
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# 中部署{#mid-sourcing-deployment}

此配置是在托管(ASP)配置和内部化之间的最佳中间解决方案。 面向外的执行组件在Adobe Campaign托管的“中间采购”服务器上执行。

>[!NOTE]
>
>要设置此类部署，您需要获取相应的选项。 请检查您的许可合同。

服务器和进程之间的一般通信根据以下模式进行：

![](assets/s_ncs_install_midsourcing.png)

* 实例上禁用了执行和弹回管理模块。
* 应用程序配置为在使用SOAP调用（通过HTTP或HTTPS）驱动的远程“中间源”服务器上执行消息执行。

## 功能 {#features}

### 优势 {#advantages}

* 简化的服务器配置：客户无需配置面向外的模块（mta和inMail）。
* 带宽使用有限：由于执行由中间采购服务器执行，因此只需要足够的带宽将个性化数据发送到中间采购服务器。
* 高可用性不再是一个内部问题：问题转移到中间源服务器（重定向、镜像页面、执行服务器等）。
* 数据库不会离开公司：只有汇编消息所必需的数据才会发送到中间采购服务器（HTTPS可用于此）。
* 此类部署可以是大容量架构（数据库中的许多接收方）的解决方案，具有显着的交付吞吐量。

### 缺点 {#disadvantages}

* 查看消息执行信息和报告功能稍有延迟，因为从中间采购服务器获取信息所花费的时间很长。
* 调查和Web表单仍保留在客户端平台上。

### 推荐的设备 {#recommended-equipment}

* 应用程序服务器：2 Ghz四核CPU,4 GB RAM，软件RAID 1 80 GB SATA硬盘。
* 数据库服务器：3 GHz双四核CPU，最小4 GB RAM，硬件RAID 10 15000 RPM SAS硬盘，数量取决于数据库的大小和预期性能。

>[!NOTE]
>
>重定向和中部采购是单独的元素，但通常跟踪服务器将与中部采购服务器共享。

## 安装和配置步骤 {#installation-and-configuration-steps-}

### 先决条件 {#prerequisites}

* 应用程序服务器上的JDK。
* 访问应用程序服务器上的数据库服务器。
* 防火墙配置为打开HTTP(80)或HTTPS(443)端口至中间来源服务器。

### 安装和配置（外包部署） {#installing-and-configuring--mid-sourcing-deployment-}

请参阅 [中间采购服务器](../../installation/using/mid-sourcing-server.md)。
