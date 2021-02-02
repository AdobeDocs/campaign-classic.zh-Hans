---
solution: Campaign Classic
product: campaign
title: 版本 20.1
description: 版本 20.1
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: b5b9e42eca25193cf4d69f654e74a02afd8adca9
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 8%

---


# 版本 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) 版本 20.1.4 - 版本 9126 {#release-20-1-4-build-9126}

_2020 年 12 月 23 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您通过活动标识服务(IMS)连接到Adobe，则活动服务器和客户端控制台都必须进行升级，才能在2021年3月31日&#x200B;**之后连接到活动。**
   >
   > 
* 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html):升级是强制性的，以增强环境安全性。


* 连接协议已经更新，以遵循新的 IMS 认证机制。
* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)

## ![](assets/do-not-localize/red_2.png) 版本 20.1.3 - 版本 9124{#release-20-1-3-build-9124}

_2020年5月6日_

* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)

## ![](assets/do-not-localize/red_2.png) 版本 20.1.2 - 版本 9123{#release-20-1-2-build-9123}

_2020年3月13日_

* 修复了阻止在Red Hat 7服务器上部署版本的问题。 (NEO-23332)

## ![](assets/do-not-localize/red_2.png) 版本 20.1 - 版本 9122{#release-20-1-build-9122}

_2020年2月17日_

**新增功能**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake联合数据访问连接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake是完全托管的云data warehouse，可在存储和计算级别进行扩展。 有了这个新的连接器，Adobe Campaign现在可以利用Snowflake的强大功能来执行大数据分段。 此连接器可供所有客户使用，包括由Adobe托管。</p>
    <p>有关详细信息，请参阅<a href="../../installation/using/configure-fda-snowflake.md">详细文档</a>和<a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">教程视频</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop联合数据访问连接器增强功能</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>hadoop联合数据访问连接器已得到改进，支持Hadoop3.0和Cloudera。</p>
    <p>有关详细信息，请参阅<a href="../../installation/using/configure-fda-hadoop.md">详细文档</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增强**

* 改进了报告配置中的安全性，以防止点击劫持。 这适用于新报告。 对于旧报告，您需要重新发布它们以应用更改。 (NEO-13282)

* 修复cryptString中的小内存问题。 (NEO-20071)

* 改进了监视器JSP以修复内部IP泄露。 (NEO-16821)

* 修复了堆栈跟踪信息可显示给非管理员用户的问题。 (NEO-12388)

* 改进了对以前会话中缓存数据的管理。 (NEO-17039)

* 修复了导致logins.log文件无法通过IMS记录成功登录尝试的问题。 (NEO-11004)

**改进**

* HTTP2连接器现在支持iOS 13。

