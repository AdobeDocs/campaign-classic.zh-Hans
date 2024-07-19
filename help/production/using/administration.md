---
product: campaign
title: 管理
description: 管理
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# 管理{#administration}

Adobe Campaign模块（**web**、**mta**、**wfserver**&#x200B;等）的自动启动 由&#x200B;**nlserver**&#x200B;服务器提供。

安装Adobe Campaign会自动配置计算机，以便在启动序列中启动&#x200B;**nlserver**&#x200B;服务。

以下命令用于手动启动和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络启动nlserver6**
   * **网络停止nlserver6**

* 在Linux中（作为根）：

   * **/etc/init.d/nlserver6启动**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>从20.1开始，我们建议改用以下命令（对于Linux）： **systemctl start nlserver** / **systemctl stop nlserver**

以下是在Linux中可访问的常用管理命令列表(如&#x200B;**Adobe Campaign**)：

* 显示所有已启动的Adobe Campaign模块： **/etc/init.d/nlserver6 pdump**&#x200B;或&#x200B;**/etc/init.d/nlserver6状态**

  >[!NOTE]
  >
  >通过将&#x200B;**-who**&#x200B;参数添加到&#x200B;**pdump**&#x200B;命令，您可以收集有关当前连接（用户和进程）的信息。\
  >**/etc/init.d/nlserver6 status**&#x200B;命令（不带“ — who”参数）将返回：
  >
  >    * 如果正在执行所有进程，则为0。
  >    * 如果缺少进程，则为1。
  >    * 如果未执行任何进程，则为2。
  >    * 如果存在错误，则为另一个值。
  >

* 启动/停止多实例或单实例模块(**web**、**trackinglogd**、**syslogd**、**mta**、**wfserver**、**inmail**)：

  **nlserver启动`<module>[@<instance>]`**

  **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

  您还可以使用&#x200B;**nlserver restart`<module>[@<instance>]`**&#x200B;命令重新启动模块。

  例如：

  **nlserver启动web**

  **nlserver启动mta@my_instance**

  **nlserver停止syslogd**

  **nlserver停止wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver重新启动web**

  >[!NOTE]
  >
  >* 如果未指定实例，则将使用“默认”实例。
  >* 在紧急情况下，使用&#x200B;**-immediate**&#x200B;选项强制立即停止进程（等同于Unix命令&#x200B;**kill -9**）。
  >* 使用&#x200B;**-noconsole**&#x200B;选项可确保启动的模块不会在控制台上显示任何内容。 其日志将通过&#x200B;**syslogd**&#x200B;模块写入磁盘。
  >* 使用&#x200B;**-verbose**&#x200B;选项可显示有关进程操作的其他信息。
  >
  >   例如：
  >
  >   **nlserver重新启动web -verbose**
  >
  >   **nlserver启动mta@myinstance -verbose**
  >
  >   此选项添加其他日志。 我们建议您在找到所需信息后重新启动进程，而不使用&#x200B;**-verbose**&#x200B;选项，以避免日志过载。

* 启动所有Adobe Campaign进程（相当于启动&#x200B;**nlserver6**&#x200B;服务）：

  **nlserver watchdog -noconsole**

* 关闭所有Adobe Campaign进程（相当于关闭&#x200B;**nlserver6**&#x200B;服务）：

  **nlserver关闭**

* 编辑&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-`<instance>  .xml </instance>`**&#x200B;文件时，重新加载&#x200B;**nlserver web**&#x200B;模块配置（以及Web服务器扩展模块，如果适用）。

  **nlserver配置 — 重新加载**

  >[!NOTE]
  >
  >某些配置更改不会动态考虑；必须关闭Adobe Campaign后重新启动。
