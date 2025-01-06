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
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 1%

---

# 应用程序服务器{#application-server}

必须在服务器上安装所需的数据库访问层，并可从Adobe Campaign帐户访问。

## Java开发工具包 — JDK {#jdk}

Java开发工具包（简称JDK）是一个软件开发工具包。 它是实现Java应用程序和Java小程序开发的基础组件。

动态网页生成器采用JSP技术。 为此，应用程序中包含一个Tomcat引擎（来自Apache）。 它要求在所有安装了Adobe Campaign应用程序的服务器上安装Java开发工具包(JDK)。

必须先在要运行Adobe Campaign应用程序服务器（**nlserver web**&#x200B;进程）的计算机上安装JDK，因为它包含用于生成动态网页（报表、Web窗体等）的servlet容器Apache Tomcat。

该应用程序已被批准用于Oracle开发的Java开发工具包(JDK)以及&#x200B;**OpenJDK**。

Campaign [兼容性矩阵](../../rn/using/compatibility-matrix.md)中详细介绍了支持的版本。


>[!AVAILABILITY]
>
>* 从v7.4.1开始，Campaign至少需要&#x200B;**Java JDK 11**。 如果Campaign服务器安装在Windows环境中，则不再自动检测到Java运行时(JRE)。 必须将JRE_HOME环境变量设置为Campaign可以找到`bin/server/jvm.dll`文件的文件夹。 例如，如果JDK 11安装在`C:\Program Files\Java\jdk-11`文件夹下，则JRE_HOME必须为`C:\Program Files\Java\jdk-11`。
>
>* 从v7.4.1开始，Tomcat 10.1是默认版本。
>

### 推荐做法

安装和升级Java Development Kit时，请应用以下建议：

* Java开发套件可以使用计算机上其他应用程序已使用的相应JDK版本进行安装。

* 安装JDK时，不需要与Web浏览器集成。

* 在只执行投放代理（**nlserver mta**&#x200B;进程）或工作流服务器（**nlserver wfserver**&#x200B;进程）的计算机上，不需要安装JDK。

* 升级Java版本时，首先需要卸载以前的版本。 安装在同一台计算机上的两个Java版本都可能会导致冲突。

  作为内部部署客户，您可以检查`LD_LIBRARY_PATH` [环境变量](installing-packages-with-linux.md#environment-variables)是否设置为最新版本(例如， java11)。 如果设置为以前的版本(例如， Java8)，则需要更新。 对于JDK 11，查找JDK库的路径为`/usr/lib/jvm/java-11-openjdk-amd64/lib`。


### 安装步骤

Java开发工具包特定于平台：每个操作系统都需要单独的安装程序。

要下载JDK，请连接到[Oracle网站](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}。

>[!CAUTION]
>
> 请确保下载的是Java开发工具包(JDK)，而不是Java运行时环境(JRE)。


要在Linux环境中安装JDSL，Adobe建议使用包管理器。

对于Debian，使用以下命令：

```sql
apt install openjdk-11-jdk-headless
```

对于RHEL，请使用以下命令：

```sql
dnf install java-11-openjdk-headless
```



## 导出报告 {#exporting-reports}

您可以使用Adobe Campaign将报表导出到Microsoft Excel和Adobe PDF。

* 对于Microsoft Excel格式，Adobe Campaign依赖于&#x200B;**LibreOffice**。

* 对于Adobe PDF格式，Adobe Campaign使用&#x200B;**PhantomJS**&#x200B;转换器。 PhantomJs包含在工厂软件包中，并且LibreOffice必须安装在（**nlserver web**&#x200B;进程）上执行Adobe Campaign应用程序服务器的计算机上。

>[!NOTE]
>
>对于Linux，您需要添加字体。 有关详细信息，请参阅[用于MTA统计数据的字体](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin允许您为电子邮件分配分数，以确定接收时使用的反垃圾邮件工具是否将邮件风险视为不需要。 安装是可选的。

SpamAssassin将电子邮件认定为不受欢迎，完全基于筛选和评分规则。 因此，这些规则必须每天至少更新一次，以便SpamAssassin安装及其与Adobe Campaign的集成能够完全正常运行，并确保在发送之前分配给投放的分数的相关性。 此更新由托管SpamAssassin的服务器管理员负责。

支持的最低版本为： **3.4**

SpamAssassin需要HTTP Internet访问(tcp/80)。

在[配置SpamAssassin](../../installation/using/configuring-spamassassin.md)中提供了SpamAssassin的安装和配置阶段。
