---
product: campaign
title: 管理
description: 管理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 管理{#administration}



自动启动Adobe Campaign模块(**web**, **mta**, **wfserver**&#x200B;等) 由提供 **nlserver** 服务器。

安装Adobe Campaign会自动配置计算机，以便 **nlserver** 服务在启动序列期间启动。

以下命令用于手动启动和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络启动nlserver6**
   * **net stop nlserver6**

* 在Linux（作为根）中：

   * **/etc/init.d/nlserver6开始**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>从20.1开始，我们建议改用以下命令（对于Linux）： **systemctl启动nlserver** / **systemctl停止nlserver**

以下是可在Linux中访问的常用管理命令的列表(如 **Adobe Campaign**):

* 显示所有已启动的Adobe Campaign模块： **/etc/init.d** 或 **/etc/init.d/nlserver6状态**

   >[!NOTE]
   >
   >添加 **-who** 参数 **pdump** 命令允许您收集有关当前连接（用户和进程）的信息。\
   >的 **/etc/init.d/nlserver6状态** 命令（不带“ — who”参数）将返回：
   >
   >    * 如果正在执行所有进程，则为0。
   >    * 1，如果流程缺失。
   >    * 2，如果未执行进程。
   >    * 另一个值。


* 启动/停止多实例或单实例模块(**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **nlserver开始`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您还可以使用 **nlserver重新启动`<module>[@<instance>]`** 命令重新启动模块。

   示例:

   **nlserver启动web**

   **nlserver开始mta@my_instance**

   **nlserver stop syslogd**

   **nlserver停止wfserver@my_instance**

   **nlserver停止web-immediate**

   **nlserver重新启动web**

   >[!NOTE]
   >
   >* 如果未指定实例，则将使用“default”实例。
   >* 在发生紧急情况时，使用 **-immediate** 强制立即停止进程的选项（等同于Unix命令） **kill -9**)。
   >* 使用 **-noconsole** 选项，以确保启动的模块在控制台上不显示任何内容。 其日志将通过 **syslogd** 模块。
   >* 使用 **-verbose** 选项，以显示有关流程操作的其他信息。

      >
      >   示例:
      >
      >   **nlserver重新启动web -verbose**
      >
      >   **nlserver start mta@myinstance -verbose**
      >
      >   此选项会添加其他日志。 我们建议在没有 **-verbose** 选项，以避免日志过载。


* 启动所有Adobe Campaign进程(等同于启动 **nlserver6** 服务):

   **nlserver watkdog-noconsole**

* 关闭所有Adobe Campaign进程(等同于关闭 **nlserver6** 服务):

   **nlserver关闭**

* 重新加载 **nlserver web** 模块配置(和web服务器扩展模块（如果适用）) **serverConf.xml** 和 **配置 —`<instance>  .xml </instance>`** 文件已编辑。

   **nlserver配置 — 重新加载**

   >[!NOTE]
   >
   >某些配置更改不会动态考虑；Adobe Campaign必须关闭，然后重新启动。
