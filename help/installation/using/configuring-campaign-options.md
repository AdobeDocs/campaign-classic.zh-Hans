---
title: 配置营销活动选项
seo-title: 配置营销活动选项
description: 配置营销活动选项
seo-description: null
page-status-flag: never-activated
uuid: 32e85e41-6898-4fb3-90c8-2201ceea2e91
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 9c1884f6-1dd8-41ab-b8dc-604c8cc2dc89
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 93a19c765e8d3de0fcbc29e27202fcbd2da6d32f

---


# 营销活动经典选项列表{#configuring-campaign-options}

该节 **[!UICONTROL Administration / Platform / Options]** 点允许您配置Adobe Campaign选项。

>[!NOTE]
>
>修改或更新Adobe Campaign选项只能由专家用户执行。

其中一些是内置的，安装Campaign时，另一些则可以根据需要手动添加。 可用选项因实例中安装的包而异。

## 投放 {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span><br /> </td> 
   <td> 从可交付性实例检索的上一个broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span><br /> </td> 
   <td> 发送到可交付性实例的上一个broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span><br /> </td> 
   <td> 传送报告标识符。 请联系支持部门以获取您的标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span><br /> </td> 
   <td> 要将测试地址用于收件箱渲染的架构列表。 （元素名称以逗号分隔）例如：custom_nms_recipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span><br /> </td> 
   <td> 收件人最少数量，以便将付款视为计费报告中的主要分发。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span><br /> </td> 
   <td> 新模板的默认路由服务提供商。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span><br /> </td> 
   <td> 一次为分发创建的BroadLog数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span><br /> </td> 
   <td> 每个事务插入（表格中）日志(broadLogs):每批要处理的行数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span><br /> </td> 
   <td> 分析中间来源补充交货时交货部分的分组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span><br /> </td> 
   <td> 交付的默认交付期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span><br /> </td> 
   <td> 用于标准化传送消息的正则表达式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span><br /> </td> 
   <td> 输入“1”作为值可排除不再希望联系的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span><br /> </td> 
   <td> 输入“1”作为值可自动忽略两倍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span><br /> </td> 
   <td> Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:recipient)进行对话。<br /> 选项值必须与与外部收件人表匹配的架构的名称相对应。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span><br /> </td> 
   <td> 允许您定义回复消息时使用的错误地址语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span><br /> </td> 
   <td> 允许您定义发送消息时使用的发件人地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span><br /> </td> 
   <td> 分析期间的最大重试次数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span><br /> </td> 
   <td> 发布脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span><br /> </td> 
   <td> 禁用推送消息的broadLogMsg计数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span><br /> </td> 
   <td> 在传送向导中显示消息粗细。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span><br /> </td> 
   <td> 用户留空时，实例级别的默认“error”电子邮件地址用于电子邮件发送。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span><br /> </td> 
   <td> 用户留空时，实例级别的默认“发件人”电子邮件地址用于电子邮件发送。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span><br /> </td> 
   <td> 如果用户留空，则默认的“回复”电子邮件地址位于用于电子邮件发送的实例级别。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span><br /> </td> 
   <td> 客户的通用名称。 用于显示给收件人的某些警告消息。<br /> “您收到此消息是因为您与*****或联属公司联系。 不再接收来自*****”的消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span><br /> </td> 
   <td> 如果用户将“发件人”电子邮件标签留空，则默认为实例级别，用于电子邮件发送。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span><br /> </td> 
   <td> 用户留空时，在用于电子邮件发送的实例级别默认的“回复”电子邮件标签。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span><br /> </td> 
   <td> 电子邮件两次重试之间的时间（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span><br /> </td> 
   <td> 电子邮件的重试时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span><br /> </td> 
   <td> 用于计算临时传送消息的权重的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_Whitelist电子邮件</span><br /> </td> 
   <td> 授权转发电子邮件地址列表（来自入站邮件处理模块）。 地址必须用逗号（或*）分隔，才能允许所有地址。 例如xyz@abc.com、pqr@abc.com。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span><br /> </td> 
   <td> 在渠道“email”上（用作默认值）:在将接收者隔离之前，发送过程中SOFT错误被接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailInvergientErrorDelay</span><br /> </td> 
   <td> 在渠道“email”上（用作默认值）:在考虑新的SOFT错误之前，自上一个引用的SOFT错误以来花费的最短时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span><br /> </td> 
   <td> 在渠道“移动”上：在将接收者隔离之前，发送过程中SOFT错误被接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileAppriventErrorDelay</span><br /> </td> 
   <td> 在渠道“移动”上：在考虑新的SOFT错误之前，自上一个引用的SOFT错误以来花费的最短时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span><br /> </td> 
   <td> 镜像页面服务器的URL（默认情况下，应与NmsTracking_ServerUrl相同）。<br /> 在路由定义中未指定URL时，它是电子邮件发送的默认值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span><br /> </td> 
   <td> 发件人地址的第1行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span><br /> </td> 
   <td> 发件人地址的第3行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span><br /> </td> 
   <td> 发件人地址的第4行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span><br /> </td> 
   <td> 发件人地址的第6行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span><br /> </td> 
   <td> 发件人地址的第7行。<br /> </td> 
  </tr>
    <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span><br /> </td> 
   <td><p>在计算正在运行的提交 <span class="uicontrol"><a href="../../workflow/using/campaign.md">数量时</a></span> ,OperationMagt技术工作流会使用此选项。</p>它允许您定义天数，在天数内，状态不一致的交货将从正在运行的交货的计数中排除。</p><p>默认情况下，该值设置为“7”，这意味着将排除早于7天的不一致提交。</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span><br /> </td> 
   <td> 已发送SMS消息的参数：发送到SMS网关以指示消息优先级的信息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span><br /> </td> 
   <td> 发送SMS消息时的重试次数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span><br /> </td> 
   <td> 执行SMS消息重试的期间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span><br /> </td> 
   <td> 电子邮件地址的有效字符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span><br /> </td> 
   <td> 允许指定最大时间段（以小时为单位），以限制每次执行同步工作流时恢复的广播日志数。 请参 <a href="../../platform/using/accessing-an-external-database.md#cloud-messaging---fda-synchronization">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span><br /> </td> 
   <td> MidSourcing会话中可以并行运行的最大调用数（默认情况下为3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span><br /> </td> 
   <td><p> 允许您允许负责交付的操作员确认发送（如果指定特定的操作员或操作员组在交付的属性中开始交付）。</p><p> 为此，请通过输入“1”作为值来激活该选项。 要取消激活此选项，请输入“0”。</p><p> 然后，发送确认过程将作为默认操作：只有在交付属性（或管理员）中为发送指定的操作员或操作员组才能确认和执行发送。 请参 <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">阅此部分</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span><br /> </td> 
   <td> 自定义延迟（以分钟为单位），之后传送被视为“延迟”，默认为30分钟。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span><br /> </td> 
   <td> 启用／禁用对Code128特殊字符的支持。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span><br /> </td> 
   <td> 在“lineImage”servlet中使用AES键对URL（LINE通道）进行编码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span><br /> </td> 
   <td> 包含Web区段及其状态的选项的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span><br /> </td> 
   <td> NmsUserAgent统计数据的上 <span class="uicontrol">次合并日期</span> 。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 添加此选项并带有“0”值，以禁用分发版本的XML代码(右键单击/ <span class="uicontrol">编辑XML源</span> ，或 <span class="uicontrol">CTRL + F4快捷键</span> )。<br /> </td> 
  </tr> 
  <!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr> 
 </tbody> 
