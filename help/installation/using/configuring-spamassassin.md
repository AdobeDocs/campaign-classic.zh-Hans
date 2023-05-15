---
product: campaign
title: 配置 SpamAssassin
description: 配置 SpamAssassin
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 2%

---

# 配置 SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>某些配置只能通过Adobe来执行由Adobe托管的部署。 例如，访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 或 [本页](../../installation/using/capability-matrix.md).

## 概述 {#overview}

SpamAssassin是一款用于过滤不良电子邮件的软件。 与此软件结合使用后，Adobe Campaign可以为电子邮件分配分数，并确定在投放启动之前是否可能认为某个消息是不受欢迎的。 为此，必须在Adobe Campaign的应用程序服务器上安装和配置SpamAssassin ，并需要一定数量的附加Perl模块才能运行。

本章所述的SpamAssassin的部署和集成基于默认软件安装，过滤和评分规则也是基于默认软件安装的，这些规则是SpamAssassin提供的，无需任何修改或优化。 得分归因和消息鉴别完全基于SpamAssassin选项的配置和过滤规则。 网络管理员负责根据公司的需求调整他们的工作。

>[!IMPORTANT]
>
>SpamAssassin对电子邮件不希望的鉴别完全基于过滤和评分规则。
>
>因此，必须每天至少更新一次这些规则，以便SpamAssassin安装及其与Adobe Campaign的集成能够完全正常运行，并确保在发送之前分配给投放的分数的相关性。
>
>此更新由托管SpamAssassin的服务器管理员负责。

在Adobe Campaign中使用SpamAssassin可指示使用SpamAssassin的邮件服务器在收到由Adobe Campaign发送的电子邮件时的可能行为。 但是，互联网提供商或在线邮件服务器的邮件服务器仍可能认为Adobe Campaign发送的邮件是不可取的。

在Perl中部署SpamAssassin及其模块要求Adobe Campaign应用程序服务器配备通过HTTP连接（TCP/80流）进行Internet访问的功能。

## 在Windows计算机上安装 {#installing-on-a-windows-machine}

要在Windows上安装和配置SpamAssassin以启用与Adobe Campaign的集成，请应用以下步骤：

1. 安装SpamAssassin
1. 将SpamAssassin集成到Adobe Campaign

### 安装SpamAssassin {#installing-spamassassin}

1. 连接到 [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 使用您的用户凭据。 了解有关Software Distribution的更多信息，请参阅 [本页](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans?lang=en).
1. 下载 **Neolane Spam Assassin（Windows安装）(2.0)** 文件(neolane_spamassassin.2.0.zip)。
1. 将此文件复制到Adobe Campaign服务器，然后解压缩。

   >[!NOTE]
   >
   >您可以选择根据需要解压缩文件，前提是路径由以下任意正则表达式字符组成： **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. 安装路径不得包含任何空格字符。

1. 转到已解压缩文件的文件，然后双击 **run_me.bat** 文件来启动安装脚本。

   如果出现Windows Shell，并且该Shell继续显示几秒钟，请等待安装和更新完成，然后单击 **输入**.

   如果Windows Shell在立即消失之前未显示或未显示，请执行这些步骤，双击 **portableShell.bat** 文件来显示Windows Shell，并检查Shell路径是否与 **spamassassin.zip** 文件已解压。 如果不是这种情况，请使用 **cd** 命令。

   输入 **run_me.bat** 然后单击 **输入** 以启动安装和更新过程。 该操作会返回以下值之一，以指示更新结果。

   * **0**:已进行更新。
   * **1**:没有新更新可用。
   * **2**:没有新更新可用。
   * **3**:更新在先前验证期间失败。
   * **4** 或更多：发生错误。

1. 要检查SpamAssassin安装是否成功，请按照以下步骤使用GTUBE测试（未经请求的批量电子邮件的通用测试）：

   1. 创建文本文件，并将其保存在 **C:\TestSpamMail.txt**.
   1. 在文件中插入以下内容：

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. 双击 **portableShell.bat** 文件来显示Windows Shell，然后启动以下命令(或“`<root>`“ ”在解压缩时指定已创建的文件夹  **spamassassin.zip** 文件):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此测试电子邮件的内容会触发SpamAssassin的1,000分。 这意味着，它被检测为不需要，并且安装成功并且完全正常。

### 将SpamAssassin集成到Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 编辑 **`[INSTALL]/conf/serverConf.xml`** 文件。 中所有可用的参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).
1. 更改 **spamCheck** elements&#39; **命令** 属性 **Web** 节点。 为此，请运行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路径都必须是绝对路径。

   停止并启动 **[!UICONTROL Adobe Campaign]** 服务。

1. 要在Adobe Campaign中检查SpamAssassin的集成，请使用GTBUE测试（未经请求的批量电子邮件的通用测试）：

   双击 **portableshell.bat** 文件。 这会触发Windows Shell的显示。 然后，运行以下命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此测试电子邮件的内容会触发由SpamAssassin分配的1,000个点数。 这意味着，它被检测为不良，在Adobe Campaign的集成成功，并且完全正常。

1. 更新SpamAssassin过滤和评分规则

   要初步更新过滤和评分规则，请开始 **portableShell.bat** 并运行以下命令：

   ```
   sa-update --no-gpg
   ```

   要运行过滤和评分规则的自动更新，请在计划系统任务中使用以下相同命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux计算机上安装 {#installing-on-a-linux-machine}

### Debian中的安装步骤 {#installation-steps-in-debian}

* 如有必要，请使用以下命令安装Perl和SpamAssassin:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* 在 **serverConf.xml** 文件(在 `/usr/local/[INSTALL]/nl6/conf/`)，请更改 **spamCheck** 行如下：

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### RHEL/CentOS中的安装步骤 {#installation-steps-in-rhel-centos}

如有必要，请安装Perl并使用CPAN恢复包：

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### 更新过滤器规则 {#updating-filter-rules}

可以使用 **sa-update** 工具。 请参阅官方的SpamAssassin网站 [https://spamassassin.apache.org/](https://spamassassin.apache.org/) 以了解更多信息。

在Debian中，每天会自动进行更新。

如果情况并非如此（例如，手动安装Debian时），请创建脚本以自动更新规则。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

将此脚本插入 **crontab** 使用以下命令：

```
crontab-e
```

### 性能优化 {#performance-optimization}

要提高Linux中的性能，请编辑 **/etc/spamassassin/local.cf** ，并在文件末尾添加以下行：

```
dns_available no
```
