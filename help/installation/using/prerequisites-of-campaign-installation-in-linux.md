---
solution: Campaign Classic
product: campaign
title: 在 Linux 中安装 Campaign 的先决条件
description: 在 Linux 中安装 Campaign 的先决条件
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: ae4b2ba6db140cdfb9ec4a38231fcc3e54b1478c
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 1%

---


# 在Linux{#prerequisites-of-campaign-installation-in-linux}上安装活动的先决条件

## 软件先决条件{#software-prerequisites}

本节详细介绍安装Adobe Campaign前所需的初步配置步骤。

安装Adobe Campaign所需的技术和软件配置详见[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

作为提醒，需要安装并正确配置以下组件：

* Apache， refer to [ Compatibility matrix](../../rn/using/compatibility-matrix.md),
* Java JDK和OpenJDK，请参阅[Java开发工具包 — JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* 库，请参阅[库](#libraries),
* 数据库访问层，请参阅[数据库访问层](#database-access-layers),
* LibreOffice，请参阅[安装LibreOffice for Debian](#installing-libreoffice-for-debian)和[安装LibreOffice for CentOS](#installing-libreoffice-for-centos),
* 字体，请参阅[用于MTA统计信息的字体](#fonts-for-mta-statistics)和用于日语实例的字体](#fonts-for-japanese-instances)。[

>[!NOTE]
>
>要在CentOS 7和Debian 8平台上安装低于或等于8709的内部版本，必须启用apache access_compat模块。

### 库{#libraries}

要在Linux中安装Adobe Campaign，请确保您拥有所需的库。

* 库C必须能够支持TLS(线程本地存储)模式。 除某些内核已禁用Xen支持外，此模式在大多数情况下都处于活动状态。

   要检查此问题，可以使用&#x200B;**uname -a 例如| grep xen**&#x200B;命令。

   如果命令未返回任何内容（空行），则表示配置正确。

* 您必须具有OpenSSL的&#x200B;**版本0.9.8**&#x200B;或&#x200B;**1.0**。

   对于RHEL 7分发版，需要OpenSSL的1.0版。

* 要使用Adobe Campaign，您需要安装&#x200B;**libicu**&#x200B;库。

   支持以下版本的&#x200B;**libicu**（32位或64位）：

   * RHEL 7、CentOS 7:libicu50
   * 德比安8:libicu52
   * 德比亚9:libicu57

   要使用Adobe Campaign，您需要安装libc-ares库。 在RHEL/CentOS上，运行以下命令：

   ```
   yum install c-ares
   ```

   在德比亚：

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

使用时，必须正确配置SELinux模块。

为此，请以root身份登录并输入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在&#x200B;**/etc/sysconfig/httpd**&#x200B;文件中，添加了以下行以引用Adobe Campaign环境配置脚本：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，当启用SELinux时，会发现与数据库客户端层的兼容性问题。 为确保Adobe Campaign能够正确运行，建议禁用SELinux。

**应用以下流程：**

* 编辑文件&#x200B;**/etc/selinux/config**

* 修改SELINUX行，如下所示：

```
SELINUX=disabled
```

### MTA统计数据{#fonts-for-mta-statistics}的字体

为了正确显示有关MTA统计数据(nms/fra/jsp/stat.jsp)的报告，请添加字体。

在Debian中，添加命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### 日文实例的字体{#fonts-for-japanese-instances}

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

1. 安装以下字体（可选，但强烈建议用于日文实例）：

   ```
   apt-get install fonts-ipafont
   ```

### 安装CentOS {#installing-libreoffice-for-centos}的LibreOffice

CentOS需要以下配置：

1. 安装以下标准包：

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. 安装以下字体（可选，但强烈建议用于日文实例）：

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## 数据库访问层{#database-access-layers}

您所使用的数据库引擎的访问层必须安装在服务器上，并可通过Adobe Campaign帐户访问。 版本和安装模式可能因所使用的数据库引擎而异。

[兼容性矩阵](../../rn/using/compatibility-matrix.md)中详细介绍了支持的导频版本。

另请检查常规[Database](../../installation/using/database.md)部分。

### PostgreSQL {#postgresql}

Adobe Campaign支持7.2版中的所有版本的PostgreSQL客户端库：（**libpq.so.5**、**libpq.so.4**、**libpq.so.3.2**&#x200B;和&#x200B;**libpq.so.3.1**）。

将PostgreSQL与Adobe Campaign一起使用还需要安装相应的&#x200B;**pgcrypto**&#x200B;库。

### Oracle {#oracle}

检索64位Debian的库版本，即：**libclntsh.so**、**libclntsh.so.11.1**&#x200B;和&#x200B;**libclntsh.so.10.1**。

您可以从Oracle技术网获取Linux RPM包。

>[!NOTE]
>
>如果已安装Oracle客户端，但已安装全局环境(例如：/etc/用户档案)未正确配置，您可以向&#x200B;**nl6/customer.sh**&#x200B;脚本添加缺失信息。有关详细信息，请参阅[环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables)。

**疑难解答和最佳实践**

在Oracle客户端或服务器更新、版本更改后或实例的第一次安装时，可能会出现问题。

如果您在客户端控制台上注意到日志、工作流上次处理、下次处理等中存在意外的时间延迟（一个或多个小时），则Oracle客户端的库与Oracle服务器之间可能存在问题。 要避免此类问题

1. 确保使用&#x200B;**完整客户端**。

   在使用Oracle Instant Client版本时已发现各种问题。 此外，在即时客户端上更改时区文件是不可能的。

1. 确保&#x200B;**客户端版本**&#x200B;和&#x200B;**数据库服务器版本**&#x200B;是&#x200B;**相同**。

   尽管有Oracle的兼容性矩阵和调整客户端和服务器版本的建议，但混合版本仍然会导致问题。

   同时检查ORACLE_HOME值，确保它指向预期的客户端版本（如果计算机上安装了多个版本）。

1. 确保客户端和服务器使用相同的&#x200B;**时区文件**。

### DB2 {#db2}

支持的库版本为&#x200B;**libdb2.so**。

## 实施步骤 {#implementation-steps}

Adobe Campaign安装Linux必须按以下顺序进行：服务器安装后跟实例配置。

本章将介绍安装过程。 安装步骤如下：

* 第1步：安装应用程序服务器，请参阅[安装Linux](../../installation/using/installing-packages-with-linux.md)包。
* 第2步：与Web服务器集成（可选，具体取决于所部署的组件）。

安装步骤完成后，您需要配置实例、数据库和服务器。 有关详细信息，请参阅[关于初始配置](../../installation/using/about-initial-configuration.md)。
