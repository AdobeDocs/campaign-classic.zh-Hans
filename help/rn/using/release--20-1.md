---
product: campaign
title: 20.1 版
description: 20.1 版
feature: 概述
role: Business Practitioner
level: Beginner
exl-id: 7e4234c9-3d8f-4014-a870-75e91cfad725
source-git-commit: c0a3d9217696f5f5622a6af8f64c62b1a9fbce20
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 19%

---

# 20.1 版{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) 20.1.4 版 - 内部版本 9126 {#release-20-1-4-build-9126}

_2021 年 4 月 15 日_

* 修复了导致 IMS 连接屏幕上出现持续错误消息的客户端控制台回退问题。 (NEO-34821)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2021 年 3 月 22 日_

* 修复了导致无法使用某些控制台组件（如投放中的日期选择器和图像管理）的回退问题。(NEO-31453, NEO-31454)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。

_2020 年 12 月 23 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。[了解详情](../../technotes/ims-updates.md)
   >
   > 
* 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。


* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)

## ![](assets/do-not-localize/red_2.png) 20.1.3 版 - 内部版本 9124{#release-20-1-3-build-9124}

_2020年5月6日_

* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)

## ![](assets/do-not-localize/red_2.png) 20.1.2 版 - 内部版本 9123{#release-20-1-2-build-9123}

_2020 年 3 月 13 日_

* 修复了阻止在Red Hat 7服务器上部署版本的问题。 (NEO-23332)

## ![](assets/do-not-localize/red_2.png) 20.1 版 - 内部版本 9122{#release-20-1-build-9122}

_2020年2月17日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> <strong>SnowflakeFDA连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake是一个完全托管的云data warehouse，旨在在存储和计算级别进行扩展。 借助这款新连接器，Adobe Campaign现在可以利用Snowflake的强大功能执行大数据分段。 此连接器可供所有客户使用，包括由Adobe托管。</p>
    <p>有关更多信息，请参阅<a href="../../installation/using/configure-fda-snowflake.md">详细文档</a>和<a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">教程视频</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>HadoopFDA连接器增强</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>hadoopFDA连接器已得到改进，可支持Hadoop3.0和Cloudera。</p>
    <p>有关详细信息，请参阅<a href="../../installation/using/configure-fda-hadoop.md">详细文档</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 改进了报表配置中的安全性，以防止Clickjacking。 这适用于新报表。 对于旧报表，您需要重新发布这些报表以应用更改。 (NEO-13282)

* 修复了cryptString中的小内存问题。 (NEO-20071)

* 改进了监视器JSP以修复内部IP泄漏。 (NEO-16821)

* 修复了可向非管理员用户显示堆栈跟踪信息的问题。 (NEO-12388)

* 改进了对以前会话中缓存数据的管理。 (NEO-17039)

* 修复了导致logins.log文件无法通过IMS记录成功登录尝试的问题。 (NEO-11004)

**改进**

* 现在，HTTP2连接器支持iOS 13。

