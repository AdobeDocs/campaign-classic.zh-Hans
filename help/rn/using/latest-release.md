---
title: 最新版本
description: 最新Campaign Classic发行说明
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 3%

---


# 最新版本{#latest-release}

本页列表了最新Campaign Classic发行候选版附带的新功 **能、改进和修复**。

有关Campaign Classic金标版（最新GA版本）, [请参阅本页](../../rn/using/gold-standard.md)。

## ![](assets/do-not-localize/blue_2.png) 版本 20.3.1 - 版本 9228 {#release-20-3-1-build-9228}

_2020年10月27日_

**新增功能**

<table> 
<thead>
<tr> 
<th> <strong>iOS推送通知改进</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>在将移动应用程序与活动集成时，您需要确保与Apple推送通知服务(APNs)的通信安全。 您可以使用基于证书或基于令牌的身份验证。
</p>
<p>以下两种身份验证模式现在可用于Campaign Classic中的iOS移动应用程序：
</p>
<ul> 
<li><p>基于令牌的身份验证（推荐）:此身份验证模式基于。p8文件。 此身份验证模式速度更快，因为对APNs的每个请求都包含令牌。 <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">了解详情</a></p></li>
<li><p>基于证书的身份验证：此身份验证模式基于。p12文件。 对于每个应用程序，都需要一个单独的证书。 此证书由Apple通过您的开发人员帐户提供。 <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">了解详情</a></p></li> 
</ul>
<p>在详细文档中了解如何在活动中选 <a href="../../delivery/using/configuring-the-mobile-application.md">择身份验证模式</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Android推送通知改进</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Android推送通知已得到改进，可支持FCM HTTP v1 API，用于Android推送渠道身份验证。 </p>
<p>使用新的受支持API版本，您现在可以发送FCM通知消息，该消息提供增强的富推送消息功能。 <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">了解详情</a></p> 
<p>在本节中，了解如何在Adobe Campaign中为Android配置FCM HTTP v1 <a href="../../delivery/using/configuring-the-mobile-application-android.md">API</a> 。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增强**

