---
title: 配置SpamAssassin
seo-title: 配置SpamAssassin
description: 配置SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: edb99a13d8b2f39f991e8ceb6718291d92504242

---


# 配置SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>某些配置只能由Adobe为Adobe托管的部署执行。 例如，访问服务器和实例配置文件。 要进一步了解不同的部署，请参阅托 [管模型部分](../../installation/using/hosting-models.md) ，或 [本文](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

## 概述 {#overview}

SpamAssassin是一款用于过滤不良电子邮件的软件。 与此软件一起，Adobe Campaign可以为电子邮件分配分数，并确定在启动传送之前是否可能认为不需要发送邮件。 为此，必须在Adobe Campaign的应用程序服务器上安装和配置SpamAssassin，并需要一定数量的附加Perl模块才能运行。

本章中所述的SpamAssassin的部署和集成基于默认软件安装，过滤和评分规则也基于这些规则，这些规则由SpamAssassin提供，无需任何更改或优化。 得分归因和消息资格仅基于SpamAssassin选项的配置和过滤规则。 网络管理员负责使他们适应公司的需求。

>[!CAUTION]
>
>SpamAssassin对电子邮件的评级是完全基于过滤和评分规则。
>
>因此，必须每天至少更新这些规则一次，以便SpamAssassin安装及其与Adobe Campaign的集成能够全面发挥作用，并确保在发送之前分配给您的分发的分数的相关性。
>
>此更新由承载SpamAssassin的服务器管理员负责。

在Adobe Campaign中使用SpamAssassin可指示在收到Adobe Campaign发送的电子邮件时使用SpamAssassin的邮件服务器的可能行为。 但是，互联网提供商的邮件服务器或在线邮件服务器仍可能认为Adobe Campaign发送的邮件不受欢迎。

在Perl中部署SpamAssassin及其模块需要Adobe Campaign应用程序服务器通过HTTP连接（TCP/80流）配备Internet访问。

## 在Windows计算机上安装 {#installing-on-a-windows-machine}

要在Windows上安装和配置SpamAssassin以启用与Adobe Campaign的集成，请应用以下步骤：

1. 安装SpamAssassin
1. 将SpamAssassin集成到Adobe Campaign中

### 安装SpamAssassin {#installing-spamassassin}

1. 使用用户凭 [据连接到Extranet](http://support.neolane.net) Portal。
1. 转到下载 **中心** ，然后浏览页面以查找工 **具部分** 。
1. 下载 **Spam Assassin（Windows安装）(1.0)文件** 。
1. 将此文件复制到Adobe Campaign服务器上，然后将其解压缩。

   >[!NOTE]
   >
   >您可以选择在任意位置解压缩文件，前提是路径由以下任意正则表达式字符组成： **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. 安装路径不得包含任何空格字符。

1. 转到已解压文件的文件，然后双击 **run_me.bat文件以启动安装脚本** 。

   如果出现Windows Shell并且继续显示几秒钟，请等到安装和更新完成，然后单击 **Enter**。

   如果Windows shell在立即消失之前未出现或未显示，请执行以下步骤，双击 **portableShell.bat** 文件以显示Windows Shell，并检查Shell路径是否与解压缩了 **** spamassassin.zip文件的文件夹相对应。 如果不是这样，请使用cd命令访问 **它** 。

   输 **入run_me.bat** ，然后单 **击Enter** ，开始安装和更新过程。 该操作返回以下值之一以指示更新的结果。

   * **0**:已进行更新。
   * **1**:没有可用的新更新。
   * **2**:没有可用的新更新。
   * **3**:更新在先前验证期间失败。
   * **4** 或更多：发生错误。

1. 要检查SpamAssassin安装是否成功，请按照以下过程使用GTUBE测试（主动提供的批量电子邮件的常规测试）:

   1. 创建文本文件并将其保存在C:\TestSpamMail.txt **下**。
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

   1. 双击portableShell.bat文 **件以显示Windows Shell** ，然后启动以下命令(或“`<root>`”在解压缩spamassassin.zip文件时指定创建的 **** 文件夹):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此测试电子邮件的内容触发了SpamAssassin的1,000分得分。 这意味着已检测到它不需要，并且安装成功并且完全正常工作。

### 将SpamAssassin集成到Adobe Campaign中 {#integrating-spamassassin-into-adobe-campaign}

1. 编辑文 **`[INSTALL]/conf/serverConf.xml`** 件。 serverConf.xml中可用的所 **有参数都列在本节** 中 [](../../installation/using/the-server-configuration-file.md)。
1. 更改 **Web** 节点中 **spamCheck元素** 的command **属性的** 值。 为此，请运行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路径必须为绝对路径。

   停止并启动服 **[!UICONTROL Adobe Campaign]** 务。

1. 要检查Adobe Campaign中SpamAssassin的集成，请使用GTBUE测试（主动提供的批量电子邮件的通用测试）:

   双击portableshell. **bat文件** 。 这会触发Windows shell的显示。 然后，运行以下命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此测试电子邮件的内容会触发SpamAssassin分配的1,000点积分。 这意味着它被检测为不需要，并且Adobe Campaign中的集成已成功并且完全正常工作。

1. 更新SpamAssassin过滤和评分规则

   有关筛选和评分规则的初始更新，请启 **动portableShell.bat** ，然后运行以下命令：

   ```
   sa-update --no-gpg
   ```

   要运行筛选和评分规则的自动更新，请在计划的系统任务中使用以下相同命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux计算机上安装 {#installing-on-a-linux-machine}

### 在Debian中安装步骤 {#installation-steps-in-debian}

* 如有必要，请使用以下命令安装Perl和SpamAssassin:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* 在serverConf. **xml文件** (在中提供 `/usr/local/[INSTALL]/nl6/conf/`)中，按如下方式更改 **spamCheck** 行：

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

### 更新筛选器规则 {#updating-filter-rules}

可以使用sa-update工具自动更新 **筛选器规则** 。 有关详细信息，请参 [阅官方](http://spamassassin.apache.org/) SpamAssassin网站http://spamassassin.apache.org/。

在德比安，更新每天自动进行。

如果不是这样（例如，手动安装Debian时），请创建一个脚本以自动更新规则。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

使用以下命令 **将此脚本** 插入crontab:

```
crontab-e
```

### 性能优化 {#performance-optimization}

要提高Linux中的性能，请编辑 **/etc/spamassassin/local.cf** 文件，并在文件末尾添加以下行：

```
dns_available no
```

