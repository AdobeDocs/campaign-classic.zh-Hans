---
title: 集成到Linux的Web服务器
seo-title: 集成到Linux的Web服务器
description: 集成到Linux的Web服务器
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: abddb3cdfcee9e41cab2e7e662d5bfd5d53d6f7e

---


# 集成到Linux的Web服务器{#integration-into-a-web-server-for-linux}

Adobe Campaign包含Apache Tomcat，它通过HTTP（和SOAP）充当应用程序服务器中的入口点。

您可以使用此集成的Tomcat服务器来提供HTTP请求。

在这种情况下：

* 默认监听端口为8080。 要更改它，请参阅配 [置Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat)。
* 然后，客户端控制台使用URL进行连接，如：

   ```
   http://<computer>:8080
   ```

但是，出于安全和管理原因，当运行Adobe Campaign的计算机在Internet上公开并且您希望打开对网络外控制台的访问时，我们建议使用专用Web服务器作为HTTP通信的主要入口点。

Web服务器还允许您使用HTTP协议保证数据的机密性。

同样，当您希望使用跟踪功能时，必须使用Web服务器，该功能仅作为Web服务器的扩展模块可用。

>[!NOTE]
>
>如果不使用跟踪功能，则可以通过重定向到Campaign来执行Apache或IIS的标准安装。 无需跟踪Web服务器扩展模块。

## 使用Debian配置Apache web服务器 {#configuring-the-apache-web-server-with-debian}

如果您在基于APT的分发下安装了Apache，则此过程适用。

应用以下步骤：

1. 使用以下命令禁用默认加载的模块：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   确保 **别名**、authz_host **** 和mime **** 模块仍处于启用状态。 为此，请使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 在 **/etc/apache2/mods-available中创建文件nlsrv.load** ，并插入以下内容 **** :

   在德边7号：

   ```
   LoadModule requesthandler22_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

   在德边8中：

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 使用以 **下命令在** /etc/apache2/mods-available中创建文件 **** nlsrv.conf:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模块：

   ```
    a2enmod nlsrv
   ```

   如果您使用Adobe Campaign页的 **mod_rewrite** 模块，则需要将 **nlsrv.** 和 **nlsrv.conf文件重命名为********** lsrv.nlsrv.nzz和jzz-lsrv.conf文件重命名为jlsrv.nlsrv.load.conf。 要激活模块，请运行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 编辑 **/etc/apache2/envvars文件** ，添加以下行：

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

## 在RHEL中配置Apache web服务器 {#configuring-apache-web-server-in-rhel}

如果您在基于RPM（RHEL、CentOS和Suse）的包下安装并保护了Apache，则此过程适用。

应用以下步骤：

1. 在文件 `httpd.conf` 中，激活以下Apache模块：

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

对链接到取消激活模块的函数进行注释：

    &quot;
    
    
    
    
    
    
    
    
    
    
    DirectoryIndexIndexIndexOptionsAddIconByEncodingAddIconByTypeAddIconDefaultIconReadmeNameHeaderNameIndexIndexIgnoreLanguagePriorityForceLanguagePriority
    &quot;

1. 在文件夹中创建特定于Adobe Campaign的配置 `/etc/httpd/conf.d/` 文件。

例如 `CampaignApache.conf`。

1. 对 **于RHEL6**，在文件中添加以下说明：

   ```
   LoadModule requesthandler22_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

对 **于RHEL7**，在文件中添加以下说明：

LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.soInclude /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf

1. 对于 **RHEL6**:

在文件中添加以下说 `/etc/sysconfig/httpd` 明：

    &quot;
    #Neolane/Adobe Campaign
    Configurationif [ &quot;$LD_LIBRARY_PATH&quot; != &quot;&quot; ];然后导出LD_LIBRARY_PATH=&quot;/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH&quot;;else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib;
    fiexport USERPATH=/usr/local/neolane
    &quot;

对于 **RHEL7**:

添加包 `/etc/systemd/system/httpd.service` 含以下内容的文件：

    &quot;
    包括/usr/lib/systemd/system/httpd.service
    
    [服务]
    Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
    &quot;

更新系统使用的模块：

    &quot;
    systemctl daemon-reload
    &quot;

1. 然后，通过运行以下命令，将Adobe Campaign操作符添加到Apache操作符组中，反之亦然：

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```
要使用的组名称取决于Apache的配置方式。

1. 运行Apache和Adobe Campaign服务器。

对于RHEL6:

    &quot;
    /etc/init.d/httpd start
    /etc/init.d/nlserver start
    &quot;

对于RHEL7:

    &quot;
    systemctl启动
    httpdsystemctl启动nlserver
    &quot;

## 启动Web服务器并测试配置{#launching-the-web-server-and-testing-the-configuration}

您现在可以通过启动Apache来测试配置。 Adobe Campaign模块现在应在控制台上显示其横幅（某些操作系统上有两个横幅）:

```
 /etc/init.d/apache start
```

此时将显示以下信息：

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下来检查它是否通过提交测试URL做出响应。

您可以通过执行以下操作，从命令行测试：

```
 telnet localhost 80  
```

您应当获得：

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
````

然后输入：

```
GET /r/test
````

此时将显示以下信息：

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
````

您还可以从Web浏览器 [`http://<computer>`](http://machine/r/test) 请求该URL。