* 改进了隔离管理和清除推送通知功能（nms:address和nms:appSubscriptionRcp）使用的表。 对于iOS（仅限HTTP2连接器），禁用的令牌现在处理方式与Android相同。 现在在NmsAppSubscriptionRcp表中设置禁用标志。 [阅读更多](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 在&#x200B;**JavaScript代码**&#x200B;和&#x200B;**高级JavaScript代码**&#x200B;工作流活动中添加了一个新选项，用于定义超时周期。 这可防止javascript执行阶段运行太长。 如果经过超时时间，则停止工作流。 默认超时为1小时。 [阅读更多](../../workflow/using/sql-code-and-javascript-code.md)

* 现在，当在投放服务器上找不到匹配的关联时，中间源分析会停止，并显示相应的错误消息。

* 现在支持Postgres的数据库故障转移：当活动库服务器崩溃和重新启动时，现在数据库自动重新连接到它。

* **开始挂起**&#x200B;视图已添加到“管理”>“审核”>“工作流状态”节点。 这允许您监视实例上等待由&#x200B;**operationMgt**&#x200B;进程启动的所有工作流。 此视图包含在营销活动包中。 [阅读更多](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他变更**

* 在Linux上，nlserver服务启动现在使用系统单元而不是/etc/init.d/nlserver6脚本。 安装20.1包时，将自动执行到新启动方案的迁移。 /etc/init.d/nlserver6仍然提供，但是为了与nlserver服务(开始、重新启动、停止等)交互，我们建议您直接使用systemctl命令。

* 最耗用的自定义表已从&#x200B;**xtkNewId**&#x200B;序列移动到专用序列。 [阅读更多](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 改进了查询性能，这些性能可能会受到不必要的数据库连接的影响。

* 改进了数据库更新向导的性能，以减少SQL语句的数量，从而优化响应时间。

* 数据库记录管理得到了增强。

* 连接池的健壮性已得到改进，这可能防止意外连接故障的发生频率过高。

* 增强了在软错误时向隔离发送地址的电子邮件地址验证规则。 [阅读更多](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 对于Debian,活动现在在系统PCRE库可用时使用它们。

* 活动现在允许使用更新的系统ODBC库。

* 在打开连接以加载富映像时，超时已添加到LINE servlet。 如果加载图像所花的时间过长，Servlet将停止连接以避免出现瓶颈。

**修补程序**

* 修复了使用Hadoop连接器时的帐户密钥加密问题。

* 修复了由于实施SSL认证而导致用户连接在Windows服务器上失败的回归问题。 (NEO-20629)

* 修复了负工作流ID情况下增量查询活动的问题。 (NEO-19779)

* 修复了通过Netezza查询连接器运行联合数据访问时的编码问题。 (NEO-19594)

* 修复了在&#x200B;**Web下载**&#x200B;工作流POST活动中使用事件方法时导致错误的问题。

* 修复了生成优惠建议的问题。 (NEO-18176)

* 修复了使用客户获取Web表单模板时的页脚显示问题。

* 修复了分析连续投放内容中的URL时可能导致其崩溃的问题。 (NEO-16910)

* 修复了在创建新开始时不计算&#x200B;**活动**&#x200B;和&#x200B;**结束**&#x200B;字段的问题。

* 修复了使用URL时的&#x200B;**文件下载**&#x200B;工作流活动的问题。

* 修复了在报表的列表活动中预览导入的查询时的问题。 (NEO-13119)

* 修复了在电子邮件编辑器中选择&#x200B;**由活动**&#x200B;提供个性化块时显示过时图像的问题。

* 客户端与服务器之间的网络通信已得到改进。

* 修复了在同一工作流中创建过多活动的问题。 现在，您创建的工作流不能超过28个。 将显示警告。

* 修复了在&#x200B;**合并**&#x200B;工作流活动中使用&#x200B;**列**&#x200B;对帐选项时的问题。

* 修复了在工作流中使用损坏的扩充列表时可能发生的控制台崩溃问题。 (NEO-18096)

* 修复了工作流(NEO-18010、NEO-18032)中可能发生的各种控制台崩溃问题

* 修复了允许执行&#x200B;**外部信号**&#x200B;工作流活动的问题，即使它被禁用。 (NEO-17524)

* 修复了创建新模式时的问题。

* 修复了发送SMS消息时的跟踪问题。 (NEO-19595)

* 修复了在受众指示器中显示错误的目标投放号的问题。

* 修复了在通过工作流活动生成描述性报告时显示错误百分比的问题。 (NEO-14314)

* 修复了在时间投放参数时使视图吞吐量报告显示不同数字的问题。 (NEO-11783)

* 修复了事务性消息跟踪指示器无法由跟踪工作流更新的问题。 (NEO-17770)

* 修复了在通过SOAP请求优惠时导致Web进程崩溃和重新启动的回归问题。 (NEO-19482)

* 修复了上载目录是远程共享位置时无法将数据上载到公共资源的问题。 (NEO-19361)

* 修复了导致从Adobe Experience Cloud **技术工作流导入受众始终失败的问题。**(NEO-18463)

* 修复了在使用从投放导入的模板时无法发送Experience Manager的问题。 (NEO-17540)

* 修复了升级到构建9032并阻止实例通过SSL协议连接到FTP服务器后出现的问题。 (NEO-20498)

* 修复了在工作流中使用&#x200B;**更新活动**&#x200B;以联合数据访问模式作为定位维度删除、插入或更新大量数据时发生的问题。 (NEO-13280)

* 修复了在HTML内容标记外存在Javascript代码时无法发送电子邮件的问题。 (NEO-18628)

* 修复了在尝试显示来自已发送消息的投放日志的镜像页面时发生的问题。 (NEO-17976)

* 修复了在投放中单击&#x200B;**导入HTML**&#x200B;后，阻止&#x200B;**指向镜像页面**&#x200B;个性化块的链接显示在&#x200B;**文本内容**&#x200B;选项卡中的问题。 (NEO-17568)

* 单击指向已过期的镜像页面的链接时显示错误消息。 (NEO-17340)

* 修复了阻止在&#x200B;**数据分发**&#x200B;创建屏幕中使用某些按钮的问题。

* 修复了在以亚洲／加尔各答为时区的实例中安排投放活动时发生的问题。 (NEO-20001)

* 现在，当投放有关联配置问题时显示错误。

* 修复了在&#x200B;**“关于**”菜单中显示错误版本标签号的问题。

* 修复了在工作流中尝试从重复路由的属性更新投放帐户时发生的问题。 (NEO-18684)

* 修复了通过重定向模块连接到实例时出现的问题，该问题导致关闭后连接无法正确清理。
