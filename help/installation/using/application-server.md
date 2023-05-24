---
product: campaign
title: 应用程序服务器
description: 应用程序服务器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 1%

---

# 应用程序服务器{#application-server}



必须在服务器上安装所需的数据库访问层，并可从Adobe Campaign帐户访问。

## Java开发工具包 — JDK {#java-development-kit---jdk}

动态网页生成器采用JSP 1.2技术。 为此，应用程序中包含一个Tomcat引擎（来自Apache）。 它要求在所有安装了Adobe Campaign应用程序的服务器上安装Java开发工具包(JDK)。

必须先在要运行Adobe Campaign应用程序服务器的计算机上安装JDK (**nlserver web** 进程)，因为它包含一个servlet容器Apache Tomcat，用于生成动态网页（报表、Web窗体等）。

该应用程序已被批准用于Oracle开发的Java开发工具包(JDK)以及 **OpenJDK**.

Campaign中详细介绍了支持的版本 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>可以使用计算机上其他应用程序已使用的相应JDK版本安装它。
>  
>在安装时，您无需执行与Web浏览器的集成。
>
>在只执行投放代理的计算机上(**nlserver mta** process)或工作流服务器(**nlserver wfserver** 进程)，无需安装JDK。

要下载Java JDK，请连接到： [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**警告：您必须下载JDK，而不是JRE。**

>[!CAUTION]
>
>要保留平台操作性能并确保与已安装版本的兼容性，您必须禁用Windows和Linux中的自动JDK更新功能。

要在Linux环境中安装JDSL，最好使用包管理器。

在Debian 8和9中，使用以下命令：

```
aptitude install openjdk-8-jdk
```

对于RHEL 7，使用以下命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必须安装OpenSSL。 Adobe Campaign支持OpenSSL版本1.0.2或更高版本。

## 导出报告 {#exporting-reports}

Adobe Campaign允许您以Microsoft Excel和Adobe PDF格式导出平台报表。 对于Microsoft Excel格式，Adobe Campaign使用 **LibreOffice**. 对于Adobe PDF格式，Adobe Campaign使用 **PhantomJS** 转换器。 PhantomJs包含在工厂软件包中，LibreOffice必须安装在执行Adobe Campaign应用程序服务器的计算机上(**nlserver web** process)。

>[!NOTE]
>
>对于Linux，您需要添加字体。 有关更多信息，请参阅 [MTA统计信息的字体](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin允许您为电子邮件分配分数，以确定接收时使用的反垃圾邮件工具是否会将邮件视为不受欢迎的邮件。 安装是可选的。

SpamAssassin将电子邮件认定为不受欢迎完全基于筛选和评分规则。 因此，这些规则必须每天至少更新一次，以便您的SpamAssassin安装及其与Adobe Campaign的集成能够完全正常运行，并且保证在发送之前分配给投放的分数的相关性。 此更新由托管SpamAssassin的服务器管理员负责。

支持的最低版本为： **3.4**

SpamAssassin需要HTTP Internet访问(tcp/80)。

SpamAssassin的安装和配置阶段在中介绍 [配置SpamAssassin](../../installation/using/configuring-spamassassin.md).
