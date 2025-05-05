---
product: campaign
title: Web服务器配置
description: 了解有关Web服务器配置主要最佳实践的更多信息
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Web服务器配置 {#web-server-configuration}



您将在下面找到与Web服务器(Apache/IIS)配置相关的一些主要最佳实践。

* 更改默认错误页面。

* 禁用旧的SSL版本和密码：

  **在Apache**&#x200B;上，编辑/etc/apache2/mods-available/ssl.conf。 示例如下：

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **在IIS**&#x200B;上（请参阅[文档](https://support.microsoft.com/en-us/kb/245030)），执行以下配置：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加注册表子项
   * 要使系统能够使用默认不会协商的协议（如TLS 1.2），请在&#x200B;**Protocols**&#x200B;键下的以下注册表项中将DisabledByDefault值的DWORD值数据更改为0x0：

     SCHANNEL\Protocols\TLS 1.2\客户端

     SCHANNEL\Protocols\TLS 1.2\服务器

  **禁用SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client： DisabledByDefault： DWORD （32位）值为1

  SCHANNEL\Protocols\SSL 3.0\Server：已启用： DWORD （32位）值为0

* 删除&#x200B;**TRACE**&#x200B;方法：

  **在Apache**&#x200B;上，在/etc/apache2/conf.d/security： TraceEnable **Off**&#x200B;中编辑

  **在IIS**&#x200B;上（请参阅[文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)），执行以下配置：

   * 确保已安装&#x200B;**请求筛选**&#x200B;角色服务或功能。
   * 在&#x200B;**请求筛选**&#x200B;窗格中，单击“HTTP动词”选项卡，然后单击“拒绝动词”。 在“操作”窗格中，在打开的对话框中输入TRACE。

* 删除横幅：

  **在Apache**&#x200B;上，编辑/etc/apache2/conf.d/security：

   * ServerSignature **关闭**
   * ServerTokens **产品**

  **在IIS**&#x200B;上，执行以下配置：

   * 安装&#x200B;**URLcan**。
   * 编辑&#x200B;**Urlscan.ini**&#x200B;文件以使&#x200B;**RemoveServerHeader=1**

* 限制查询大小以防止上载重要文件：

  **在Apache**&#x200B;上，在/目录中添加&#x200B;**LimitRequestBody**&#x200B;指令（以字节为单位）。

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **在IIS**（请参阅[文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)）上，在内容筛选选项中设置&#x200B;**maxAllowedContentLength**（允许的最大内容长度）。

相关主题：

* [Adobe Marketing Cloud合规性概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign安全概述](https://experienceleague.adobe.com/zh-hans/docs/experience-platform/landing/governance-privacy-security/overview#security)
