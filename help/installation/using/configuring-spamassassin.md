---
product: campaign
title: 配置SpamAssassin
description: 配置SpamAssassin
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 1%

---

# 配置SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>对于由Adobe托管的部署，某些配置只能由Adobe执行。 例如，访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 区域或至 [此页面](../../installation/using/capability-matrix.md).

## 概述 {#overview}

SpamAssassin是一款旨在过滤不想要的电子邮件的软件。 结合此软件，Adobe Campaign可以为电子邮件分配一个分数，并在启动投放之前确定消息是否可能被视为不需要。 为此，必须在Adobe Campaign的应用程序服务器上安装和配置SpamAssassin，并且运行另外一定数量的Perl模块。

本章所述的SpamAssassin部署和集成基于默认软件安装，以及过滤和评分规则，这些规则由SpamAssassin提供，没有任何更改或优化。 得分归因和消息资格认证完全基于SpamAssassin选项的配置和过滤规则。 网络管理员负责根据公司的需要调整其设置。

>[!IMPORTANT]
>
>SpamAssassin将电子邮件认定为不受欢迎，完全基于筛选和评分规则。
>
>因此，这些规则必须每天至少更新一次，以便SpamAssassin安装及其与Adobe Campaign的集成能够完全正常运行，并确保在发送之前分配给投放的分数的相关性。
>
>此更新由托管SpamAssassin的服务器管理员负责。

在Adobe Campaign中使用SpamAssassin可指示使用SpamAssassin的邮件服务器在收到Adobe Campaign发送的电子邮件时可能采取的行为。 但是，互联网提供商或在线邮件服务器的邮件服务器可能仍然认为Adobe Campaign发送的消息不可取。

在Perl中部署SpamAssassin及其模块时，需要Adobe Campaign应用程序服务器配备通过HTTP连接（TCP/80流）访问Internet。

## 在Windows计算机上安装 {#installing-on-a-windows-machine}

要在Windows上安装和配置SpamAssassin以启用与Adobe Campaign的集成，请应用以下步骤：

1. 安装SpamAssassin
1. 将SpamAssassin集成到Adobe Campaign

### 安装SpamAssassin {#installing-spamassassin}

1. 连接到 [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 使用您的用户凭据。 在中了解有关软件分发的更多信息 [此页面](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans).
1. 下载 **Neolane Spam Assassin（Windows安装） (2.0)** 文件(neolane_spamassassin.2.0.zip)。
1. 将此文件复制到Adobe Campaign服务器，然后解压缩。

   >[!NOTE]
   >
   >只要路径由以下任意正则表达式字符组成，您就可以选择在任何地方解压缩文件： **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. 安装路径不得包含任何空白字符。

1. 转到解压文件的文件，然后双击 **run_me.bat** 文件启动安装脚本。

   如果出现Windows Shell并继续显示几秒钟，请等待安装和更新完成，然后单击 **输入**.

   如果Windows Shell在立即消失之前未出现或未显示，请按照以下步骤操作，双击 **portableShell.bat** 文件来显示Windows Shell，并检查Shell路径是否与 **spamassassin.zip** 文件已解压缩。 如果不是这种情况，请使用 **cd** 命令。

   输入 **run_me.bat** 然后单击 **输入** 以开始安装和更新过程。 该操作将返回以下值之一，以指示更新结果。

   * **0**：已执行更新。
   * **1**：没有可用的新更新。
   * **2**：没有可用的新更新。
   * **3**：在之前验证期间更新失败。
   * **4** 或更多：发生错误。

1. 要检查SpamAssassin安装是否成功，请使用以下步骤使用GTUBE测试（针对未经请求的批量电子邮件的常规测试）：

   1. 创建文本文件，并将其保存在 **C:\TestSpamMail.txt**.
   1. 将以下内容插入文件：

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

   1. 双击 **portableShell.bat** 文件以显示Windows Shell，然后启动以下命令(或&#39;&#39;`<root>`”在解压缩  **spamassassin.zip** 文件)：

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此测试电子邮件的内容在SpamAssassin中触发1,000分的得分。 这意味着它被检测到为不需要，并且安装成功且完全正常工作。

### 将SpamAssassin集成到Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 编辑 **`[INSTALL]/conf/serverConf.xml`** 文件。 中所有可用的参数，请参见 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).
1. 更改 **spamCheck** 元素 **命令** 中的属性 **Web** 节点。 为此，请运行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路径都必须是绝对路径。

   停止并启动 **[!UICONTROL Adobe Campaign]** 服务。

1. 要检查SpamAssassin在Adobe Campaign中的集成，请使用GTBUE测试（对未经请求的批量电子邮件的常规测试）：

   双击 **portableshell.bat** 文件。 这会触发Windows Shell的显示。 然后运行以下命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此测试电子邮件的内容会触发SpamAssassin分配的1,000点。 这意味着该功能已被检测到不理想，并且Adobe Campaign中的集成已成功运行并充分发挥功能。

1. 更新SpamAssassin过滤和评分规则

   要初始更新筛选和评分规则，请开始 **portableShell.bat** 并运行以下命令：

   ```
   sa-update --no-gpg
   ```

   要运行过滤和评分规则的自动更新，请在计划系统任务中使用此相同的命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux计算机上安装 {#installing-on-a-linux-machine}

### Debian中的安装步骤 {#installation-steps-in-debian}

* 如有必要，使用以下命令安装Perl和SpamAssassin：

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* 在 **serverConf.xml** 文件(可在 `/usr/local/[INSTALL]/nl6/conf/`)，更改 **spamCheck** 行如下所示：

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

### 更新筛选规则 {#updating-filter-rules}

过滤器规则可以使用自动更新 **sa-update** 工具。 请参阅官方的SpamAssassin网站 [https://spamassassin.apache.org/](https://spamassassin.apache.org/) 以了解更多信息。

在Debian中，每天都会自动进行更新。

如果不是这种情况（例如手动安装Debian时），请创建脚本以自动更新规则。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

将此脚本插入到 **crontab** 使用以下命令：

```
crontab-e
```

### 性能优化 {#performance-optimization}

要提高Linux的性能，请编辑 **/etc/spamassassin/local.cf** 并在文件末尾添加以下行：

```
dns_available no
```
