---
title: 应用程序服务器
seo-title: 应用程序服务器
description: 应用程序服务器
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 应用程序服务器{#application-server}

必须在服务器上安装所需的数据库访问层，并可从Adobe Campaign帐户访问。

## Java开发工具包- JDK {#java-development-kit---jdk}

动态网页生成器采用JSP 1.2技术。 为此，应用程序中包含一个Tomcat引擎（来自Apache）。 它需要一个Java开发工具包(JDK)，它安装在安装了Adobe Campaign应用程序的所有服务器上。

必须首先在要运行Adobe Campaign应用程序服务器(**nlserver web** process)的计算机上安装JDK，因为它包含用于生成动态网页（报表、Web表单等）的servlet容器Apache Tomcat。

该应用程序已经被批准用于Oracle开发的Java开发工具包(JDK)以及 **OpenJDK**。

兼容性矩阵中详细介绍了支持 [的版本](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

>[!NOTE]
>
>可以使用计算机上其他应用程序已使用的相应JDK版本安装它。
>  
>安装时，您无需执行与Web浏览器的集成。
>
>在只执行交付代理(**nlserver mta** process)或工作流服务器(**** nlserver wfserver process)的计算机上，无需安装JDK。

要下载Java JDK，请连接到： [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。

**警告：必须下载JDK，而不是JRE。**

>[!CAUTION]
>
>要保持平台操作性能并确保与已安装版本兼容，必须在Windows和Linux中禁用自动JDK更新功能。

要在Linux环境中安装JDSL，最好使用包管理器。

在Debian 7和8中，使用以下命令：

```
aptitude install openjdk-7-jdk
```

对于RHEL 6，请使用以下命令：

```
yum install java-1.8.0-openjdk
```

对于RHEL 7，请使用以下命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必须安装OpenSSL。 Adobe Campaign支持的版本 **为OpenSSL 1.0.1** 和 **OpenSSL 0.9.8**。 子版本0.9.8g至0.9.8o已接受。

>[!NOTE]
>
>对于RHEL 6和CentOS 6，需要openSSL 1.0。

## 导出报告 {#exporting-reports}

Adobe Campaign允许您以Microsoft excel和Adobe PDF格式导出平台报表。 对于Microsoft excel格式，Adobe Campaign使用 **LibreOffice**。 对于Adobe PDF格式，Adobe Campaign使用 **PhantomJS转换程序** 。 PhantomJs包含在工厂包中，并且LibreOffice必须安装在执行Adobe Campaign应用程序服务器(nlserver **web进程** )的计算机上。

>[!NOTE]
>
>对于Linux，您需要添加字体。 有关详细信息，请参阅 [Fonts for MTA统计信息](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin允许您为电子邮件分配分数，以确定接收时使用的防垃圾邮件工具是否认为邮件风险是不可取的。 安装是可选的。

SpamAssassin对电子邮件的评级是完全基于过滤和评分规则。 因此，必须每天至少更新这些规则一次，以便SpamAssassin安装及其与Adobe Campaign的集成能够全面发挥作用，并确保在发送之前分配给您的分发的分数的相关性。 此更新由承载SpamAssassin的服务器管理员负责。

支持的最低版本为： **3.2.5** 和 **3.3.2**。

SpamAssassin需要HTTP Internet访问(tcp/80)。

配置SpamAssassin中介绍了SpamAssassin的安装和 [配置阶段](../../installation/using/configuring-spamassassin.md)。
