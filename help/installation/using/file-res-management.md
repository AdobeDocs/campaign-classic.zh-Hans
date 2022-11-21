---
product: campaign
title: 文件和资源管理
description: 了解如何在Campaign中配置文件和资源管理
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# 文件和资源管理{#file-and-resmanagement}

![](../../assets/v7-only.svg)

## 限制上载文件格式 {#limiting-uploadable-files}

使用 **uploadWhiteList** 属性来限制可在Adobe Campaign服务器上上传的文件类型。

此属性在 **dataStore** 元素 **serverConf.xml** 文件。 中所有可用的参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).

此属性的默认值为 **.+** 和允许您上传任何文件类型。

要限制可能的格式，请使用有效的java正则表达式替换属性值。 您可以输入多个值，方法是用逗号分隔它们。

例如： **uploadWhiteList=”。&#42;.png，.&#42;.jpg&quot;** 将允许您在服务器上上传PNG和JPG格式。 不接受其他格式。

您还可以通过配置Web服务器来阻止上传重要文件。 [了解详情](web-server-configuration.md)

>[!NOTE]
>
>的 **uploadWhiteList** 属性会限制可在Adobe Campaign服务器上上传的文件类型。 但是，当发布模式为 **跟踪服务器** 或 **其他Adobe Campaign服务器**, **uploadWhitelist** 属性也必须在这些服务器上更新。

## 代理连接配置 {#proxy-connection-configuration}

您可以使用 **文件传输** 例如，工作流活动。 要实现此目的，您需要配置 **proxyConfig** 部分 **serverConf.xml** 文件。 中可用的所有参数 **serverConf.xml** 此 [部分](../../installation/using/the-server-configuration-file.md).

可以使用以下代理连接：HTTP、HTTPS、FTP、SFTP。 请注意，从20.2 Campaign版本开始，HTTP和HTTPS协议参数为 **不再可用**. 由于这些参数在以前的版本（包括9032）中仍然可用，因此下面仍提到这些参数。

>[!CAUTION]
>
>仅支持基本身份验证模式。 不支持NTLM身份验证。
>
>不支持SOCKS代理。

您可以使用以下命令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

协议参数可以是“http”、“https”或“ftp”。

如果您将FTP设置为与HTTP/HTTPS流量相同的端口，则可以使用以下方法：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

仅当协议参数为“ftp”时，才使用“http”和“https”选项，并指示指定端口上的隧道操作是通过HTTPS还是通过HTTP执行。

如果您通过代理服务器对FTP/SFTP和HTTP/HTTPS流量使用不同的端口，则应设置“ftp”协议参数。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然后输入密码。

HTTP连接在proxyHTTP参数中定义：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS连接在proxyHTTPS参数中定义：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS连接在proxyFTP参数中定义：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果对多种连接类型使用相同的代理，则仅在将useSingleProxy设置为“1”或“true”时定义proxyHTTP。

如果您的内部连接应通过代理，请将其添加到覆盖参数中。

如果要临时禁用代理连接，请将enabled参数设置为“false”或“0”。

如果需要通过代理使用iOS HTTP/2连接器，则支持以下HTTP代理模式：

* 未经身份验证的HTTP
* HTTP基本身份验证

要激活代理模式，必须在 `serverconf.xml` 文件：

```
<nmac useHTTPProxy="true">
```

有关此iOS HTTP/2连接器的更多信息，请参阅此 [页面](../../delivery/using/about-mobile-app-channel.md).

## 管理公共资源 {#managing-public-resources}

要公开提供，链接到营销活动的电子邮件和公共资源中使用的图像必须显示在可外部访问的服务器上。 然后，外部收件人或操作员可使用这些值。 [了解详情](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公共资源存储在 **/var/res/instance** Adobe Campaign安装目录的目录。

匹配的URL是： **http://server/res/instance** where **实例** 是跟踪实例的名称。

您可以通过向 **conf-`<instance>`.xml** 文件来配置服务器上的存储。 这意味着添加以下行：

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

在这种情况下，部署向导窗口上半部分中给定的公共资源的新URL应指向此文件夹。
