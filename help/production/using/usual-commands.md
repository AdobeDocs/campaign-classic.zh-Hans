---
solution: Campaign Classic
product: campaign
title: 常用命令
description: 常用命令
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 常用命令{#usual-commands}

此部分列表Adobe Campaign中的常用命令。

命令&#x200B;**nlserver**&#x200B;是整个Adobe Campaign应用程序的输入命令。

此命令的语法如下：**nlserver **`<command>`****`<arguments>`****

参数&#x200B;**`<command>`**&#x200B;与模块对应。

>[!NOTE]
>
>* 无论如何，您都可以添加&#x200B;**-noconsole**&#x200B;参数，以删除在启动模块后显示的注释。
>* 相反，您可以添加参数&#x200B;**-verbose**&#x200B;以显示详细信息。

>



## 监视命令{#monitoring-commands-}

>[!NOTE]
>
>要列表所有模块，您需要使用&#x200B;**nlserver pdump**&#x200B;命令。

可以添加参数&#x200B;**-who**&#x200B;来列表正在进行的连接（数据库和应用程序）。

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

另一个有用的命令是&#x200B;**nlserver monitor**。 它列表监视XML文件(在Adobe Campaign客户端或通过&#x200B;**monitor.jsp**&#x200B;网页获取)。

可以添加参数&#x200B;**-missing**&#x200B;来列表缺失的模块（模块中出错、模块关闭等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

这与具有自动启动但尚未启动的模块相对应。

## 模块启动命令{#module-launch-commands}

用于启动模块的语法仍将具有以下格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 对应于在配置文件中输入的实例的名称，或单实例 **** 模块的默认名称。

## 关闭服务{#shut-down-services}

要停止Adobe Campaign服务，请使用以下命令之一：

* 如果您具有根或管理员访问权限：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >从20.1开始，我们建议改用以下命令（对于Linux）:**systemctl停止nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 否则，在Adobe Campaign帐户中：

   ```
   nlserver shutdown 
   ```

## 重新启动服务{#restart-services}

同样，要重新启动Adobe Campaign，您可以使用以下命令之一：

* 如果您具有根或管理员访问权限：

   * 在Linux中：/etc/init.d/nlserver6开始

      >[!NOTE]
      >
      >从20.1开始，我们建议改用以下命令（对于Linux）:**systemctl开始nlserver**

   * 在Windows中：网络开始nlserver6

* 否则，在Adobe Campaign帐户中：**nlserver watchdog -svc -noconsole**

## config命令{#the-config-command}

使用&#x200B;**config**&#x200B;命令可以管理服务器配置，包括数据库连接的重新配置。

将&#x200B;**nlserver**&#x200B;可执行文件的&#x200B;**config**&#x200B;命令与&#x200B;**-setdblogin**&#x200B;参数一起使用。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

输入密码。

要更改&#x200B;**internal**&#x200B;密码：**nlserver config -internalpassword**

>[!IMPORTANT]
>
>要使用&#x200B;**Internal**&#x200B;标识符登录，您需要事先定义口令。 如需详细信息，请参阅[此部分](../../installation/using/campaign-server-configuration.md#internal-identifier)。

>[!NOTE]
>
>* 通常，您可以使用&#x200B;**config**&#x200B;命令而不是手工修改配置文件
>* 要获取参数的列表，请使用&#x200B;**-?** 参数： **nlserver config -?**
>* 对于Oracle数据库，您不能指定帐户。 语法如下：

>
>  
nlserver config -setdblogin:Oracle:test6@dbserver

