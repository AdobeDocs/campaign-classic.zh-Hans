---
product: campaign
title: 管理
description: 管理
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 管理{#administration}

自动启动Adobe Campaign模块（**web**、**mta**、**wfserver**&#x200B;等） 由&#x200B;**nlserver**&#x200B;服务器提供。

安装Adobe Campaign会自动配置计算机，以便在引导序列期间启动&#x200B;**nlserver**&#x200B;服务。

以下命令用于手动启动和关闭Adobe Campaign服务：

* 在Windows中：

   * **网络启动nlserver6**
   * **net stop nlserver6**

* 在Linux（作为根）中：

   * **/etc/init.d/nlserver6开始**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>从20.1开始，我们建议改用以下命令（对于Linux）：**systemctl启动nlserver** / **systemctl停止nlserver**

以下是可在Linux中访问的常用管理命令列表(如&#x200B;**Adobe Campaign**):

* 显示所有已启动的Adobe Campaign模块：**/etc/init.d/nlserver6 pdump**&#x200B;或&#x200B;**/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >将&#x200B;**-who**&#x200B;参数添加到&#x200B;**pdump**&#x200B;命令中，可让您收集有关当前连接（用户和进程）的信息。\
   >**/etc/init.d/nlserver6 status**&#x200B;命令（不带“ — who”参数）将返回：
   >
   >    * 如果正在执行所有进程，则为0。
   >    * 1，如果流程缺失。
   >    * 2，如果未执行进程。
   >    * 另一个值。


* 启动/停止多实例或单实例模块(**web**、**trackinglogd**、**syslogd**、**mta**、**wfserver**、**inmail**):

   **nlserver开始`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您还可以使用&#x200B;**nlserver restart`<module>[@<instance>]`**&#x200B;命令重新启动模块。

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
   >* 在发生紧急情况时，使用&#x200B;**-immediate**&#x200B;选项强制立即停止该进程（等同于Unix命令&#x200B;**kill -9**）。
   >* 使用&#x200B;**-noconsole**&#x200B;选项确保启动的模块在控制台上不显示任何内容。 其日志将通过&#x200B;**syslogd**&#x200B;模块写入磁盘。
   >* 使用&#x200B;**-verbose**&#x200B;选项可显示有关进程操作的其他信息。

      >
      >   
      示例:
      >
      >   
      **nlserver重新启动web -verbose**
      >
      >   
      **nlserver start mta@myinstance -verbose**
      >
      >   
      此选项会添加其他日志。 我们建议您在找到所需信息后，再次启动不使用&#x200B;**-verbose**&#x200B;选项的进程，以避免日志过载。


* 启动所有Adobe Campaign进程（等同于启动&#x200B;**nlserver6**&#x200B;服务）：

   **nlserver watkdog-noconsole**

* 关闭所有Adobe Campaign进程（等同于关闭&#x200B;**nlserver6**&#x200B;服务）：

   **nlserver关闭**

* 编辑了&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-`<instance>  .xml </instance>`**&#x200B;文件后，重新加载&#x200B;**nlserver web**&#x200B;模块配置（以及适用的Web服务器扩展模块）。

   **nlserver配置 — 重新加载**

   >[!NOTE]
   >
   >某些配置更改不会动态考虑；Adobe Campaign必须关闭，然后重新启动。
