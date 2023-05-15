---
product: campaign
title: Web服务器配置
description: 了解有关Web服务器配置的主要最佳实践的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Web服务器配置 {#web-server-configuration}



下面列出了一些与Web服务器(Apache/IIS)配置相关的主要最佳实践。

* 更改默认错误页面。

* 禁用旧SSL版本和密码：

   **在Apache上**，编辑/etc/apache2/mods-available/ssl.conf。 示例如下：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS上** (请参阅 [文档](https://support.microsoft.com/en-us/kb/245030))，请执行以下配置：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加注册表子项
   * 要使系统能够使用默认不会协商的协议（如TLS 1.2），请在 **协议** 键：

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **禁用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\客户端：DisabledByDefault:DWORD（32位）值为1

   SCHANNEL\Protocols\SSL 3.0\Server:已启用：DWORD（32位）值为0

* 删除 **TRACE** 方法：

   **在Apache上**，在/etc/apache2/conf.d/security中编辑：TraceEnable **关闭**

   **在IIS上** (请参阅 [文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，请执行以下配置：

   * 确保 **请求筛选** 角色服务或功能已安装。
   * 在 **请求筛选** 窗格中，单击“HTTP动词”选项卡，然后单击“拒绝动词”。 在“操作”窗格中，在打开的对话框中输入TRACE。

* 删除横幅：

   **在Apache上**，编辑/etc/apache2/conf.d/安全：

   * ServerSignature **关闭**
   * ServerTokens **生产**

   **在IIS上**，请执行以下配置：

   * 安装 **URLcan**.
   * 编辑 **Urlscan.ini** 文件 **RemoveServerHeader=1**


* 限制查询大小以阻止上载重要文件：

   **在Apache上**，添加 **LimitRequestBody** /目录中的指令(大小（以字节为单位）。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS上** (请参阅 [文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))，请设置 **maxAllowedContentLength** （允许的最大内容长度）。

相关主题：

* [Adobe Marketing Cloud合规性概述](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全概述](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)
