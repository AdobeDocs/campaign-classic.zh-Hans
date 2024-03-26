---
product: campaign
title: 管理
description: 管理
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 3%

---

# 管理{#administration}



Adobe Campaign模块的自动启动(**Web**， **mta**， **wfserver**、等) 由 **nlserver** 服务器。

安装Adobe Campaign会自动配置计算机，以便 **nlserver** 服务在启动序列中启动。

以下命令用于手动启动和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络启动nlserver6**
   * **网络停止nlserver6**

* 在Linux中（作为根）：

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>从20.1开始，我们建议改使用以下命令（对于Linux）： **systemctl启动nlserver** / **systemctl stop nlserver**

以下是在Linux中可访问的常用管理命令列表(如 **Adobe Campaign**)：

* 显示所有启动的Adobe Campaign模块： **/etc/init.d/nlserver6 pdump** 或 **/etc/init.d/nlserver6状态**

  >[!NOTE]
  >
  >添加 **-who** 参数到 **pdump** 命令可以收集有关当前连接（用户和进程）的信息。\
  >此 **/etc/init.d/nlserver6状态** 命令（不带“ — who”参数）将返回：
  >
  >    * 如果正在执行所有进程，则为0。
  >    * 如果缺少进程，则为1。
  >    * 如果未执行任何进程，则为2。
  >    * 如果存在错误，则为另一个值。
  >

* 启动/停止多实例或单实例模块(**Web**， **trackinglogd**， **syslogd**， **mta**， **wfserver**， **inmail**)：

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  您也可以使用 **nlserver重新启动`<module>[@<instance>]`** 命令重新启动模块。

  例如：

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver restart web**

  >[!NOTE]
  >
  >* 如果未指定实例，则将使用“默认”实例。
  >* 在出现紧急情况时，请使用 **-immediate** 强制立即停止进程的选项（相当于Unix命令） **kill -9**)。
  >* 使用 **-noconsole** 选项，以确保启动的模块不会在控制台上显示任何内容。 其日志将通过 **syslogd** 模块。
  >* 使用 **-verbose** 选项，以显示有关流程操作的其他信息。
  >
  >   例如：
  >
  >   **nlserver restart web -verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   此选项添加其他日志。 我们建议重新开始流程，不执行 **-verbose** 选项，以避免日志过载。

* 启动所有Adobe Campaign进程(相当于启动 **nlserver6** 服务)：

  **nlserver watchdog -noconsole**

* 关闭所有Adobe Campaign进程(相当于关闭 **nlserver6** 服务)：

  **nlserver shutdown**

* 重新加载 **nlserver web** 模块配置（以及Web服务器扩展模块，如果适用） **serverConf.xml** 和 **config-`<instance>  .xml </instance>`** 文件已编辑。

  **nlserver配置 — reload**

  >[!NOTE]
  >
  >某些配置更改不会动态考虑；必须关闭Adobe Campaign后重新启动。