</table>-->

## 资源 {#resources}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span><br /> </td> 
   <td> Adobe Campaign客户端控制台中要发布的资源位置。 请参 <a href="../../delivery/using/formatting.md#image-referencing">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span><br /> </td> 
   <td> 在Adobe Campaign客户端控制台中预览的资源位置。 请参 <a href="../../delivery/using/formatting.md#image-referencing">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span><br /> </td> 
   <td> 上传期间跳过的图像的URL蒙版列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 图像上传的配置。 这些值可以是无／跟踪／脚本／列表（可以由运算符的可选设置覆盖）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span><br /> </td> 
   <td> 存储服务器上的图像的文件夹。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span><br /> </td> 
   <td> 显示徽标的空间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span><br /> </td> 
   <td> 发布的根文件夹。<br /> 有关生成HTML和文本内容的详细信息，请参 <a href="../../delivery/using/using-a-content-template.md">阅本节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span><br /> </td> 
   <td> 允许您定义存储传送中使用的图像的服务器，以便浏览器获取这些图像。<br /> 对于构建版本&lt;= 5098，我们使用上传到实例的图像的URL。<br /> 对于构建版本&gt; 5098，我们使用交付的公共URL或 <span class="uicontrol">XtkFileRes_Public_URL</span> 选项的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span><br /> </td> 
   <td> 允许您配置图像上传的实例名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span><br /> </td> 
   <td> 允许您配置图像上传的口令。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span><br /> </td> 
   <td> 允许您配置用于图像上传的媒体URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span><br /> </td> 
   <td> 交付的在线资源的默认有效期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span><br /> </td> 
   <td> 公共资源文件的新URL。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 营销活动和工作流管理 {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span><br /> </td> 
   <td> 显示此月数的营销历史记录。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span><br /> </td> 
   <td> 营销活动的默认有效期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span><br /> </td> 
   <td> 可由OperationMgt工作流开始的一次可处理的交付／工作流／假设／模拟作业的最大数量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span><br /> </td> 
   <td> 允许您监控操作管理技 <a href="../../workflow/using/campaign.md">术工作流</a> ，并执行该工作流。 激活后（值“1”），执行信息将记录在工作流审核日志中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span><br /> </td> 
   <td> 在计划模式下定位和提取条件的时间段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span><br /> </td> 
   <td> 受影响的记录数，之后自动重新计算表统计数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span><br /> </td> 
   <td> 要在导出的报表的右上角显示的标志。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span><br /> </td> 
   <td> 检查已暂停的工作流之间等待的天数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span><br /> </td> 
   <td> 通过输入“1”作为值，激活工序所有者的交货验证。 要取消激活此选项，请输入“0”。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span><br /> </td> 
   <td> 要在工作流的活动“营销资源通知”中加载的其他JS库。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 安全性 {#security}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span><br /> </td> 
   <td> （安装兼容性模式：build&gt;6000）如果输入了“1”，此选项将激活存储密码的兼容性模式。 更改此选项可防止使用存储在数据库中的旧口令。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span><br /> </td> 
   <td> 此密钥用于加密数据库中的大多数口令。 （外部帐户、LDAP口令……）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span><br /> </td> 
   <td> 如果选择1，则此选项允许javascript中的privilegeEscalation。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span><br /> </td> 
   <td> 如果选择1，则此选项将在文件下载过程中（通过fileDownload.jsp）禁用ACL控件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span><br /> </td> 
   <td> 如果选择1，则此选项将禁用Javascript中的文件沙盒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span><br /> </td> 
   <td> 如果设置为“true”，则授权非管理员操作员通过部署向导更新xtkOption值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span><br /> </td> 
   <td> 如果选择1，则此选项允许使用decryptString解密某些密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span><br /> </td> 
   <td> 输入“1”值，以跟踪mData中包含审核跟踪信息的元素删除，方法是在删除记录之前修改其“修改者”字段。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 消息中心 {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_ExcentrixtCustomJs</span><br /> </td> 
   <td> 个性化的JavaScript库以丰富活动。 必须包含以下两个功能的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"></span> 丰富RtEvents(aiEventId);:丰富和保存数据库中的事件( <span class="uicontrol">aiEventId</span> 对应于处理的实时事件表)。</p> </li> 
     <li> <p> <span class="uicontrol"></span> mythingBatchEvents(aiEventId);:丰富和保存数据库中的事件( <span class="uicontrol">其中aiEventId</span> 对应于处理的批处理事件的ID表)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span><br /> </td> 
   <td> 通过交付日志进行上次事件状态更新的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span><br /> </td> 
   <td> 要针对路由事件进行个性化的JavaScript库。 必须包含以下两个功能的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"></span> dispatchRtEvent(iEventId);:返回选定用于处理实时事件的事务性消息的内部名称(其中 <span class="uicontrol">iEventId</span> 对应于所处理实时事件的ID)。</p> </li> 
     <li> <p> <span class="uicontrol"></span> dispatchBatchEvent(iEventId);:返回选定用于处理批处理事件的事务性消息的内部名称(其中 <span class="uicontrol">iEventId</span> 与所处理的批处理事件的ID相对应)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span><br /> </td> 
   <td> 实时事件平均发送时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span><br /> </td> 
   <td> 实时事件平均发送时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span><br /> </td> 
   <td> 实时事件平均处理时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span><br /> </td> 
   <td> 实时事件的平均处理时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span><br /> </td> 
   <td> 排队实时事件的平均数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span><br /> </td> 
   <td> 实时事件的平均排队时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span><br /> </td> 
   <td> 实时事件的平均排队时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span><br /> </td> 
   <td> 排队实时事件的平均数的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span><br /> </td> 
   <td> 实时事件处理错误的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span><br /> </td> 
   <td> 处理实时事件错误的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span><br /> </td> 
   <td> 排队实时事件的最大数量的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span><br /> </td> 
   <td> 排队实时事件的最大数量的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span><br /> </td> 
   <td> 排队实时事件的最小数量的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span><br /> </td> 
   <td> 已排队实时事件的最小数量的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span><br /> </td> 
   <td> 等待实时事件队列的关键条件前的阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span><br /> </td> 
   <td> 挂起实时事件队列警告前的阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span><br /> </td> 
   <td> 实时事件吞吐量的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span><br /> </td> 
   <td> 实时事件吞吐量的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span><br /> </td> 
   <td> 事件路由的重新分组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span><br /> </td> 
   <td> 更新RtEvent状态的指针（检索数据之前的最后一个日期）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span><br /> </td> 
   <td> 用于发送欢迎消息的消息中心服务器URL（LINE频道）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 数据库 {#database}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span><br /> </td> 
   <td> 定义上次运行清除进程的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span><br /> </td> 
   <td> <p>允许您定义从数据库中擦除广播的延迟。</p><p>在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span><br /> </td> 
   <td><p> 允许您定义从数据库中擦除事件历史记录的延迟。</p><p>
   在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span><br /> </td> 
   <td><p> 允许您定义从数据库中擦除事件后的延迟。</p><p>在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span><br /> </td> 
   <td><p> 允许您定义从数据库中擦除事件统计信息的延迟。</p><p>在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_CompationPurgeDelay</span><br /> </td> 
   <td><p> 允许您定义延迟，在延迟后，将从数据库中擦除主张。</p><p> 在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span><br /> </td> 
   <td> <p>允许您定义从数据库中删除隔离的延迟。</p><p> 在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span><br /> </td> 
   <td> <p>允许您定义从数据库中擦除循环的交付的延迟。</p><p> 在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejicesPurgeDelay</span><br /> </td> 
   <td> <p>允许您定义延迟，在此延迟之后，将从数据库中擦除拒绝。</p><p>在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span><br /> </td> 
   <td> <p>允许您定义从数据库中擦除跟踪日志的延迟。</p><p>在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span><br /> </td> 
   <td><p> 允许您定义从数据库中擦除跟踪统计信息的延迟。</p><p> 在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span><br /> </td> 
   <td> <p>允许您定义从数据库中删除访客的延迟。</p><p> 在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span><br /> </td> 
   <td> <p>允许您定义从数据库中抹除工作流结果的延迟。</p><p> 在界面中修改延迟后，会自动创建此选项。 如果从选项列表中修改值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span><br /> </td> 
   <td> Azure SQL Datawarehouse连接器选项。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span><br /> </td> 
   <td>允许您根据以下潜在值影响所有工作流和PostgreSQL数据库查询的“无条件停止”行为：<ul>
    <li><p>0 - default:停止工作流进程，不影响数据库<p></li>
    <li><p>1 - pg_cancel_backend:停止工作流进程并取消数据库中的查询<p></li>
    <li><p>2 - pg_terminate_backend:停止工作流进程并终止数据库中的查询<p></li></ul></td> 
  </tr>  
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span><br /> </td> 
   <td> 要包含Adobe Campaign标准表索引的表空间的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span><br /> </td> 
   <td> 要包含标准Adobe Campaign表数据的表空间的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span><br /> </td> 
   <td> 要包含Adobe Campaign工作表数据的表空间的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span><br /> </td> 
   <td> 要包含Adobe Campaign工作表索引的表空间的名称。<br /> </td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span><br /> </td> 
   <td> 允许您为Microsoft SQL server上的工作表配置单独的数据库。 这将优化备份和复制。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)">阅读更多</a><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span><br /> </td> 
   <td> Adobe Campaign实例的时区。 请参阅 <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">配置</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span><br /> </td> 
   <td> 数据库的字符串字段是否使用NChar定义？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span><br /> </td> 
   <td> 数据库的“datetime”字段是否存储时区信息？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span><br /> </td> 
   <td> 数据库的ID。 对于Unicode DataBase，以“u”开头。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span><br /> </td> 
   <td> 添加到自动生成的内部名称的前缀。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span><br /> </td> 
   <td> xtk:schema和xtk:srcSchema上的查询返回的最大结果数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span><br /> </td> 
   <td> 此时后创建的所有自定义架构（具有autopk="true"且不具有属性"pkSequence"）将获得一个自动生成的序列"auto_ &lt;schemanamespace&gt; &lt;schemaname&gt; _seq"。 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span><br /> </td> 
   <td> 在迁移过程中，将根据新版本标准自动重新组织树结构。<br /> 此选项允许您禁用导航树的自动迁移。 如果您使用它，则在迁移后，您必须删除废弃的文件夹，添加新文件夹并运行所有必要的检查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"></span> 数据类型：整数</p> </li> 
     <li> <p> <span class="uicontrol">值（文本）</span> :1 </p> </li> 
    </ul> 仅当现成的导航树进行了太多更改时，才应使用此选项。<br /> 有关此内容的详细信息，请参 <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span><br /> </td> 
   <td> NmsEmailErrorStat表清除的 <span class="uicontrol">上次处理日期</span> 。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span><br /> </td> 
   <td> <br /> 与Postupgrade中发生的错误相关的信息，请遵循以下语法： <strong>{内部版本号}:{mode:pre/post/...}:{出现错误的'lessThan'/'greaterOrEquelThan' +子步骤}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span><br /> </td> 
   <td> 输入“1”值，以便不会通过清除工作流执行统计信息更新。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration {#integration}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span><br /> </td> 
   <td> 可在Adobe Campaign中使用的AEM资源类型。 值必须用逗号分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span><br /> </td> 
   <td> 允许您配置Experience cloud触发器。 数据类型为“长文本”，且必须采用JSON格式。 请参 <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">阅如何将Experience Cloud触发器与Adobe Campaign Classic结合使用</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span><br /> </td> 
   <td> 当通过CRM连接器从第三方系统导入数据时，将使用此选项。 启用此选项后，您只能收集自上次导入以来修改的对象。 必须手动创建并填充此选项，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">内部名称</span> :LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（字段）</span> :上次导入的日期，格式为yyyy/MM/dd hh:mm:ss。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span><br /> </td> 
   <td> 用于集成的Adobe Target服务器。 默认情况下，此选项已被选中。 此值与Adobe Target域服务器相对应，后跟值/m2。 例如：tt.omtrdc.net/m2。<br /> 请参 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span><br /> </td> 
   <td> Adobe target组织名称。 此值与Adobe Target客户端的名称相对应。<br /> 请参 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span><br /> </td> 
   <td> 用于与Adobe Audience manager集成的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span><br /> </td> 
   <td> 用于与Adobe Audience manager集成的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span><br /> </td> 
   <td> Teradata连接器选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span><br /> </td> 
   <td> Hive连接器选项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 优惠 {#offers}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoopuns_MaxPerTransac</span><br /> </td> 
   <td> 每个SQL事务更新的优惠券数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompationSynchControl_</span><br /> </td> 
   <td> '+ [主张的架构] + "_" + extAccountSource。@executionInstanceId + [命题的架构] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompationSynchExec_</span><br /> </td> 
   <td> '+ [命题架构] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget。@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span><br /> </td> 
   <td> 同步工作流跟踪。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span><br /> </td> 
   <td> 启用／禁用异步命题编写（“0”禁用，“1”启用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span><br /> </td> 
   <td> 允许您启用优惠券。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服务器 {#server}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span><br /> </td> 
   <td> 执行实例标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span><br /> </td> 
   <td> 发送账单报表时使用的客户标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span><br /> </td> 
   <td> 访问应用程序服务器的内部基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span><br /> </td> 
   <td> 上次升级之前的交流实例的内部版本号。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span><br /> </td> 
   <td> 公共Web应用程序服务器的基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span><br /> </td> 
   <td> 允许您在迁移后继续使用旧的未声明的SQL函数。 由于此选项带来的安全风险，我们强烈建议不要使用此选项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟踪 {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span><br /> </td> 
   <td> 用于激活跟踪的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span><br /> </td> 
   <td> 跟踪的URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span><br /> </td> 
   <td> 允许您定义跟踪服务器的外部帐户。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span><br /> </td> 
   <td> 允许您在跟踪服务器上定义实例名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span><br /> </td> 
   <td> 上次将跟踪信息与新数据整合在一起的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span><br /> </td> 
   <td> 打开URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span><br /> </td> 
   <td> 跟踪服务器的口令<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span><br /> </td> 
   <td> 指针会跟踪通过其ID和日期处理的最后一个消息事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span><br /> </td> 
   <td> 额外跟踪服务器的安全URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span><br /> </td> 
   <td> 额面跟踪服务器的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span><br /> </td> 
   <td> 用于联系跟踪服务器的URL列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span><br /> </td> 
   <td> 浏览器标识规则集。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span><br /> </td> 
   <td> 用于计算Web跟踪标签的脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span><br /> </td> 
   <td> 为Web跟踪管理设计的虚拟交付的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span><br /> </td> 
   <td> 允许您定义Web跟踪模式。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 隐私 {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span><br /> </td> 
   <td> 如果选择了选项1，则必须在第二步中手动确认在界面中的删除。 否则，数据将被删除而不进行确认。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span><br /> </td> 
   <td> 请求之间的延迟等待删除确认，请求被取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span><br /> </td> 
   <td> 处理／删除隐私请求时允许的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span><br /> </td> 
   <td> 在队列上创建请求之间的延迟，并删除请求数据。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span><br /> </td> 
   <td> 使LDAP服务器能够用于验证用户身份并向用户提供授权。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span><br /> </td> 
   <td> 应用程序登录以联系服务器进行各种搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span><br /> </td> 
   <td> 应用程序登录的加密密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span><br /> </td> 
   <td> 在Adobe Campaign中支持自动创建运营商和权限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span><br /> </td> 
   <td> 基于登录名的LDAP DN的计算公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span><br /> </td> 
   <td> 在目录中启用DN搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span><br /> </td> 
   <td> 搜索基础。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span><br /> </td> 
   <td> DN搜索筛选器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span><br /> </td> 
   <td> 搜索范围。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span><br /> </td> 
   <td> 用于联系LDAP服务器的身份验证类型(plain、md5、lds、ntlm、dpa)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span><br /> </td> 
   <td> 启用从LDAP目录到Adobe Campaign中指定权限的授权和组的同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span><br /> </td> 
   <td> 包含授权名称的LDAP属性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span><br /> </td> 
   <td> 搜索基础。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span><br /> </td> 
   <td> 搜索用户授权的筛选器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span><br /> </td> 
   <td> 用于从LDAP授权中提取Adobe Campaign权限名称的表达式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span><br /> </td> 
   <td> 搜索范围。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span><br /> </td> 
   <td> LDAP服务器地址（可以通过指定“:”作为分隔符来指定端口）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web表单 {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span><br /> </td> 
   <td> 设置为1的值将允许在详细信息表单中添加滚动条。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span><br /> </td> 
   <td> 在“其他服务器”模式下用于Web表单失效的实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span><br /> </td> 
   <td> 在“其他服务器”模式下用于Web表单失效的实例的口令。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span><br /> </td> 
   <td> 用于指定Web表单的失效模式的选项：默认情况下，如果选项为“跟踪”，则使用跟踪服务器，并将个性化列表与“其他服务器”选项一起使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span><br /> </td> 
   <td> 要因Web表单失效而联系的服务器的个性化地址列表（“其他服务器”模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

