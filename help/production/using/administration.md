---
solution: Campaign Classic
product: campaign
title: 管理
description: 管理
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# 管理{#administration}

自动启动Adobe Campaign模块（**web**、**mta**、**wfserver**&#x200B;等） 由&#x200B;**nlserver**&#x200B;服务器提供。

安装Adobe Campaign会自动配置计算机，使&#x200B;**nlserver**&#x200B;服务开始在启动序列期间启动。

以下命令用于手动开始和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络开始nlserver6**
   * **net stop nlserver6**

* 在Linux（作为根）中：

   * **/etc/init.d/nlserver6开始**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>从20.1开始，我们建议改用以下命令（对于Linux）:**systemctl开始nlserver** / **systemctl停止nlserver**

以下是Linux中可访问的常见管理命令的列表(如&#x200B;**Adobe Campaign**):

* 显示所有已启动的Adobe Campaign模块：**/etc/init.d/nlserver6 pdump**&#x200B;或&#x200B;**/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >将&#x200B;**-who**&#x200B;参数添加到&#x200B;**pdump**&#x200B;命令可以收集有关当前连接（用户和进程）的信息。\
   >**/etc/init.d/nlserver6 status**&#x200B;命令（不带“-who”参数）将返回：
   >
   >    * 如果正在执行所有进程，则为0。
   >    * 1，如果缺少进程。
   >    * 2.如果未执行进程。
   >    * 另一个值。


* 开始/停止多实例或单实例模块(**web**、**trackinglogd**、**syslogd**、**mta**、**wfserver**、**inmail&lt;a1/>):**

   **nlserver开始`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   还可以使用&#x200B;**nlserver restart`<module>[@<instance>]`**&#x200B;命令重新启动模块。

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
   >    * 在紧急事件，使用&#x200B;**-immediate**&#x200B;选项强制立即停止进程（相当于Unix命令&#x200B;**kill -9**）。
   >    * 使用&#x200B;**-noconsole**&#x200B;选项确保启动的模块在控制台上不显示任何内容。 其日志将通过&#x200B;**syslogd**&#x200B;模块写入磁盘。
   >    * 使用&#x200B;**-verbose**&#x200B;选项可显示有关进程操作的其他信息。

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
      此选项会添加其他日志。 我们建议在您找到所需信息后再次启动进程，而不使用&#x200B;**-verbose**&#x200B;选项，以避免日志过载。


* 开始所有Adobe Campaign进程（相当于启动&#x200B;**nlserver6**&#x200B;服务）:

   **nlserver监视程序-noconsole**

* 关闭所有Adobe Campaign进程（相当于关闭&#x200B;**nlserver6**&#x200B;服务）:

   **服务器关闭**

* 编辑&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-`<instance>  .xml </instance>`**&#x200B;文件后，重新加载&#x200B;**nlserver web**&#x200B;模块配置（如果适用，还要重新加载Web服务器扩展模块）。

   **nlserver config -reload**

   >[!NOTE]
   >
   >某些配置更改没有动态考虑；Adobe Campaign必须关闭，然后重新启动。

