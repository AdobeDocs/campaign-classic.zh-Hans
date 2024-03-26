---
product: campaign
title: 中间源部署
description: 中间源部署
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 4%

---

# 中间源部署{#mid-sourcing-deployment}



此配置是托管(ASP)配置与内部化之间的最佳中间解决方案。 在Adobe Campaign托管的“中间源”服务器上执行面向外部的执行组件。

>[!NOTE]
>
>要设置此类型的部署，您需要获取相应的选项。 请检查您的许可合同。

服务器和进程之间的一般通信按照以下模式进行：

![](assets/s_ncs_install_midsourcing.png)

* 实例上已禁用执行和退回管理模块。
* 应用程序配置为在使用SOAP调用（通过HTTP或HTTPS）驱动的远程“中源”服务器上执行消息。

## 功能 {#features}

### 优点 {#advantages}

* 简化的服务器配置：客户无需配置面向外部的模块（mta和inMail）。
* 带宽使用受限：由于执行由中间源服务器执行，因此只需要足够的带宽即可将个性化数据发送到中间源服务器。
* 高可用性不再是一个内部问题：问题已转移到中间源服务器（重定向、镜像页面、执行服务器等）。
* 数据库不会离开公司：只有汇编消息所需的数据才会发送到中间源服务器（HTTPS可用于此目的）。
* 这种类型的部署可以作为高容量体系结构（数据库中的许多接收方）的解决方案，具有显着的投放吞吐量。

### 缺点 {#disadvantages}

* 由于从中间源服务器获取信息所需的时间，在查看消息执行信息和报告功能方面略有延迟。
* 调查和Web窗体仍保留在客户端平台上。

### 推荐的设备 {#recommended-equipment}

* 应用程序服务器：2 Ghz四核CPU、4 GB RAM、软件RAID 1 80 GB SATA硬盘。
* 数据库服务器：3 GHz双四核CPU、最低4 GB RAM、硬件RAID 10 15000RPM SAS硬盘，数量取决于数据库的大小和预期性能。

>[!NOTE]
>
>重定向和中间源是独立的元素，但通常跟踪服务器将与中间源服务器共享。

## 安装和配置步骤 {#installation-and-configuration-steps-}

### 先决条件 {#prerequisites}

* 应用程序服务器上的JDK。
* 访问应用程序服务器上的数据库服务器。
* 防火墙配置为打开HTTP (80)或HTTPS (443)端口到中间源服务器。

### 安装和配置（中间源部署） {#installing-and-configuring--mid-sourcing-deployment-}

请参阅 [中间源服务器](../../installation/using/mid-sourcing-server.md).
