---
product: campaign
title: Web服务器配置
description: 了解有关Web服务器配置的主要最佳实践的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Web服务器配置 {#web-server-configuration}

![](../../assets/v7-only.svg)

下面列出了一些与Web服务器(Apache/IIS)配置相关的主要最佳实践。

* 更改默认错误页面。

* 禁用旧SSL版本和密码：

   **在Apache上**，编辑/etc/apache2/mods-available/ssl.conf。示例如下：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS上** (请参阅 [此文档](https://support.microsoft.com/en-us/kb/245030))，执行以下配置：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加注册表子项
   * 要使系统能够使用默认不会协商的协议（如TLS 1.2），请在&#x200B;**Protocols**&#x200B;键下的以下注册表项中，将DisabledByDefault值的DWORD值数据更改为0x0:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **禁用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client网站：DisabledByDefault:DWORD（32位）值为1

   SCHANNEL\Protocols\SSL 3.0\Server网站：已启用：DWORD（32位）值为0

* 删除&#x200B;**TRACE**&#x200B;方法：

   **在Apache上**，在/etc/apache2/conf.d/security中编辑：TraceEnable  **Off**

   **在IIS上** (请参阅 [此文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，执行以下配置：

   * 确保安装了&#x200B;**请求筛选**&#x200B;角色服务或功能。
   * 在&#x200B;**请求过滤**&#x200B;窗格中，单击HTTP动词选项卡，然后单击拒绝谓词。 在“操作”窗格中，在打开的对话框中输入TRACE。

* 删除横幅：

   **在Apache上**，编辑/etc/apache2/conf.d/security:

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **在IIS上**，执行以下配置：

   * 安装&#x200B;**URLScan**。
   * 编辑&#x200B;**Urlscan.ini**&#x200B;文件，使其具有&#x200B;**RemoveServerHeader=1**


* 限制查询大小以阻止上载重要文件：

   **在Apache上**，将LimitRequestBodydirective( **** 大小（以字节为单位）)添加到/目录中。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS** (请参阅 [此文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))上，在内容过滤 **选项中设置maxAllowedContentLength** （允许的最大内容长度）。

相关主题：

* [Adobe Marketing Cloud合规性概述](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全概述](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
