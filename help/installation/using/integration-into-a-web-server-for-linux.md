---
product: campaign
title: 集成到Linux版Web服务器
description: 了解如何将Campaign集成到Web服务器(Linux)
feature: Installation, Instance Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 2%

---

# 集成到Linux版Web服务器 {#integration-into-a-web-server-for-linux}


Adobe Campaign包括Apache Tomcat，后者通过HTTP(和SOAP)充当应用程序服务器中的入口点。

您可以使用此集成的Tomcat服务器来处理HTTP请求。

在本例中：

* 默认侦听端口为8080。 要更改它，请参阅[此部分](configure-tomcat.md)。
* 然后，客户端控制台使用URL进行连接，例如：

  ```
  https://<computer>:8080
  ```

但是，出于安全和管理原因，当运行Adobe Campaign的计算机在Internet上公开并且您希望打开访问网络外部的控制台时，我们建议使用专用的Web服务器作为HTTP流量的主要入口点。

Web服务器还允许您通过HTTPs协议保证数据机密性。

同样，当您希望使用跟踪功能时，必须使用Web服务器，该功能只能作为Web服务器的扩展模块使用。

>[!NOTE]
>
>如果不使用跟踪功能，则可以执行Apache或IIS的标准安装，并重定向到Campaign。 不需要跟踪Web服务器扩展模块。

## 使用Debian配置Apache Web Server {#configuring-the-apache-web-server-with-debian}

如果您在基于APT的分发下安装了Apache，则此流程适用。

应用以下步骤：

1. 使用以下命令禁用默认加载的模块：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   确保仍然启用&#x200B;**别名**、**authz_host**&#x200B;和&#x200B;**mime**&#x200B;模块。 为此，请使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 在&#x200B;**/etc/apache2/mods-available**&#x200B;中创建文件&#x200B;**nlsrv.load**&#x200B;并插入以下内容：

   在Debian 8中：

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 使用以下命令在&#x200B;**/etc/apache2/mods-available**&#x200B;中创建文件&#x200B;**nlsrv.conf**：

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模块：

   ```
    a2enmod nlsrv
   ```

   如果您对Adobe Campaign页面使用&#x200B;**mod_rewrite**&#x200B;模块，则需要将&#x200B;**nlsrv.load**&#x200B;和&#x200B;**nlsrv.conf**&#x200B;文件重命名为&#x200B;**zz-nlsrv.load**&#x200B;和&#x200B;**zz-nlsrv.conf**。 要激活此模块，请运行以下命令：

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

1. 然后使用以下类型的命令将Adobe Campaign用户添加到Apache用户组，反之亦然：

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. 重新启动Apache：

   ```
   invoke-rc.d apache2 restart
   ```

## 在RHEL中配置Apache Web Server {#configuring-apache-web-server-in-rhel}

如果您在基于RPM （RHEL、CentOS和Suse）的软件包下安装并保护了Apache，则此过程适用。

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

1. 对于&#x200B;**RHEL7**，请在文件中添加以下说明：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 对于&#x200B;**RHEL7**：

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

1. 然后通过运行以下命令，将Adobe Campaign运算符添加到Apache运算符组中（反之亦然）：

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   要使用的组名取决于Apache的配置方式。

1. 运行Apache和Adobe Campaign Server。

   对于RHEL7：

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 启动Web服务器并测试配置{#launching-the-web-server-and-testing-the-configuration}

您现在可以通过启动Apache测试配置。 Adobe Campaign模块现在应在控制台上显示其横幅（某些操作系统上有两个横幅）：

```
 /etc/init.d/apache start
```

将显示以下信息：

```sql
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下来，检查它是否通过提交测试URL做出响应。

您可以通过执行以下操作从命令行对此进行测试：

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

您还可以从Web浏览器请求URL `https://myserver.adobe.com/r/test`。
