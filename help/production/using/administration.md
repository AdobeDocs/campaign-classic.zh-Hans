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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---


# 管理{#administration}

自动启动Adobe Campaign模&#x200B;**块**( **web**、 **mta**、wfserver等) 由nlserver服务 **器提供** 。

安装Adobe Campaign会自动配置计算机，以 **便nlserver** 服务开始在启动序列期间启动。

以下命令用于手动开始和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络开始nlserver6**
   * **net stop nlserver6**

* 在Linux（作为根）中：

   * **/etc/init.d/nlserver6开始**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>从20.1开始，我们建议改用以下命令（对于Linux）: **systemctl开始nlserver** / **systemctl停止nlserver**

以下是Linux中可访问的常见管理命令的列表(如 **Adobe Campaign**):

* 显示所有已启动的Adobe Campaign模块： **/etc/init.d/nlserver6 pdump** 或 **/etc/init.d/nlserver6状态**

   >[!NOTE]
   >
   >将-who **参数添加** 到pdump命令 **** 后，您可以收集有关当前连接（用户和进程）的信息。\
   >/etc/init.d/ **nlserver6 status** 命令（不带“-who”参数）将返回：
   >
   >    * 如果正在执行所有进程，则为0。
   >    * 1，如果缺少进程。
   >    * 2.如果未执行进程。
   >    * 另一个值。


* 开始/停止多实例或单实例模块(**web**、 **syslogd**、 **sysloglogd**、 **mta**、 **wfserver******、、、邮件):

   **nlserver开始`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   还可以使用nlserver restart **命令重`<module>[@<instance>]`** 新启动模块。

   示例:

   **nlserver开始web**

   **nlserver开始mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver停止web-immediate**

   **nlserver重新启动web**

   >[!NOTE]
   > 
   >    * 如果未指定该实例，将使用“默认”实例。
   >    * 在紧急事件，使用 **-immediate** 选项强制立即停止进程(相当于Unix命令 **kill -9**)。
   >    * 使用- **noconsole** 选项确保启动的模块在控制台上不显示任何内容。 其日志将通过syslogd模块写入 **磁盘** 。
   >    * 使用- **verbose选项** ，可显示有关进程操作的其他信息。

      >    
      >      
      示例:
      >    
      >      
      **nlserver重新启动web -verbose**
      >    
      >      
      **nlserver开始mta@myinstance -verbose**
      >    
      >      
      此选项会添加其他日志。 我们建议在您找到所需信息后， **再次启动进程** ，而不要使用-verbose选项，以避免日志过载。


* 开始所有Adobe Campaign进程(相当于启动 **nlserver6服务** ):

   **nlserver监视程序-noconsole**

* 关闭所有Adobe Campaign进程(相当于关闭 **nlserver6** 服务):

   **服务器关闭**

* 编辑 **serverConf.xml** 和config-文件后，重新加载nlserver web ******`<instance>  .xml </instance>`** module配置（和web server extension module，如果适用）。

   **nlserver config -reload**

   >[!NOTE]
   >
   >某些配置更改没有动态考虑；Adobe Campaign必须关闭，然后重新启动。

