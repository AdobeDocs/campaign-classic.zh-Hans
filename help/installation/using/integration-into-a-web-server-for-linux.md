---
solution: Campaign Classic
product: campaign
title: 集成到 Linux 版的 Web 服务器
description: 了解如何将活动集成到Web服务器(Linux)
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---

# 集成到 Linux 版的 Web 服务器{#integration-into-a-web-server-for-linux}

Adobe Campaign包括Apache Tomcat，它通过HTTP（和SOAP）作为应用程序服务器中的入口点。

您可以使用此集成的Tomcat服务器来提供HTTP请求。

在这种情况下：

* 默认监听端口为8080。 要更改它，请参阅[此部分](configure-tomcat.md)。
* 然后，客户端控制台使用URL进行连接，例如：

   ```
   http://<computer>:8080
   ```

但是，出于安全和管理原因，当运行Adobe Campaign的计算机在Internet上公开并且您希望打开对网络外部控制台的访问时，我们建议使用专用Web服务器作为HTTP通信的主入口点。

Web服务器还允许您使用HTTPs协议保证数据的机密性。

同样，当您希望使用跟踪功能时，必须使用Web服务器，该功能仅作为Web服务器的扩展模块提供。

>[!NOTE]
>
>如果您不使用跟踪功能，则可以通过重定向到活动来执行Apache或IIS的标准安装。 不需要跟踪Web服务器扩展模块。

## 使用Debian {#configuring-the-apache-web-server-with-debian}配置Apache Web服务器

如果您已在基于APT的分发下安装Apache，则此过程适用。

应用以下步骤：

1. 使用以下命令禁用默认加载的模块：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   确保&#x200B;**alias**、**authz_host**&#x200B;和&#x200B;**mime**&#x200B;模块仍处于启用状态。 为此，请使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 在&#x200B;**/etc/apache2/mods-available**&#x200B;中创建文件&#x200B;**nlsrv.load**&#x200B;并插入以下内容：

   在德比8中：

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 使用以下命令在&#x200B;**/etc/apache2/mods-available**&#x200B;中创建文件&#x200B;**nlsrv.conf**:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模块：

   ```
    a2enmod nlsrv
   ```

   如果对Adobe Campaign页使用&#x200B;**mod_rewrite**&#x200B;模块，则需要将&#x200B;**nlsrv.load**&#x200B;和&#x200B;**nlsrv.conf**&#x200B;文件重命名为&#x200B;**zz-nlsrv.load**&#x200B;和&#x200B;**zz-nlsrv.a9/>。**&#x200B;要激活模块，请运行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 编辑&#x200B;**/etc/apache2/envvars**&#x200B;文件，添加以下行：

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   保存更改。

1. 然后，使用以下类型的命令将Adobe Campaign用户添加到Apache用户组，反之亦然：

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. 重新启动Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## 在RHEL {#configuring-apache-web-server-in-rhel}中配置Apache Web服务器

如果您已在基于RPM（RHEL、CentOS和Suse）的包下安装并保护Apache，则此过程适用。

应用以下步骤：

1. 在`httpd.conf`文件中，激活以下Apache模块：

   ```
   alias
   authz_host
   mime
   ```

1. 取消激活以下模块：

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   注释链接到已停用模块的函数：

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. 在`/etc/httpd/conf.d/`文件夹中创建特定于Adobe Campaign的配置文件。 例如`CampaignApache.conf`

1. 对于&#x200B;**RHEL7**，在文件中添加以下说明：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 对于&#x200B;**RHEL7**:

   添加包含以下内容的`/etc/systemd/system/httpd.service`文件：

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   更新系统使用的模块：

   ```
   systemctl daemon-reload
   ```

1. 然后，通过运行以下命令将Adobe Campaign运算符添加到Apache运算符组中，反之亦然：

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   要使用的组名称取决于Apache的配置方式。

1. 运行Apache和Adobe Campaign服务器。

   对于RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 启动Web服务器并测试配置{#launching-the-web-server-and-testing-the-configuration}

您现在可以通过启动Apache来测试配置。 Adobe Campaign模块现在应在控制台上显示其横幅（某些操作系统上有两个横幅）：

```
 /etc/init.d/apache start
```

将显示以下信息：

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下来检查它是否通过提交测试URL做出响应。

您可以通过执行以下操作，从命令行测试此功能：

```
 telnet localhost 80  
```

您应获得：

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

然后输入：

```
GET /r/test
```

将显示以下信息：

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

您还可以从Web浏览器请求URL [`https://<computer>`](https://myserver.adobe.com/r/test)。
