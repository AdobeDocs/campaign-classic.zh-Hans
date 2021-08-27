---
product: campaign
title: 配置 SpamAssassin
description: 配置 SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 2%

---

# 配置 SpamAssassin{#configuring-spamassassin}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>某些配置只能通过Adobe来执行由Adobe托管的部署。 例如，访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅[托管模型](../../installation/using/hosting-models.md)部分或[此页面](../../installation/using/capability-matrix.md)。

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

1. 使用您的用户凭据连接到[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)。 详细了解[本页](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans?lang=en)中的软件分发。
1. 下载&#x200B;**Neolane Spam Assassin（Windows安装）(2.0)**&#x200B;文件(neolane_spamassassin.2.0.zip)。
1. 将此文件复制到Adobe Campaign服务器，然后解压缩。

   >[!NOTE]
   >
   >如果路径由以下任意正则表达式字符组成，则可以选择根据需要解压缩文件：**`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**。 安装路径不得包含任何空格字符。

1. 转到已解压文件的文件，然后双击&#x200B;**run_me.bat**&#x200B;文件以启动安装脚本。

   如果Windows Shell出现并继续显示几秒钟，请等待安装和更新完成，然后单击&#x200B;**Enter**。

   如果Windows Shell在立即消失之前未显示或未显示，请按照以下步骤操作，双击&#x200B;**portableShell.bat**&#x200B;文件以显示Windows Shell，并检查Shell路径是否与&#x200B;**spamassassin.zip**&#x200B;文件已解压的文件夹相对应。 如果不是这样，请使用&#x200B;**cd**&#x200B;命令访问它。

   输入&#x200B;**run_me.bat**，然后单击&#x200B;**Enter**&#x200B;以开始安装和更新过程。 该操作会返回以下值之一，以指示更新结果。

   * **0**:已进行更新。
   * **1**:没有新更新可用。
   * **2**:没有新更新可用。
   * **3**:更新在先前验证期间失败。
   * **4** 或更多：发生错误。

1. 要检查SpamAssassin安装是否成功，请按照以下步骤使用GTUBE测试（未经请求的批量电子邮件的通用测试）：

   1. 创建一个文本文件，并将其保存在&#x200B;**C:\TestSpamMail.txt**&#x200B;下。
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

   1. 双击&#x200B;**portableShell.bat**&#x200B;文件以显示Windows Shell，然后启动以下命令（或&quot;`<root>`&quot;在解压缩&#x200B;**spamassassin.zip**&#x200B;文件时指定创建的文件夹）：

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此测试电子邮件的内容会触发SpamAssassin的1,000分。 这意味着，它被检测为不需要，并且安装已成功，并且完全正常运行。

### 将SpamAssassin集成到Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 编辑&#x200B;**`[INSTALL]/conf/serverConf.xml`**&#x200B;文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。
1. 在&#x200B;**Web**&#x200B;节点中更改&#x200B;**spamCheck**&#x200B;元素&#39; **command**&#x200B;属性的值。 为此，请运行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路径都必须是绝对路径。

   停止并启动&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;服务。

1. 要在Adobe Campaign中检查SpamAssassin的集成，请使用GTBUE测试（未经请求的批量电子邮件的通用测试）：

   双击&#x200B;**portableshell.bat**&#x200B;文件。 这会触发Windows Shell的显示。 然后，运行以下命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此测试电子邮件的内容会触发由SpamAssassin分配的1,000个点数。 这意味着，它被检测为不良，在Adobe Campaign的集成成功，并且完全正常。

1. 更新SpamAssassin过滤和评分规则

   要初始更新过滤和评分规则，请启动&#x200B;**portableShell.bat**&#x200B;并运行以下命令：

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

* 在&#x200B;**serverConf.xml**&#x200B;文件（在`/usr/local/[INSTALL]/nl6/conf/`中提供）中，按如下方式更改&#x200B;**spamCheck**&#x200B;行：

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

可以使用&#x200B;**sa-update**&#x200B;工具自动更新过滤器规则。 有关更多信息，请参阅官方的SpamAssassin网站[http://spamassassin.apache.org/](http://spamassassin.apache.org/)。

在Debian中，每天会自动进行更新。

如果情况并非如此（例如，手动安装Debian时），请创建脚本以自动更新规则。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

使用以下命令将此脚本插入&#x200B;**crontab**:

```
crontab-e
```

### 性能优化 {#performance-optimization}

要提高Linux中的性能，请编辑&#x200B;**/etc/spamassassin/local.cf**&#x200B;文件，并在文件末尾添加以下行：

```
dns_available no
```