* 改进了推送通知功能（nms:address和nms:appSubscriptionRcp）所使用的表的隔离管理和清理。 对于iOS（仅限HTTP2连接器），禁用的令牌现在处理方式与Android相同。 现在，在NmsAppSubscriptionRcp表中设置了禁用标志。 [阅读更多](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 在&#x200B;**JavaScript代码**&#x200B;和&#x200B;**高级JavaScript代码**&#x200B;工作流活动中添加了新选项，以定义超时期限。 这可防止Javascript执行阶段运行过长。 如果超时期间已过，工作流将停止。 默认超时为1小时。 [阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

* 现在，在中间源服务器上找不到匹配的亲和度时，将停止投放分析，并显示相应的错误消息。

* 现在支持Postgres的数据库故障切换：现在，当数据库服务器崩溃并重新启动时，Campaign会自动重新连接到该服务器。

* **启动挂起**&#x200B;视图已添加到“管理”>“审核”>“工作流状态”节点。 这允许您监视实例上等待&#x200B;**operationMgt**&#x200B;进程启动的所有工作流。 此视图随营销活动包一起提供。 [阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他变更**

* 在Linux上，nlserver服务启动现在使用系统单元，而不是/etc/init.d/nlserver6脚本。 安装20.1程序包时，将自动执行到新启动方案的迁移。 /etc/init.d/nlserver6仍然提供，但是为了与nlserver服务（启动、重新启动、停止等）进行交互，我们建议您直接使用systemctl命令。

* 最常用的自定义表已从&#x200B;**xtkNewId**&#x200B;序列移至专用序列。 [阅读更多](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 改进了查询性能，这些性能可能会受到不必要的数据库连接的影响。

* 改进了数据库更新向导的性能，以减少SQL语句的数量，从而优化响应时间。

* 数据库记录管理已得到增强。

* 连接池的稳健性已得到改进，这可能防止意外连接失败的发生频率过高。

* 电子邮件地址验证规则，用于在发生软错误时将地址添加到隔离。 [阅读更多](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 对于Debian，Campaign现在使用系统PCRE库（当它们可用时）。

* Campaign现在允许使用更新的系统ODBC库。

* 在打开连接以加载富图像时，已向LINE servlet添加超时。 如果图像加载时间过长，则Servlet会停止连接以避免瓶颈。

**修补程序**

* 修复了使用Hadoop连接器时的帐户密钥加密问题。

* 修复了由于实施SSL认证而导致Windows服务器上用户连接失败的回归问题。 (NEO-20629)

* 修复了当工作流ID为负时，增量查询活动存在的问题。 (NEO-19779)

* 修复了通过NetezzaFDA连接器运行查询时的编码问题。 (NEO-19594)

* 修复了在&#x200B;**Web下载**&#x200B;工作流事件活动中使用POST方法时导致错误的问题。

* 修复了生成优惠建议时出现的问题。 (NEO-18176)

* 修复了使用客户获取Web表单模板时的页脚显示问题。

* 修复了解析连续投放内容中的URL时可能导致崩溃的问题。 (NEO-16910)

* 修复了在创建新营销活动时未计算&#x200B;**开始**&#x200B;和&#x200B;**结束**&#x200B;字段的问题。

* 修复了使用URL时&#x200B;**文件下载**&#x200B;工作流活动的问题。

* 修复了在报表的查询活动中预览导入的列表时的问题。 (NEO-13119)

* 修复了在电子邮件编辑器中选择&#x200B;**由Campaign**&#x200B;提供支持的个性化块时显示过时图像的问题。

* 客户端与服务器之间的网络通信已得到改进。

* 修复了在同一营销活动中创建的工作流过多的问题。 现在，您无法创建28个以上的工作流。 将显示警告。

* 修复了在&#x200B;**Union**&#x200B;工作流活动中使用&#x200B;**所选列**&#x200B;协调选项的问题。

* 修复了在工作流中使用损坏的扩充列表时可能发生的控制台崩溃问题。 (NEO-18096)

* 修复了工作流中可能发生的各种控制台崩溃问题(NEO-18010、NEO-18032)

* 修复了允许执行&#x200B;**外部信号**&#x200B;工作流活动（即使已禁用该活动）的问题。 (NEO-17524)

* 修复了创建新架构时的问题。

* 修复了发送短信消息时的跟踪问题。 (NEO-19595)

* 修复了投放指示器中显示错误的目标受众数量的问题。

* 修复了在通过工作流活动生成描述性报表时显示错误百分比的问题。 (NEO-14314)

* 修复了在时间视图参数下使投放吞吐量报表显示不同数字的问题。 (NEO-11783)

* 修复了阻止跟踪工作流更新事务型消息跟踪指示器的问题。 (NEO-17770)

* 修复了在通过SOAP请求选件时导致Web进程崩溃并重新启动的回归问题。 (NEO-19482)

* 修复了上载目录是远程共享位置时无法将数据上载到公共资源的问题。 (NEO-19361)

* 修复了导致&#x200B;**从Adobe Experience Cloud**&#x200B;技术工作流导入受众时常失败的问题。 (NEO-18463)

* 修复了使用从Experience Manager导入的模板时无法发送投放的问题。 (NEO-17540)

* 修复了在升级到构建9032并阻止实例通过SSL协议连接到FTP服务器后发生的问题。 (NEO-20498)

* 修复了在使用FDA模式作为定向维度的工作流中使用&#x200B;**更新数据**&#x200B;活动删除、插入或更新大量数据时发生的问题。 (NEO-13280)

* 修复了在HTML内容标记外部存在Javascript代码时无法发送电子邮件的问题。 (NEO-18628)

* 修复了在尝试从已发送消息的投放日志显示镜像页面时发生的问题。 (NEO-17976)

* 修复了在单击投放中的&#x200B;**导入HTML**&#x200B;后，**链接到镜像页面**&#x200B;个性化块无法显示在&#x200B;**文本内容**&#x200B;选项卡中的问题。 (NEO-17568)

* 澄清了单击指向已过期镜像页面的链接时显示的错误消息。 (NEO-17340)

* 修复了导致某些按钮无法在&#x200B;**Data distribution**&#x200B;创建屏幕中使用的问题。

* 修复了在以亚洲/加尔各答为时区的实例中计划投放活动时发生的问题。 (NEO-20001)

* 现在，当投放存在亲和度配置问题时，会显示错误。

* 修复了在&#x200B;**关于**&#x200B;菜单中显示错误版本标签号的问题。

* 修复了尝试从工作流中定期投放的属性更新路由帐户时发生的问题。 (NEO-18684)

* 修复了在通过重定向模块连接到实例时发生的问题，该问题会在关闭后阻止正确清理连接。
