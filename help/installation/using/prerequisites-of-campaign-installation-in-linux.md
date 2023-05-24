---
product: campaign
title: 在 Linux 中安装 Campaign 的先决条件
description: 在 Linux 中安装 Campaign 的先决条件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 1%

---

# 在Linux上安装Campaign的先决条件{#prerequisites-of-campaign-installation-in-linux}



## 软件先决条件 {#software-prerequisites}

本节详细介绍在安装Adobe Campaign之前所需的初步配置步骤。

有关安装Adobe Campaign所需的技术和软件配置的详情，请参见 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

提醒一下，需要安装和正确配置以下组件：

* Apache，请参阅 [兼容性矩阵](../../rn/using/compatibility-matrix.md)，
* Java JDK和OpenJDK，请参阅 [Java开发工具包 — JDK](../../installation/using/application-server.md#java-development-kit---jdk)，
* 库，请参阅 [库](#libraries)，
* 数据库访问层，请参阅 [数据库访问层](#database-access-layers)，
* LibreOffice，请参阅 [安装LibreOffice for Debian](#installing-libreoffice-for-debian) 和 [安装LibreOffice for CentOS](#installing-libreoffice-for-centos)，
* 字体，请参阅 [MTA统计信息的字体](#fonts-for-mta-statistics) 和 [日语实例的字体](#fonts-for-japanese-instances).

>[!NOTE]
>
>要在CentOS 7和Debian 8平台上安装版本低于或等于8709，必须启用apache access_compat模块。

### 库 {#libraries}

要在Linux中安装Adobe Campaign，请确保您拥有所需的库。

* 库C必须能够支持TLS（线程本地存储）模式。 在大多数情况下，此模式处于活动状态，但某些内核禁用了Xen支持。

   要检查此项，您可以使用 **uname -a |希腊xen** 命令。

   如果命令未返回任何内容（空行），则表示配置正确。

* 您必须具有OpenSSL版本 **1.0.2** 或更高。

   对于RHEL 7/8分发，需要OpenSSL版本1.0。

* 要使用Adobe Campaign，您需要拥有 **利比库** 库已安装。

   以下版本的 **利比库** 受支持（32位或64位）：

   * RHEL 7/8、CentOS 7：libicu50
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

在使用时，必须正确配置SELinux模块。

为此，请以root用户身份登录并输入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在 **/etc/sysconfig/httpd** 文件，添加了以下行以引用Adobe Campaign环境配置脚本：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，当启用SELinux时，注意到数据库客户端层的兼容性问题。 为确保Adobe Campaign能够正常运行，我们建议禁用SELinux。

**应用以下进程：**

* 编辑文件 **/etc/selinux/config**

* 按如下方式修改SELINUX行：

```
SELINUX=disabled
```

### MTA统计信息的字体 {#fonts-for-mta-statistics}

为了正确显示有关MTA统计信息(nms/fra/jsp/stat.jsp)的报告，请添加字体。

在Debian中，添加命令：

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

在Red Hat中，添加命令：

* 对于RHEL 7：

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

### 安装LibreOffice for CentOS {#installing-libreoffice-for-centos}

CentOS需要以下配置：

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## 数据库访问层 {#database-access-layers}

您使用的数据库引擎的访问层必须安装在您的服务器上，并可通过Adobe Campaign帐户访问。 版本和安装模式可能会因所使用的数据库引擎而异。

支持的试点测试版本详见 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

同时检查常规 [数据库](../../installation/using/database.md) 部分。

### PostgreSQL {#postgresql}

Adobe Campaign支持版本7.2中的PostgreSQL客户端库的所有版本： (**libpq.so.5**， **libpq.so.4**， **libpq.so.3.2** 和 **libpq.so.3.1**)。

在Adobe Campaign中使用PostgreSQL还需要安装相应的 **pgcrypto** 库。

### Oracle {#oracle}

检索64位Debian的库版本，即： **libclntsh.so**， **libclntsh.so.11.1** 和 **libclntsh.so.10.1**.

您可以从Oracle技术网获取Linux RPM软件包。

>[!NOTE]
>
>如果您已安装Oracle客户端，但全局环境（例如： /etc/profile）配置不正确，则可以将缺少的信息添加到 **nl6/customer.sh** 脚本有关更多信息，请参阅 [环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables).

**疑难解答和最佳实践**

在Oracle客户端或服务器更新、版本更改或首次安装实例时，可能会出现问题。

如果您在客户端控制台上注意到日志、上次处理工作流、下次处理等操作中存在意外的时间延迟（一个或多个小时），则Oracle客户端的库与Oracle服务器之间可能存在问题。 避免此类问题

1. 确保使用 **完整客户端**.

   在使用OracleInstant Client版本时发现了各种问题。 此外，不可能在即时客户端上更改时区文件。

1. 确保 **客户端版本** 和 **数据库服务器版本** 是 **相同**.

   尽管Oracle的兼容性列表和调整客户端和服务器版本的建议，但混合版本已知会导致问题。

   另外，请检查ORACLE_HOME值，确保它指向预期的客户端版本（如果计算机上安装了多个版本）。

1. 确保客户端和服务器使用相同的 **时区文件**.

### DB2 {#db2}

支持的库版本为 **libdb2.so**.

## 实施步骤 {#implementation-steps}

适用于Linux的Adobe Campaign安装必须按以下顺序执行：服务器安装，实例配置。

本章介绍了安装过程。 安装步骤如下：

* 步骤1：安装应用程序服务器，请参阅 [在Linux中安装软件包](../../installation/using/installing-packages-with-linux.md).
* 步骤2：与Web服务器集成（可选，具体取决于部署的组件）。

完成安装步骤后，您需要配置实例、数据库和服务器。 有关更多信息，请参阅 [关于初始配置](../../installation/using/about-initial-configuration.md).