* 库的安全加载：为了防止DLL预加载攻击，活动现在仅从Windows默认系统DLL路径中加载Windows DLL，同时加载活动客户端(nlclient)。 [了解更多](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* 修复了一个安全问题，以加强针对服务器端请求伪造(SSRF)攻击的保护。 (NEO-25661)
* 修复了处理GDPR隐私请求时发生的问题，该问题导致记录无法从与收件人表具有二级关系的自定义表中删除。 (NEO-25967)
* 修复了在尝试同步Adobe Experience Manager模板时使用非管理员用户发出的API调用的安全问题。 (NEO-23487)

**兼容性更新**

Campaign 现在支持以下系统：
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**已弃用的功能**

20.3中已弃用以下功能：

* 用于将受众导入和导出到Adobe Experience Cloud的demdex域已弃用。 如果您正在导入／导出外部帐户使用demdex域，则需要相应地调整实施。 [了解详情](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* 最初基于oAUTH身份验证设置触发集成身份验证以访问管道现已更改并移至AdobeI/O。 [了解更多](../../integrations/using/about-triggers.md)

在已弃用和已删 [除的功能页面了解更多信息](../../rn/using/deprecated-features.md)。

**改进**

* 客户端控制台已做 **了若干改进**:
   * 为防止与某些因特网安全GPO规则限制不兼容，活动客户端控制台登录屏幕已被内置标准Windows表单取代。
   * 修复了在使用64位客户端控制台的工作流中复制／粘贴活动时的问题。 (NEO-27635)
   * 在“关 **于** ”菜单中，添加了信息以区分64位和32位控制台。
* 现在，在恢复工作流时，工作流标识符会显示在日志中，这使您能够更好地识别已恢复的工作流。
* 引入了新的永久Cookie:nllastdelid。 此Cookie（UUID230除外）将存储deliveryId。 当会话cookie不存在时，将从此cookie中存在的deliveryId获取广播信息。
此更改修复了浏览器会话结束时发生的问题：已删除包含deliveryId和broadlogId的会话cookie。 如果没有deliveryId，则找不到广播信息，并且如果是永久跟踪(上次投放)，将丢失跟踪表信息。
在本节中进一步了 [解cookies](../../platform/using/privacy-and-recommendations.md#cookies)。
* 通过在投放发送之前重新启动MTA进程，改进了可交付性服务器的高容量投放吞吐量性能。

**其他变更**

* 对SFTP使用相对路径时， `~/` 不再自动添加字符。 如果需要，您可以手 `~/` 动向路径添加字符，但Adobe建议使用绝 **对路径**。
* 在使用Microsoft SQL Server配置新数据库时，Windows NT身份验证已从可用的身份验证方法中删除。 [阅读更多](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* 为了提高性能，已针对Teradata优化了数据库清理工作流。 (NEO-19959)
* 改进了从Adobe Target插入图像时显示的错误消息，并且外部帐户中的租户名称为空。
* 在投放属性中， **[!UICONTROL Archive emails]** 选项已更名 **[!UICONTROL Email BCC]**。
* 为了提高健壮性，现在选择所有节点无效的查询都被拒绝。 如果需要禁用检查并返回到以前的行为，可将XtkSecurity_Disable_QueryCheck设置为0。

**技术演进**

Tomcat已从版本7(7.0.103)更新到版本8(8.5.57)。

该 `tomcat-7` 目录将替换为目 `tomcat-8` 录。

在windows上， _iis_neolane_setup_ .vbs和 _apache_neolane.conf_ 现在安装在目 `conf` 录中(而非以 `tomcat-7/conf` 前)。

在linux上， _apache_neolane_ .conf现在安装在目 `conf` 录中。

**修补程序**

* 修复了可能阻止重新计算投放统计信息的问题。
* 修复了在使用旧版本连接到服务器的Campaign Classic9080版本上传CSV文件时显示错误消息的问题。 (NEO-23218)
* 修复了在为外部帐户配置Microsoft Dynamics CRM向导时可能显示错误消息的问题。 这是由于与最新MS Dynamics CRM API版本的兼容性问题。 (NEO-24528)
* 修复了无法使用CRM连接器将查找类型记录（即由与其他表连接的外键记录组成的数据）导出到Microsoft Dynamics的问题。 (NEO-23864)
* 修复了在CRM连接器中启用“自动索引”选项时，可 **能会阻止** 获取Microsoft Dynamics数据的问题。 (NEO-25981)
* 修复了IMS身份验证的一个问题，该问题可能导致连接即使已结束也会打开。 终止的连接现在在结束后将自动关闭，以避免累积连接并消耗系统资源。 (NEO-25996)
* 修复了由于Adobe Experience Manager配置错误（帐户或密码不正确）导致投放同步外部帐户内容失败时不显示错误消息的问题。 现在，在出现故障时会显示一条消息，使您能更轻松地识别问题。 (NEO-25586)
* 修复了在“更新”数据活动 **中选择** “更新”操作类 **型时发生的问** 题。 如果要更新的数据不正确，则工作流将出错并失败。 如果数据不正确，工作流将不会失败，并且记录将存储到拒绝 **出站** 过渡。 (NEO-23794)
* 修复了可能阻止包含子工作流的工作流工作的问题。 (NEO-24036)
* 修复了在编辑活动模板描述时阻止“保 **存** ”按钮在复制粘贴符号（例如日语字符）时显示的问题。 (NEO-27071)
* 修复了一个问题，该问题可能会阻止您在实例配置向导中更改跟踪服务器。
* 修复了在单击窗口外部之前单击“保存”按钮时，活动或活动模板的描述无法保 **存的** 问题。 (NEO-27449)
* 修复了一个问题，该问题可 **能会阻止有效付费用户档案** (billingActiveContactCount)的技术工作流正常工作。 如果对模式扩展中的计算字段执行了链接，则可能会发生这种情况。 大量数据被创建，这可能导致数据库耗尽临时空间。 (NEO-24062)
* 修复了数据加 **载（文件）活动的问题** ，如果将日文字符放在文件末尾，该问题可能会阻止您从txt和csv文件导入日文字符。 (NEO-24957)
* 修复了连续投放的问题，该问题可能会 **阻止正确填****充“已开始** 分析”和“已完成分析”字段。 (NEO-20755)
* 修复了在预览(nms:收件人)以外的其他模式上查询后尝试收件人SMS消息时 **可能** 显示错误消息的问题。 (NEO-27517)
* 修复了使用Snowflake联合数据访问连接器时的问题。 具有Snowflake联合数据访问访问名称权限的用户无法对Snowflake模式执行查询。 日志中显示“找不到密码”类型的错误。 (NEO-23851)
* 修复了使用联合数据访问连接器时的问题，该连接器在链接的联合数据访问模式名称是当前模式的元素名称的子字符串时发生。 例如，如果联合数据访问模式是“客户”，而收件人模式中的某个元素是“客户”，则会发生这种情况。 在提取“customer”元素中的列并从“cust”联合数据访问模式添加列时，缺少本地列的值。 (NEO-20193)
* 修复了从外部工作流库获取记录并将记录插入活动库时的问题。 (NEO-26359)
* 修复了更新事件状态 **技术工作流中** 的问题：要与投放统计活动中传入的相应字段的大小 **匹配** ,“更新投放统计”活动中三个目 **** 标字段的大小从32位更改为64位。 (NEO-11557)在本节中进一步了 **解更新事件** 状态工 [作流程](../../workflow/using/message-center--execution-.md)。
* 修复了消息中 **心事件历史报告中** ，在尝试应用过滤器时导致脚本错误并导致无法按日期范围过滤的问题。 (NEO-23365)
* 修复了活动作业( **operationMgt** )和预览( **预测)技术工作流之** 间的干扰问题。 当计划投放处于“目标就绪”或“准备交付”状态时，会发生这种情况。 (NEO-20819)
* 修复了xtkOperator中的mdata字段中不存在XML标识符时的XML解析问题。 它导致了暴露故障。 (NEO-26113)
* 修复了使用链接到在SSL **中加密的Azure活动的** “文件传输外部帐户”(File Transfer Transfer)时，使用HTTP而不是HTTPS建立连接的问题。 (NEO-26720)
* 修复了MSSQL数据库在清理工作流期间，up_updatestats过程可能出错的问题。
* 修复了在Web进程关闭期间发生的崩溃（如果交互请求仍在处理中）。 (NEO-26447)
* 修复了Oracle DB中 **的NoNull** 函数在升级9032后不再工作的问题。 (NEO-26488)
* 修复了在未安装消息中心包的情况下安装LINEV2包时，在升级9171后跟踪工作流失败的问题。
* 修复了一个可伸缩性问题，该问题导致连接池无法增加到所需的连接数，因为属性“APP”的数据库连接字符串最终获得无效值。 (NEO-25105)
* 修复了代理配置级别上的一个问题，该问题导致在最新Windows 10更新后无法登录Adobe Campaign。 (NEO-27813)
* 修复了在导入包含跟踪链接的HTML模板后，使不需要的URL在传送的电子邮件中可见的问题。 (NEO-25909)
* 修复了在工作流中显示拆分目标的其余活动数据时导致服 **务器** 崩溃的问题。
* 修复了在清除表达式分析器时防止内存损坏的服务器崩溃问题。 (NEO-26856)
* 修复了非管理员用户定义实例变量的扩充活动中的问题。 (NEO-25653)