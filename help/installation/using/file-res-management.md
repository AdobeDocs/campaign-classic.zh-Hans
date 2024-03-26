---
product: campaign
title: 文件和资源管理
feature: Installation, Application Settings
description: 了解如何在Campaign中配置文件和资源管理
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 2%

---

# 文件和资源管理{#file-and-resmanagement}



## 限制上载文件格式 {#limiting-uploadable-files}

使用 **uploadWhiteList** 属性，用于限制可在Adobe Campaign服务器上上传的文件类型。

此属性可在 **数据存储** 元素 **serverConf.xml** 文件。 中所有可用的参数，请参见 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).

此属性的默认值为 **.+** 并允许您上传任何文件类型。

要限制可能的格式，请使用有效的Java正则表达式替换属性值。 您可以输入多个值，方法是以逗号分隔。

例如： **uploadWhiteList=”。&#42;.png，.&#42;.jpg”** 允许您在服务器上上传PNG和JPG格式。 将不接受任何其他格式。

您还可以通过配置Web服务器来阻止上载重要文件。 [了解详情](web-server-configuration.md)

>[!NOTE]
>
>此 **uploadWhiteList** 属性限制可在Adobe Campaign服务器上上传的文件类型。 但是，当发布模式为 **跟踪服务器** 或 **其他Adobe Campaign服务器**， **uploadWhitelist** 属性也必须在这些服务器上更新。

## 代理连接配置 {#proxy-connection-configuration}

您可以通过代理，使用将Campaign服务器连接到外部系统 **文件传输** 例如，工作流活动。 要实现此目的，您需要配置 **proxyConfig** 的部分 **serverConf.xml** 通过特定命令执行文件。 所有参数均可在 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).

可以使用以下代理连接： HTTP、HTTPS、FTP、SFTP。 请注意，从20.2 Campaign版本开始，HTTP和HTTPS协议参数为 **不再可用**. 由于这些参数在以前的版本（包括9032）中仍然可用，因此下文将对这些参数进行介绍。

>[!CAUTION]
>
>仅支持基本身份验证模式。 不支持NTLM身份验证。
>
>不支持SOCKS代理。
>

可以使用以下命令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

协议参数可以是“http”、“https”或“ftp”。

如果您在与HTTP/HTTPS流量相同的端口上设置FTP，则可以使用以下命令：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

“http”和“https”选项仅在protocol参数为“ftp”并指示指定端口上的隧道是通过HTTPS还是通过HTTP执行的。

如果对通过代理服务器传输的FTP/SFTP和HTTP/HTTPS流量使用不同的端口，则应设置“ftp”协议参数。


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

如果对多种连接类型使用相同的代理，则仅在useSingleProxy设置为“1”或“true”的情况下定义proxyHTTP。

如果您有不应通过代理的内部连接，请将它们添加到覆盖参数中。

如果要临时禁用代理连接，请将enabled参数设置为“false”或“0”。

如果您需要通过代理使用iOS HTTP/2连接器，则支持以下HTTP代理模式：

* 不带身份验证的HTTP
* HTTP基本身份验证

要激活代理模式，必须在 `serverconf.xml` 文件：

```
<nmac useHTTPProxy="true">
```

有关此iOS HTTP/2连接器的更多信息，请参阅此 [页面](../../delivery/using/about-mobile-app-channel.md).

## 管理公共资源 {#managing-public-resources}

要公开发布，链接到营销策划的电子邮件和公共资源中使用的图像必须存在于外部可访问的服务器上。 然后，外部收件人或操作员可以使用它们。 [了解详情](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公共资源存储在 **/var/res/instance** Adobe Campaign安装目录的目录。

匹配的URL为： **http://server/res/instance** 位置 **实例** 是跟踪实例的名称。

通过将节点添加到 **会议 — `<instance>`.xml** 文件以配置服务器上的存储。 这意味着添加以下行：

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

在这种情况下，部署向导窗口上部给定的公共资源的新URL应指向此文件夹。
