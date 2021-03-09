---
solution: Campaign Classic
product: campaign
title: Web服务器配置
description: 了解有关Web服务器配置的主要最佳实践的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Web服务器配置{#web-server-configuration}

您将在下面找到与Web服务器(Apache/IIS)配置相关的一些主要最佳实践。

* 更改默认错误页。

* 禁用旧SSL版本和密码：

   **在Apache上**，编辑/etc/apache2/mods-available/ssl.conf。以下是一个示例：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS上** (请参阅 [文档](https://support.microsoft.com/en-us/kb/245030))，执行以下配置：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加注册表子项
   * 要使系统能够使用默认情况下不会协商的协议（如TLS 1.2），请在&#x200B;**Protocols**&#x200B;键下的以下注册表项中将DisabledByDefault值的DWORD值数据更改为0x0:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **禁用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client:DisabledByDefault:DWORD（32位）值为1

   SCHANNEL\Protocols\SSL 3.0\Server:已启用：DWORD（32位）值为0

* 删除&#x200B;**TRACE**&#x200B;方法：

   **在Apache上**，在/etc/apache2/conf.d/security中编辑：跟踪启用 **关闭**

   **在IIS上** (请参阅 [文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，执行以下配置：

   * 确保已安装&#x200B;**请求筛选**&#x200B;角色服务或功能。
   * 在&#x200B;**请求过滤**&#x200B;窗格中，单击HTTP动词选项卡，然后单击拒绝动词。 在“操作”窗格中，在“打开”对话框中输入TRACE。

* 删除横幅：

   **在Apache上**，编辑/etc/apache2/conf.d/安全性：

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **在IIS上** (请参阅 [文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，执行以下配置：

   * 安装&#x200B;**URLScan**。
   * 编辑&#x200B;**Urlscan.ini**&#x200B;文件，使其具有&#x200B;**RemoveServerHeader=1**


* 限制查询大小以阻止上传重要文件：

   **在Apache** (请参 [阅文档](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody))上，将LimitRequestBody指令(以字 **** 节为单位)添加到/目录中。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS** (请参 [阅文档](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))上，在内容筛选选 **项中设置maxAllowedContentLength** （最大允许的内容长度）。

相关主题：

* [Adobe Marketing Cloud规范概述](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全性](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) 概述(PDF)
