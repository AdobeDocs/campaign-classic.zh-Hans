---
title: 在 Linux 中安装 Campaign 的先决条件
seo-title: 在 Linux 中安装 Campaign 的先决条件
description: 在 Linux 中安装 Campaign 的先决条件
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 4%

---


# 在 Linux 中安装 Campaign 的先决条件{#prerequisites-of-campaign-installation-in-linux}

## 软件先决条件 {#software-prerequisites}

本节详细介绍安装Adobe Campaign前所需的初步配置步骤。

安装Adobe Campaign所需的技术和软件配置详见兼容性 [表](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)。

作为提醒，需要安装并正确配置以下组件：

* Apache，请参阅 [兼容性表](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html),
* Java JDK和OpenJDK，请参 [阅Java开发工具包- JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* 库，请参阅 [库](#libraries),
* 数据库访问层，参 [考数据库访问层](#database-access-layers),
* LibreOffice，请参 [阅安装LibreOffice for Debian](#installing-libreoffice-for-debian)[和安装LibreOffice for CentOS](#installing-libreoffice-for-centos),
* 字体，请参阅字 [体以了解MTA统计信息](#fonts-for-mta-statistics) , [以及日文实例的字体](#fonts-for-japanese-instances)。

>[!NOTE]
>
>要在CentOS 7和Debian 8平台上安装低于或等于8709的内部版本，必须启用apache access_compat模块。

### 库 {#libraries}

要在Linux中安装Adobe Campaign，请确保您拥有所需的库。

* 库C必须能够支持TLS(线程本地存储)模式。 除某些已禁用Xen支持的内核外，此模式在大多数情况下都处于活动状态。

   要检查此项，可以使 **用uname -a | grep xen** 命令。

   如果命令未返回任何内容（空行），则表示配置正确。

* 您必须 **具有0.9.8** 或 **1.0** 版OpenSSL。

   对于RHEL 7分发版，需要OpenSSL的1.0版。

* 要使用Adobe Campaign，您需要安 **装** libicu库。

   支持以下 **版本** （32位或64位）:

   * RHEL 7, CentOS 7:libicu50
   * 德比安8:libicu52
   * 德比安9:libicu57

   要使用Adobe Campaign，您需要安装libc-ares库。 在RHEL/CentOS上，运行以下命令：

   ```
   yum install c-ares
   ```

   在德比安：

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

使用时，必须正确配置SELinux模块。

为此，请以root身份登录并输入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在/etc/ **sysconfig/httpd文件中** ，添加了以下行以引用Adobe Campaign环境配置脚本：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，在启用SELinux时，会注意到与数据库客户端层的兼容性问题。 为确保Adobe Campaign能够正确运行，我们建议禁用SELinux。

**应用以下流程：**

* 编辑文 **件/etc/selinux/config**

* 按如下方式修改SELINUX行：

```
SELINUX=disabled
```

### 用于MTA统计的字体 {#fonts-for-mta-statistics}

为了正确显示MTA统计(nms/fra/jsp/stat.jsp)报告，请添加字体。

在Debian中，添加命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### 日文实例的字体 {#fonts-for-japanese-instances}

要将报表导出为PDF格式，日文实例需要特定字符的字体。

在Debian中，添加命令：

```
aptitude install fonts-ipafont
```

在Red Hat中，添加命令：

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### 安装LibreOffice for Debian {#installing-libreoffice-for-debian}

对于Debian，需要以下配置：

1. 安装以下标准包：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安装以下字体（对于日语实例，可选但强烈建议使用）:

   ```
   apt-get install fonts-ipafont
   ```

### 安装LibreOffice for CentOS {#installing-libreoffice-for-centos}

CentOS必须进行以下配置：

1. 安装以下标准包：

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. 安装以下字体（可选，但强烈建议用于日文实例）:

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## 数据库访问层 {#database-access-layers}

您所使用的Adobe Campaign库引擎的访问层必须安装在服务器上，并可通过数据库帐户访问。 版本和安装模式可能因所使用的数据库引擎而异。

兼容性矩阵中详细介绍了支持的 [导频版本](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)。

另请检查“一般数 [据库](../../installation/using/database.md) ”部分。

### PostgreSQL {#postgresql}

Adobe Campaign支持7.2版的所有PostgreSQL客户端库：(**libpq.so.5**、 **libpq.so.4**、 **libpq.so.3.2** 和 **** libpq.so.3.1)。

将PostgreSQL与Adobe Campaign一起使用还需要安装相 **应的** pgcrypto库。

### Oracle {#oracle}

检索64位Debian的库版本，即： **libclntsh.so**、 **libclntsh.so.11.1****和libclntsh.so.10.1**。

您可以从Oracle Technology Network获取Linux RPM包。

>[!NOTE]
>
>如果已安装Oracle客户端，但已安装全局环境(例如：/etc/用户档案)未正确配置，您可以向nl6/customer.sh脚本添加缺 **失信息** 。有关详细信息，请参阅 [环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables)。

**疑难解答和最佳实践**

在Oracle客户端或服务器更新、版本更改后或实例的首次安装时，可能会出现问题。

如果您在客户端控制台上注意到日志、工作流上次处理、下次处理等中存在意外的延迟时间（一个或多个小时），则Oracle客户端的库与Oracle Server之间可能存在问题。 要避免此类问题

1. 确保使用完整 **客户端**。

   在使用Oracle Instant Client版本时已发现各种问题。 此外，在即时客户端上更改时区文件是不可能的。

1. 确保客户端 **版本和** 数据 **库服务器版** 本相 **同**。

   尽管Oracle有兼容性矩阵，并且建议将客户端和服务器版本相协调，但混合使用不同版本仍会导致问题。

   另外，检查ORACLE_HOME值，确保它指向预期的客户端版本（如果计算机上安装了多个版本）。

1. 确保客户端和服务器使用相同的 **时区文件**。

### DB2 {#db2}

支持的库版本 **为libdb2.so**。

## 实施步骤 {#implementation-steps}

Adobe CampaignLinux安装必须按以下顺序进行：服务器安装后跟实例配置。

本章介绍了安装过程。 安装步骤如下：

* 第1步：安装应用程序服务器，请参 [阅安装Linux包](../../installation/using/installing-packages-with-linux.md)。
* 第2步：与Web服务器集成（可选，具体取决于所部署的组件）。

安装步骤完成后，您需要配置实例、数据库和服务器。 有关此功能的详细信息，请参 [阅关于初始配置](../../installation/using/about-initial-configuration.md)。
