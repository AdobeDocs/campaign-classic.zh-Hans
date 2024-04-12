---
product: campaign
title: 常用命令
description: 常用命令
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---

# 常用命令{#usual-commands}



本节列出了Adobe Campaign中的常用命令。

命令 **nlserver** 是整个Adobe Campaign应用程序的输入命令。

此命令具有以下语法： **nlserver **`<command>`****`<arguments>`****

参数 **`<command>`** 对应于模块。

>[!NOTE]
>
>* 无论如何，您可以添加 **-noconsole** 用于删除模块启动后显示的注释的参数。
>* 相反，您可以添加参数 **-verbose** 以显示更多信息。
>

## 监视命令 {#monitoring-commands-}

>[!NOTE]
>
>要列出所有模块，您需要使用 **nlserver pdump** 命令。

您可以添加参数 **-who** 列出正在进行的连接（数据库和应用程序）。

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

另一个有用的命令是 **nlserver monitor**. 它列出了监控XML文件(通过Adobe Campaign客户端获取，或通过 **monitor.jsp** 网页)。

您可以添加参数 **-missing** 列出不存在的模块（模块出错、模块关闭等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

这对应于具有自动启动但尚未启动的模块。

## 模块启动命令 {#module-launch-commands}

Launch模块的语法仍将具有以下格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 对应于在配置文件中输入的实例名称，或 **默认** 用于单实例模块。

## 关闭服务 {#shut-down-services}

要停止Adobe Campaign服务，请使用以下命令之一：

* 如果您具有root或管理员访问权限：

   * 在Linux中：

     ```
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >从20.1开始，我们建议改使用以下命令（对于Linux）： **systemctl stop nlserver**

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

* 如果您具有root或管理员访问权限：

   * 在Linux中：/etc/init.d/nlserver6 start

     >[!NOTE]
     >
     >从20.1开始，我们建议改使用以下命令（对于Linux）： **systemctl启动nlserver**

   * 在Windows中：net start nlserver6

* 否则，在Adobe Campaign帐户中： **nlserver watchdog -svc -noconsole**

## 配置命令 {#the-config-command}

此 **config** 命令用于管理服务器配置，包括重新配置数据库连接。

使用 **config** 命令 **nlserver** 可执行文件 **-setdblogin** 参数。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

输入密码。

要更改 **内部** 密码： **nlserver配置 — internalpassword**

>[!IMPORTANT]
>
>要使用 **内部** 标识符，则需要预先定义密码。 如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 通常，您可以使用 **config** 命令
>* 要获取参数列表，请使用 **-？** 参数： **nlserver配置 — ？**
>* 对于Oracle数据库，不能指定帐户。 语法如下所示：
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>
