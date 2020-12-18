---
solution: Campaign Classic
product: campaign
title: 应用程序服务器
description: 应用程序服务器
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 应用程序服务器{#application-server}

必需的Adobe Campaign库访问层必须安装在服务器上，并可从数据库帐户访问。

## Java开发工具包- JDK {#java-development-kit---jdk}

动态网页生成器采用JSP 1.2技术。 对于此，应用程序中包括Tomcat引擎（来自Apache）。 它需要安装在Adobe Campaign应用程序所在的所有服务器上的Java开发工具包(JDK)。

必须首先在要运行Adobe Campaign应用程序服务器（**nlserver web**&#x200B;进程）的计算机上安装JDK，因为它包含用于生成动态网页(报表、Web 窗体等)的servlet容器,Apache Tomcat。

该应用程序已被批准用于Oracle开发的Java开发工具包(JDK)以及&#x200B;**OpenJDK**。

支持的版本详见活动[兼容性矩阵](../../rn/using/compatibility-matrix.md)。

>[!NOTE]
>
>可以使用计算机上其他应用程序已使用的相应JDK版本安装它。
>  
>安装时，您无需执行与Web浏览器的集成。
>
>在只执行投放代理（**nlserver mta**&#x200B;进程）或工作流服务器（**nlserver wfserver**&#x200B;进程）的计算机上，无需安装JDK。

要下载Java JDK，请连接到：[https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。

**警告：必须下载JDK，而不是JRE。**

>[!CAUTION]
>
>要保持平台操作性能并确保与已安装版本兼容，必须在Windows和Linux中禁用自动JDK更新功能。

要在Linux环境中安装JDSL，最好使用包管理器。

在Debian 8和9中，使用以下命令：

```
aptitude install openjdk-8-jdk
```

对于RHEL 7，请使用以下命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必须安装OpenSSL。 Adobe Campaign支持的版本为&#x200B;**OpenSSL 1.0.1**&#x200B;和&#x200B;**OpenSSL 0.9.8**。 接受0.9.8g到0.9.8o的子版本。

## 导出报告{#exporting-reports}

Adobe Campaign允许您以Microsoft Excel和Adobe PDF格式导出平台报表。 对于Microsoft Excel格式，Adobe Campaign使用&#x200B;**LibreOffice**。 对于Adobe PDF格式，Adobe Campaign使用&#x200B;**PhantomJS**&#x200B;转换器。 工厂包中包含PhantomJs，并且必须在执行Adobe Campaign应用程序服务器的计算机（**nlserver web**&#x200B;进程）上安装LibreOffice。

>[!NOTE]
>
>对于Linux，您需要添加字体。 有关详细信息，请参阅[MTA统计信息的字体](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin允许您为电子邮件分配分数，以确定接收时使用的防垃圾邮件工具是否认为邮件风险是不可取的。 安装是可选的。

SpamAssassin对电子邮件的评级完全基于过滤和评分规则。 因此，必须每天至少更新这些规则一次，以便SpamAssassin安装及其与Adobe Campaign的集成能够全面发挥作用，并确保在发送之前分配给投放的分数的相关性。 此更新由托管SpamAssassin的服务器管理员负责。

支持的最低版本为：**3.4**

SpamAssassin需要HTTP Internet Access(tcp/80)。

[配置SpamAssassin](../../installation/using/configuring-spamassassin.md)中介绍了SpamAssassin的安装和配置阶段。
