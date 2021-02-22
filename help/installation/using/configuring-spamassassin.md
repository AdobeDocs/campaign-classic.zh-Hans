---
solution: Campaign Classic
product: campaign
title: 配置 SpamAssassin
description: 配置 SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 33debcd6e399d2780277644103a620d46c22022e
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 1%

---


# 配置 SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>某些配置只能由Adobe执行，以用于由Adobe托管的部署。 例如，访问服务器和实例配置文件。 要进一步了解不同的部署，请参阅[托管模型](../../installation/using/hosting-models.md)部分或[本页](../../installation/using/capability-matrix.md)。

## 概述 {#overview}

SpamAssassin是一款用于过滤不想要的电子邮件的软件。 与此软件结合使用时，Adobe Campaign可以为电子邮件分配分数，并确定在启动投放之前是否可能认为不需要发送邮件。 为此，必须在Adobe Campaign的应用程序服务器上安装并配置SpamAssassin，并需要一定数量的附加Perl模块才能运行。

本章中所述的SpamAssassin的部署和集成基于默认软件安装，过滤和评分规则也是基于这些规则的，这些规则是SpamAssassin提供的，不进行任何更改或优化。 得分归因和消息资格仅基于SpamAssassin选项的配置和过滤规则。 网络管理员负责使他们适应其公司的需要。

>[!IMPORTANT]
>
>SpamAssassin将电子邮件评为不需要的完全基于过滤和评分规则。
>
>因此，必须每天至少更新这些规则一次，以便SpamAssancis安装及其集成到Adobe Campaign中，以使其功能完全正常，并保证在发送之前分配给投放的分数的相关性。
>
>此更新由托管SpamAssassin的服务器管理员负责。

在Adobe Campaign中使用SpamAssassin可指示使用SpamAssassin的邮件服务器在收到由Adobe Campaign发送的电子邮件时的可能行为。 然而，因特网提供商或在线邮件服务器的邮件服务器可能仍然认为Adobe Campaign发送的邮件不受欢迎。

在Perl中部署SpamAssassin及其模块需要Adobe Campaign应用服务器，这些服务器配备通过HTTP连接（TCP/80流）访问Internet。

## 在Windows计算机上安装{#installing-on-a-windows-machine}

要在Windows上安装和配置SpamAssassin以启用与Adobe Campaign的集成，请应用以下步骤：

1. 安装SpamAssan
1. 将SpamAssassin集成到Adobe Campaign

### 安装SpamAssans{#installing-spamassassin}

1. 使用您的用户凭据连接到[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 了解有关[本页](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)中软件分发的更多信息。
1. 下载&#x200B;**Neolane Spam Assassin（Windows安装）(2.0)**&#x200B;文件(neolane_spamassassin.2.0.zip)。
1. 将此文件复制到Adobe Campaign服务器，然后将其解压缩。

   >[!NOTE]
   >
   >只要路径由以下任意常规表达式字符组成，您就可以选择随时解压缩文件：**`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**。 安装路径不得包含任何空格字符。

1. 转到已解压文件的文件，然后多次单击&#x200B;**run_me.bat**&#x200B;文件以启动安装脚本。

   如果出现Windows Shell并且继续显示几秒钟，请等到安装和更新完成，然后单击&#x200B;**Enter**。

   如果Windows Shell在即时消失之前未显示或未显示，请按照以下步骤操作，多次单击&#x200B;**portableShell.bat**&#x200B;文件以显示Windows Shell，并检查Shell路径是否与&#x200B;**spamassassin.zip**&#x200B;文件解压的文件夹相对应。 如果不是这样，请使用&#x200B;**cd**&#x200B;命令访问它。

   输入&#x200B;**run_me.bat**，然后单击&#x200B;**Enter**&#x200B;以开始安装和更新过程。 该操作返回以下值之一以指示更新结果。

   * **0**:已进行更新。
   * **1**:没有可用的新更新。
   * **2**:没有可用的新更新。
   * **3**:在先前验证期间更新失败。
   * **4** 或更多：发生错误。

1. 要检查SpamAssassin安装是否成功，请按照以下步骤使用GTUBE测试（主动提供的批量电子邮件的常规测试）：

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

   1. 多次单击&#x200B;**portableShell.bat**&#x200B;文件以显示Windows Shell，然后启动以下命令（或&quot;`<root>`&quot;在解压缩&#x200B;**spamassain.zip**&#x200B;文件时指定创建的文件夹）：

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此测试电子邮件的内容会触发SpamAssassin的1,000分得分。 这意味着，它被检测为不需要，安装成功且完全正常。

### 将SpamAssassin集成到Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 编辑&#x200B;**`[INSTALL]/conf/serverConf.xml`**&#x200B;文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。
1. 更改&#x200B;**Web**&#x200B;节点中&#x200B;**spamCheck**&#x200B;元素的&#x200B;**command**&#x200B;属性的值。 为此，请运行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路径必须为绝对路径。

   停止并开始&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;服务。

1. 要检查Adobe Campaign中SpamAssassin的集成，请使用GTBUE测试（未经请求的批量电子邮件的通用测试）：

   多次 — 单击&#x200B;**portableshell.bat**&#x200B;文件。 这会触发Windows Shell的显示。 然后运行以下命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此测试电子邮件的内容会触发SpamAssassin分配的1,000点。 这意味着它被认为是不可取的，Adobe Campaign的整合是成功的，并且是全功能的。

1. 更新SpamAssassin过滤和评分规则

   对于筛选和评分规则的初始更新，请开始&#x200B;**portableShell.bat**&#x200B;并运行以下命令：

   ```
   sa-update --no-gpg
   ```

   要运行过滤和评分规则的自动更新，请在计划的系统任务中使用以下相同命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux计算机{#installing-on-a-linux-machine}上安装

### Debian {#installation-steps-in-debian}中的安装步骤

* 如有必要，请使用以下命令安装Perl和SpamAssans:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* 在&#x200B;**serverConf.xml**&#x200B;文件（在`/usr/local/[INSTALL]/nl6/conf/`中可用）中，按如下方式更改&#x200B;**spamCheck**&#x200B;行：

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### RHEL/CentOS {#installation-steps-in-rhel-centos}中的安装步骤

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

### 更新筛选器规则{#updating-filter-rules}

可以使用&#x200B;**sa-update**&#x200B;工具自动更新筛选器规则。 有关详细信息，请参阅官方的SpamAssassin网站[http://spamassassin.apache.org/](http://spamassassin.apache.org/)。

在德比安，更新每天自动进行。

如果不是这样（例如，手动安装Debian时），请创建一个脚本以自动更新规则。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

使用以下命令将此脚本插入&#x200B;**crontab**:

```
crontab-e
```

### 性能优化{#performance-optimization}

要提高Linux中的性能，请编辑&#x200B;**/etc/spamassassin/local.cf**&#x200B;文件，并在文件末尾添加以下行：

```
dns_available no
```

