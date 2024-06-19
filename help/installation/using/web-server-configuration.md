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

  **在Apache上**，编辑/etc/apache2/mods-available/ssl.conf。 示例如下：

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **在IIS上** (请参阅 [文档](https://support.microsoft.com/en-us/kb/245030))，执行以下配置：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加注册表子项
   * 要使系统能够使用默认不会协商的协议（如TLS 1.2），请将DisabledByDefault值的DWORD值数据更改为0x0，在 **协议** 键：

     SCHANNEL\Protocols\TLS 1.2\客户端

     SCHANNEL\Protocols\TLS 1.2\服务器

  **禁用SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client： DisabledByDefault： DWORD （32位）值为1

  SCHANNEL\Protocols\SSL 3.0\Server：已启用： DWORD （32位）值为0

* 删除 **TRACE** 方法：

  **在Apache上**，在/etc/apache2/conf.d/security中编辑： TraceEnable **关闭**

  **在IIS上** (请参阅 [文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，执行以下配置：

   * 确保 **请求筛选** 角色服务或功能已安装。
   * 在 **请求筛选** 窗格，单击HTTP动词选项卡，然后单击拒绝动词。 在“操作”窗格中，在打开的对话框中输入TRACE。

* 删除横幅：

  **在Apache上**，编辑/etc/apache2/conf.d/security：

   * 服务器签名 **关闭**
   * ServerTokens **Prod**

  **在IIS上**，执行以下配置：

   * 安装 **URLcan**.
   * 编辑 **Urlscan.ini** 要具有的文件 **RemoveServerHeader=1**

* 限制查询大小以防止上载重要文件：

  **在Apache上**，添加 **LimitRequestBody** /目录中的指令（以字节为单位的大小）。

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **在IIS上** (请参阅 [文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))，设置 **maxAllowedContentLength** （允许的最大内容长度）。

相关主题：

* [Adobe Marketing Cloud合规性概述](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign安全概述](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)
