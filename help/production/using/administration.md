---
title: 管理
seo-title: 管理
description: 管理
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# 管理{#administration}

自动启动Adobe Campaign模块(**web**、 **mta**、 **wfserver**&#x200B;等)由nlserver服务器 **提供** 。

安装Adobe Campaign会自动配置计算机，以便在引导 **序列期间** ,nlserver服务启动。

以下命令用于手动启动和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络启动nlserver6**
   * **网站停止nlserver6**

* 在Linux（作为根）中：

   * **/etc/init.d/nlserver6开始**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>从20.1开始，我们建议改用以下命令（对于Linux）:系 **统mctl启动nlserver** / **systemctl停止nlserver**

以下是Linux中可访问的常见管理命令列表(如 **Adobe Campaign**):

* 显示所有已启动的Adobe Campaign模块： **/etc/init.d/nlserver6 pdump****或/etc/init.d/nlserver6状态**

   >[!NOTE]
   >
   >向pdump命令 **中添加** -who参数 **** 可让您收集有关当前连接（用户和进程）的信息。\
   >/etc/init.d/ **nlserver6 status命令** （不带“-who”参数）将返回：
   >
   >    * 如果正在执行所有进程，则为0。
   >    * 1，如果进程缺失。
   >    * 2.如果未执行进程。
   >    * 另一个值。


* 启动／停止多实例或单实例(**Web**、 **Syntrackinglogd**、 **syslogd**、 ************ mta、Wfserver、Inmail邮件):

   **nlserver开始`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您还可以使用nlserver **restart命`<module>[@<instance>]`**令重新启动模块。

   例如：

   **nlserver启动Web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver停止Web-immediate**

   **nlserver重新启动Web**

   >[!NOTE]
   > 
   >    * 如果未指定该实例，则将使用“default”实例。
   >    * 在发生紧急情况时，使用 **-immediate** 选项强制立即停止进程(相当于Unix命令 **kill -9**)。
   >    * 使用 **-noconsole** 选项可确保启动的模块在控制台上不显示任何内容。 其日志将通过syslogd模块写入 **磁盘** 。
   >    * 使用 **-verbose选项** ，可显示有关进程操作的其他信息。
      >    
      >      
      例如：
      >    
      >      
      **nlserver重新启动web-verbose**
      >    
      >      
      **nlserver start mta@myinstance -verbose**
      >    
      >      
      此选项可添加其他日志。 在您找到所需信息后，我们建议在不使用 **-verbose** 选项的情况下再次启动进程，以避免日志过载。


* 启动所有Adobe Campaign进程(相当于启动 **nlserver6服务** ):

   **nlserver watchdog -noconsole**

* 关闭所有Adobe Campaign进程(相当于关闭 **nlserver6服务** ):

   **服务器关闭**

* 编辑 **serverConf.xml和config** -文件后，重新加载nlserver web ******`<instance>  .xml </instance>`**module配置(以及Web服务器扩展模块（如果适用）)。

   **nlserver config -reload**

   >[!NOTE]
   >
   >某些配置更改不会被动态考虑；必须关闭Adobe Campaign，然后重新启动。

