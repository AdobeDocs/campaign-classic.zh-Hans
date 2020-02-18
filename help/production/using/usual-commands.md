---
title: 常规命令
seo-title: 常规命令
description: 常规命令
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# 常规命令{#usual-commands}

此部分列出了Adobe Campaign中的常用命令。

命令 **nlserver** 是整个Adobe Campaign应用程序的输入命令。

此命令的语法如下： **nlserver **`<command>`****`<arguments>`****

该参 **`<command>`** 数与模块相对应。

>[!NOTE]
>
>* 无论如何，您都可以添加 **-noconsole参数** ，以删除在启动模块后显示的注释。
>* 相反，您可以添加参数 **-verbose** 以显示详细信息。
>



## 监视命令 {#monitoring-commands-}

>[!NOTE]
>
>要列出所有模块，您需要使用nlserver pdump **命令** 。

可以添加参数 **-谁** ，以列出正在进行的连接（数据库和应用程序）。

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

另一个有用的命令是 **nlserver monitor**。 它列出监视XML文件(在Adobe Campaign客户端或通过 **monitor.jsp** 网页获取)。

您可以添加缺失参 **数** ，以列出缺失的模块（模块错误、模块关闭等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

这与具有自动启动但尚未启动的模块相对应。

## 模块启动命令 {#module-launch-commands}

启动模块的语法仍将具有以下格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 对应于在配置文件中输入的实例名称，或单实例模 **块的默认** 。

## 关闭服务 {#shut-down-services}

要停止Adobe Campaign服务，请使用以下命令之一：

* 如果您具有根或管理员访问权限：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >从20.1开始，我们建议改用以下命令（对于Linux）:系 **统mctl停止nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 否则，请在Adobe Campaign帐户中：

   ```
   nlserver shutdown 
   ```

## 重新启动服务 {#restart-services}

同样，要重新启动Adobe Campaign，您可以使用以下命令之一：

* 如果您具有根或管理员访问权限：

   * 在Linux中：/etc/init.d/nlserver6开始

      >[!NOTE]
      >
      >从20.1开始，我们建议改用以下命令（对于Linux）:系 **统mctl启动nlserver**

   * 在Windows中：网络启动nlserver6

* 否则，在Adobe Campaign帐户中：nlserver watchdog -svc -noconsole ****

## config命令 {#the-config-command}

使用 **config命令** ，可以管理服务器配置，包括重新配置数据库连接。

使用 **nlserver可执行文件的config** 命令和-setdblogin ******** 参数。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

输入密码。

要更改内部 **密码** : **nlserver config -internalpassword**

>[!CAUTION]
>
>要使用内部标 **识符登录** ，您需要事先定义密码。 如需详细信息，请参阅[此部分](../../installation/using/campaign-server-configuration.md#internal-identifier)。

>[!NOTE]
>
>* 通常，您可以使用config命令，而不是手动修改配 **置文件**
>* 要获取参数列表，请使 **用-?** 参数：nlserver **config -?**
>* 对于Oracle数据库，不能指定帐户。 语法如下：
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


