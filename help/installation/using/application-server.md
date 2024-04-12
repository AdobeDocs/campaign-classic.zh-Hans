---
product: campaign
title: 应用程序服务器
description: 应用程序服务器
feature: Installation
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# 应用程序服务器{#application-server}



必须在服务器上安装所需的数据库访问层，并可从Adobe Campaign帐户访问。

## Java开发工具包 — JDK {#java-development-kit---jdk}

动态网页生成器采用JSP 1.2技术。 为此，应用程序中包含一个Tomcat引擎（来自Apache）。 它要求在所有安装了Adobe Campaign应用程序的服务器上安装Java开发工具包(JDK)。

必须先在要运行Adobe Campaign应用程序服务器的计算机上安装JDK(**nlserver web** 进程)，因为它包含一个servlet容器Apache Tomcat，用于生成动态网页（报表、Web窗体等）。

该应用程序已被批准用于Oracle开发的Java开发工具包(JDK)以及用于 **OpenJDK**.

Campaign中详细介绍了支持的版本 [兼容性矩阵](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>可以使用计算机上其他应用程序已使用的相应JDK版本来安装它。
>  
>安装时，您无需与Web浏览器执行集成。
>
>在仅执行投放代理的计算机上(**nlserver mta** process)或工作流服务器(**nlserver wfserver** 进程)，则无需安装JDK。

要下载Java JDK，请连接到： [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**警告：您必须下载JDK，而不是JRE。**

>[!CAUTION]
>
>要保留平台操作性能并确保与已安装的版本兼容，您必须在Windows和Linux中禁用自动JDK更新功能。

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

通过Adobe Campaign，您可以将Platform报表导出为Microsoft Excel和Adobe PDF格式。 对于Microsoft Excel格式，Adobe Campaign使用 **LibreOffice**. 对于Adobe PDF格式，Adobe Campaign使用 **PhantomJS** 转化因素。 PhantomJs包含在工厂软件包中，LibreOffice必须安装在执行Adobe Campaign应用程序服务器的计算机上(**nlserver web** 流程)。

>[!NOTE]
>
>对于Linux，您需要添加字体。 有关详细信息，请参见 [MTA统计数据的字体](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin允许您为电子邮件分配分数，以确定接收时使用的反垃圾邮件工具是否将邮件风险视为不需要。 安装是可选的。

SpamAssassin将电子邮件认定为不受欢迎，完全基于筛选和评分规则。 因此，这些规则必须每天至少更新一次，以便SpamAssassin安装及其与Adobe Campaign的集成能够完全正常运行，并确保在发送之前分配给投放的分数的相关性。 此更新由托管SpamAssassin的服务器管理员负责。

支持的最低版本为： **3.4**

SpamAssassin需要HTTP Internet访问(tcp/80)。

SpamAssassin的安装和配置阶段在中介绍 [配置SpamAssassin](../../installation/using/configuring-spamassassin.md).
