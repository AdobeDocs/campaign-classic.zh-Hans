---
product: campaign
title: 文件和资源管理
feature: Installation, Application Settings
description: 了解如何在Campaign中配置文件和资源管理
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# 文件和资源管理{#file-and-resmanagement}



## 限制上载文件格式 {#limiting-uploadable-files}

使用&#x200B;**uploadWhiteList**&#x200B;属性限制可在Adobe Campaign服务器上上传的文件类型。

此属性在&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**dataStore**&#x200B;元素中可用。 **serverConf.xml**&#x200B;中的所有可用参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

此属性的默认值为&#x200B;**。+**&#x200B;并允许您上传任何文件类型。

要限制可能的格式，请使用有效的Java正则表达式替换属性值。 您可以输入多个值，方法是以逗号分隔。

例如：**uploadWhiteList=&quot;。&#42;.png，。&#42;.jpg“**”将允许您在服务器上传PNG和JPG格式。 将不接受任何其他格式。

您还可以通过配置Web服务器来阻止上载重要文件。 [了解详情](web-server-configuration.md)

>[!NOTE]
>
>**uploadWhiteList**&#x200B;属性限制Adobe Campaign服务器上可上传的文件类型。 但是，当发布模式为&#x200B;**跟踪服务器**&#x200B;或&#x200B;**其他Adobe Campaign服务器**&#x200B;时，还必须在这些服务器上更新&#x200B;**uploadWhitelist**&#x200B;属性。

## 代理连接配置 {#proxy-connection-configuration}

您可以通过代理将Campaign服务器连接到外部系统，例如，使用&#x200B;**文件传输**&#x200B;工作流活动。 要实现此目的，您需要通过特定命令配置&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**proxyConfig**&#x200B;节。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

可以使用以下代理连接： HTTP、HTTPS、FTP、SFTP。 请注意，从20.2 Campaign版本开始，HTTP和HTTPS协议参数&#x200B;**不再可用**。 由于这些参数在以前的版本（包括9032）中仍然可用，因此下文将对这些参数进行介绍。

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

要激活代理模式，必须在`serverconf.xml`文件中完成以下更改：

```
<nmac useHTTPProxy="true">
```

有关此iOS HTTP/2连接器的更多信息，请参阅此[页面](../../delivery/using/about-mobile-app-channel.md)。

## 管理公共资源 {#managing-public-resources}

要公开发布，链接到营销策划的电子邮件和公共资源中使用的图像必须存在于外部可访问的服务器上。 然后，外部收件人或操作员可以使用它们。 [了解详情](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公共资源存储在Adobe Campaign安装目录的&#x200B;**/var/res/instance**&#x200B;目录中。

匹配的URL是： **http://server/res/instance**，其中&#x200B;**实例**&#x200B;是跟踪实例的名称。

通过将节点添加到&#x200B;**conf-`<instance>`.xml**&#x200B;文件以配置服务器上的存储，可以指定另一个目录。 这意味着添加以下行：

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
