---
product: campaign
title: 在Linux中安装Campaign的先决条件
description: 在 Linux 中安装 Campaign 的先决条件
feature: Installation, Instance Settings
badge-v7-prem: label="仅限本地/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于本地和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# 在Linux上安装Campaign的先决条件{#prerequisites-of-campaign-installation-in-linux}

## 软件先决条件 {#software-prerequisites}

本节详细介绍在安装Adobe Campaign之前所需的初步配置步骤。

安装Adobe Campaign所需的技术和软件配置在[兼容性矩阵](../../rn/using/compatibility-matrix.md)中有详细说明。

提醒一下，需要安装和正确配置以下组件：

* Apache，请参阅[兼容性矩阵](../../rn/using/compatibility-matrix.md)，
* Java JDK和OpenJDK，请参阅[Java开发工具包 — JDK](../../installation/using/application-server.md#jdk)，
* 库，请参阅[库](#libraries)，
* 数据库访问层，请参阅[数据库访问层](#database-access-layers)，
* LibreOffice，请参阅[安装LibreOffice for Debian](#installing-libreoffice-for-debian)和[安装LibreOffice for CentOS](#installing-libreoffice-for-centos)，
* 字体，请参阅用于MTA统计的[字体](#fonts-for-mta-statistics)和用于日语实例的[字体](#fonts-for-japanese-instances)。


### 图书馆 {#libraries}

要在 Linux 中安装 Adobe Campaign，请确保您拥有所需的库。

* 库 C 必须能够支持 TLS（线程本地存储）模式。 此模式在大多数情况下处于活动状态，但某些已禁用 Xen 支持的内核除外。

  例如，要检查这一点，您可以使用 **uname -a | grep xen** 命令。

  如果命令不返回空行，则表示配置正确。

* 您必须具有OpenSSL版本&#x200B;**1.0.2**&#x200B;或更高版本。

  对于RHEL分发，需要1.0版本的OpenSSL。

* 要使用Adobe Campaign，您需要安装&#x200B;**libicu**&#x200B;库。

### SELinux {#selinux}

使用时，必须正确配置 SELinux 模块。

为此，请以root用户身份登录并输入以下命令：

```
echo 0 >/selinux/enforce
```

此外，在&#x200B;**/etc/sysconfig/httpd**&#x200B;文件中，添加了以下行以引用Adobe Campaign环境配置脚本：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，启用SELinux时会发现数据库客户端层存在兼容性问题。 为确保Adobe Campaign能够正常运行，我们建议禁用SELinux。

**应用以下进程：**

* 编辑文件&#x200B;**/etc/selinux/config**

* 按如下方式修改SELINUX行：

```
SELINUX=disabled
```

### MTA统计数据的字体 {#fonts-for-mta-statistics}

为了正确显示MTA统计数据(nms/fra/jsp/stat.jsp)，请添加字体。

在Debian中，添加命令：

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

对RHEL使用以下命令：

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### 日语实例的字体 {#fonts-for-japanese-instances}

若要将报告导出为 PDF 格式，日语实例必须使用特定字符的字体。

在 Debian 中，添加以下命令：

```
apt install fonts-ipafont
```

对于 RHEL，请添加以下命令：

```
dnf install epel-release # if required
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

您正在使用的数据库引擎的访问层必须安装在您的服务器上，并且可以通过 Adobe Campaign 帐户进行访问。 版本和安装模式可能会因所使用的数据库引擎而异。

在[兼容性矩阵](../../rn/using/compatibility-matrix.md)中详细列出了支持的引导版本。

还要检查常规[数据库](../../installation/using/database.md)部分。

### PostgreSQL {#postgresql}

Adobe Campaign支持版本9.6中所有版本的PostgreSQL客户端库： **libpq.so.5**。

将PostgreSQL与Adobe Campaign结合使用还需要安装相应的&#x200B;**pgcrypto**&#x200B;库。

### Oracle {#oracle}

检索 64 位 Debian 的库版本，即：libclntsh.so、libclntsh.so.19.1 **、** libclntsh.so.18.1 **、** libclntsh.so.12.1 **、** libclntsh.so.11.1 **或** libclntsh.so.10.1 **。**&#x200B;**&#x200B;**

您可以从 Oracle 技术网络获取 Linux RPM 软件包。

>[!NOTE]
>
>如果您已经安装了 Oracle 客户端，但全局环境（例如：/etc/profile）配置不正确，则可以将 **缺少的信息添加到 nl6/customer.sh** 脚本 有关此内容的更多信息，请参阅 [环境变量](../../installation/using/installing-packages-with-linux.md#environment-variables)。

**故障排除和最佳做法**

在Oracle客户端或服务器更新、版本更改或首次安装实例时，可能会出现问题。

如果您在客户端控制台上注意到日志、工作流上次处理、下次处理等操作中存在意外的时间延迟（一个或多个小时），则Oracle客户端的库与Oracle服务器之间可能存在问题。 避免此类问题

1. 确保使用&#x200B;**完整客户端**。

   在使用 Oracle 即时客户端版本时发现了各种问题。 此外，无法在即时客户端上更改时区文件。

1. 确保&#x200B;**客户端版本**&#x200B;和&#x200B;**数据库服务器版本**&#x200B;相同&#x200B;**&#x200B;**。

   尽管Oracle的兼容性列表和调整客户端和服务器版本的建议都存在混用版本的情况，但已知会导致问题。

   此外，请检查ORACLE_HOME值以确保它指向预期的客户端版本（如果计算机上安装了多个版本）。

1. 确保客户端和服务器使用相同的&#x200B;**时区文件**。

## 实施步骤 {#implementation-steps}

适用于Linux的Adobe Campaign安装必须按以下顺序执行：服务器安装，实例配置。

本章介绍了安装过程。 安装步骤如下：

* 步骤1：安装应用程序服务器，请参阅[使用Linux安装包](../../installation/using/installing-packages-with-linux.md)。
* 步骤2：与Web服务器集成（可选，具体取决于部署的组件）。

完成安装步骤后，您需要配置实例、数据库和服务器。 有关详细信息，请参阅[关于初始配置](../../installation/using/about-initial-configuration.md)。
