---
product: campaign
title: 在Linux中安装Campaign的先决条件
description: 在Linux中安装Campaign的先决条件
feature: Installation, Instance Settings
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---

# 在Linux上安装Campaign的先决条件{#prerequisites-of-campaign-installation-in-linux}



## 软件先决条件 {#software-prerequisites}

本节详细介绍在安装Adobe Campaign之前所需的初步配置步骤。

有关安装Adobe Campaign所需的技术和软件配置的详情，请参见 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

提醒一下，需要安装和正确配置以下组件：

* Apache，参考 [兼容性矩阵](../../rn/using/compatibility-matrix.md)，
* Java JDK 和 OpenJDK，请参阅 [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk)，
* 图书馆，参考 [图书馆](#libraries)，
* 数据库访问层，请参阅 [数据库访问层](#database-access-layers)，
* LibreOffice，请参阅 [安装LibreOffice for Debian](#installing-libreoffice-for-debian) 和 [安装LibreOffice for CentOS](#installing-libreoffice-for-centos)，
* 字体，请参阅 [MTA统计数据的字体](#fonts-for-mta-statistics) 和 [日语实例的字体](#fonts-for-japanese-instances).

>[!NOTE]
>
>要在CentOS 7和Debian 8平台上安装版本低于或等于8709，必须启用apache access_compat模块。

### 库 {#libraries}

要在 Linux 中安装 Adobe Campaign，请确保您拥有所需的库。

* 库 C 必须能够支持 TLS（线程本地存储）模式。 此模式在大多数情况下处于活动状态，但某些已禁用 Xen 支持的内核除外。

  例如，要检查这一点，您可以使用 **uname -a | grep xen** 命令。

  如果命令未返回任何内容（空行），则表示配置正确。

* 您必须具有OpenSSL版本 **1.0.2** 或更高。

  对于RHEL 7/8分发，需要1.0版本的OpenSSL。

* 要使用Adobe Campaign，您需要拥有 **利比库** 库已安装。

  以下版本的 **利比库** 受支持（32位或64位）：

   * RHEL 7/8，CentOS 7：libicu50
   * Debian 8： libicu52
   * Debian 9： libicu57

  要使用Adobe Campaign，您需要安装libc-ares库。 在RHEL/CentOS上，运行以下命令：

  ```
  yum install c-ares
  ```

  在Debian上：

  ```
  aptitude install libc-ares2
  ```

### SELinux {#selinux}

使用时，必须正确配置 SELinux 模块。

为此，请以root用户身份登录并输入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在 **/etc/sysconfig/httpd** 文件，添加了以下行以引用Adobe Campaign环境配置脚本：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，启用SELinux时会发现数据库客户端层存在兼容性问题。 为确保Adobe Campaign能够正常运行，我们建议禁用SELinux。

**应用以下流程：**

* 编辑文件 **/etc/selinux/config**

* 修改 SELINUX 行，如下所示：

```
SELINUX=disabled
```

### MTA 统计信息的字体 {#fonts-for-mta-statistics}

要正确显示有关 MTA 统计信息的报告 （nms/fra/jsp/stat.jsp），请添加字体。

在 Debian 中，添加以下命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

* 对于CentOS/RHEL 7：

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* 对于RHEL 8：

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### 日语实例的字体 {#fonts-for-japanese-instances}

要将报表导出为PDF格式，日语实例需要特定字符的字体。

在Debian中，添加命令：

```
aptitude install fonts-ipafont
```

在 Red Hat 中，添加以下命令：

* 对于 RHEL 7：

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* 对于RHEL 8：

  ```
  dnf install vlgothic-fonts
  ```

### 安装LibreOffice for Debian {#installing-libreoffice-for-debian}

对于Debian，需要以下配置：

1. 安装以下标准包：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安装以下字体（可选，但强烈建议用于日语实例）：

   ```
   apt-get install fonts-ipafont
   ```

### 安装 LibreOffice for CentOS {#installing-libreoffice-for-centos}

CentOS 需要以下配置：

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## 数据库访问层 {#database-access-layers}

您所使用的数据库引擎的访问层必须安装在您的服务器上，并且可通过Adobe Campaign帐户访问。 版本和安装模式可能会因所使用的数据库引擎而异。

有关支持的试点版本详情，请参见 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

同时检查常规 [数据库](../../installation/using/database.md) 部分。

### PostgreSQL {#postgresql}

Adobe Campaign支持版本7.2中的所有PostgreSQL客户端库版本： (**libpq.so.5**， **libpq.so.4**， **libpq.so.3.2** 和 **libpq.so.3.1**)。

将PostgreSQL与Adobe Campaign结合使用还需要安装相应的 **pgcrypto** 库。

### Oracle {#oracle}

检索64位Debian的库版本，即： **libclntsh.so**， **libclntsh.so.11.1** 和 **libclntsh.so.10.1**.

您可以从Oracle技术网获取Linux RPM软件包。

>[!NOTE]
>
>如果您已经安装了Oracle客户端，但全局环境（例如： /etc/profile）配置不正确，则可以将缺少的信息添加到 **nl6/customer.sh** 脚本有关更多信息，请参阅 [环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables).

**疑难解答和最佳实践**

在 Oracle 客户端或服务器更新、版本更改或首次安装实例时可能会出现问题。

如果您在客户端控制台上注意到日志、工作流上次处理、下一次处理等存在意外的时间延迟（一个或多个小时），则可能是 Oracle 客户端的库和 Oracle 服务器之间存在问题。 避免此类问题

1. 确保使用 **完整客户端**.

   在使用OracleInstant Client版本时发现了各种问题。 此外，不可能在即时客户端上更改时区文件。

1. 确保 **客户端版本** 和 **数据库服务器版本** 是 **相同**.

   众所周知，尽管 Oracle 具有兼容性矩阵并建议调整客户端和服务器版本，但混合使用版本会导致问题。

   还要检查ORACLE_HOME值以确保它指向预期的客户端版本（以防计算机上安装了多个版本）。

1. 确保客户端和服务器使用相同的 **时区文件**。

### DB2 {#db2}

支持的库版本为 **libdb2.so**。

## 实施步骤 {#implementation-steps}

适用于Linux的Adobe Campaign安装必须按以下顺序执行：服务器安装，实例配置。

本章介绍了安装过程。 安装步骤如下：

* 步骤1：安装应用程序服务器，请参阅 [在Linux中安装包](../../installation/using/installing-packages-with-linux.md).
* 步骤2：与Web服务器集成（可选，具体取决于部署的组件）。

完成安装步骤后，您需要配置实例、数据库和服务器。 有关详细信息，请参见 [关于初始配置](../../installation/using/about-initial-configuration.md).
