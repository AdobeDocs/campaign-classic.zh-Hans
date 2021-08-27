---
product: campaign
title: 常用命令
description: 常用命令
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---

# 常用命令{#usual-commands}

![](../../assets/v7-only.svg)

本节列出了Adobe Campaign中的常用命令。

命令&#x200B;**nlserver**&#x200B;是整个Adobe Campaign应用程序的输入命令。

此命令具有以下语法：**nlserver **`<command>`****`<arguments>`****

参数&#x200B;**`<command>`**&#x200B;对应于模块。

>[!NOTE]
>
>* 无论如何，您都可以添加&#x200B;**-noconsole**&#x200B;参数，以删除在模块启动后显示的注释。
>* 相反，您可以添加参数&#x200B;**-verbose**&#x200B;以显示更多信息。

>


## 监视命令 {#monitoring-commands-}

>[!NOTE]
>
>要列出所有模块，您需要使用&#x200B;**nlserver pdump**&#x200B;命令。

可添加参数&#x200B;**-who**&#x200B;以列出正在进行的连接（数据库和应用程序）。

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

另一个有用的命令是&#x200B;**nlserver monitor**。 它列出了监控XML文件(在Adobe Campaign客户端中或通过&#x200B;**monitor.jsp**&#x200B;网页获取)。

可以添加参数&#x200B;**-missing**&#x200B;以列出缺失的模块（模块中的错误、模块关闭等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

这对应于具有自动启动功能但尚未启动的模块。

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
>**`<instance>`** 对应于在配置文件中输入的实例名称，或者对于单实 **** 例模块，默认值。

## 关闭服务 {#shut-down-services}

要停止Adobe Campaign服务，请使用以下命令之一：

* 如果您具有根或管理员访问权限：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >从20.1开始，我们建议改用以下命令（对于Linux）：**systemctl停止nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 如果没有，则在Adobe Campaign帐户中：

   ```
   nlserver shutdown 
   ```

## 重新启动服务 {#restart-services}

同样，要重新启动Adobe Campaign，您可以使用以下命令之一：

* 如果您具有根或管理员访问权限：

   * 在Linux中：/etc/init.d/nlserver6开始

      >[!NOTE]
      >
      >从20.1开始，我们建议改用以下命令（对于Linux）：**systemctl启动nlserver**

   * 在Windows中：网络启动nlserver6

* 否则，在Adobe Campaign帐户中：**nlserver watchdog -svc -noconsole**

## 配置命令 {#the-config-command}

使用&#x200B;**config**&#x200B;命令可以管理服务器配置，包括重新配置数据库连接。

使用&#x200B;**-setdblogin**&#x200B;参数的&#x200B;**config**&#x200B;命令对&#x200B;**nlserver**&#x200B;可执行文件执行。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

输入密码。

要更改&#x200B;**internal**&#x200B;密码，请执行以下操作：**nlserver config -internalpassword**

>[!IMPORTANT]
>
>要使用&#x200B;**Internal**&#x200B;标识符登录，您需要事先定义密码。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 通常，您可以使用&#x200B;**config**&#x200B;命令，而不是手动修改配置文件
>* 要获取参数列表，请使用&#x200B;**-?** 参数： **nlserver配置 — ?**
>* 对于Oracle数据库，不能指定帐户。 语法如下所示：
>
>  nlserver config -setdblogin&lt;a0/test6@dbserver:Oracle:
