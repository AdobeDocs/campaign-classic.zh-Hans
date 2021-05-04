---
solution: Campaign Classic
product: campaign
title: 配置活动选项
description: 了解如何配置活动选项
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '3927'
ht-degree: 0%

---

# Campaign Classic 选项列表{#configuring-campaign-options}

**[!UICONTROL Administration / Platform / Options]**&#x200B;节点允许您配置Adobe Campaign选项。

>[!NOTE]
>
>修改或更新Adobe Campaign选项只能由专家用户执行。

其中一些是内置的，安装活动时，还有一些可以根据需要手动添加。 可用选项因随实例安装的包而异。

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
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> 从可交付性实例中检索到的上一个broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 发送到可交付性实例的上一个broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 投放报告标识符。 请联系支持人员以获取您的标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 要将测试地址用于收件箱渲染的模式列表。 （元素名称用逗号分隔）例如：custom_nms_收件人.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 允许负责投放的运算符确认发送(如果指定了特定运算符或操作员组以在投放的属性中启动投放)。</p><p> 为此，请输入“1”作为值来激活选项。 要取消激活此选项，请输入“0”。</p><p> 然后，发送确认过程将作为默认过程运行：只有在“投放”属性（或管理员）中为发送指定的运算符或操作员组才能确认并执行发送。 请参阅<a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">此小节</a>。</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:收件人)对话。<br /> 选项值必须与与外部模式表匹配的收件人的名称相对应。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 最小收件人数，以便将投放视为计费报表中的主要客户。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 新模板的默认路由服务提供商。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 一次为投放创建的BroadLog数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 每个事务插入（表中）日志(broadLogs):每批要处理的行数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 分析投放投放时中间源部分的分组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 投放的默认投放时间（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 用于标准化投放消息的常规表达式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 输入“1”作为值可排除不再希望与之联系的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 输入“1”作为值可自动忽略多次。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 允许您定义回复消息时使用的错误地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 允许您定义发送消息时使用的发件人地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 允许您定义超时限制（以秒为单位），以便在检索从个性化URL下载并附加到电子邮件的图像时从服务器获取响应。 如果超出此值，则无法发送消息。 默认值为60秒。<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 允许您定义从个性化URL下载并附加到电子邮件的图像所允许的最大大小（以字节为单位）。 默认值为100,000字节。 在发送验证并下载图像以处理电子邮件时，如果图像的大小超过此值或存在下载问题，则投放日志中将显示错误，验证投放将失败。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 允许您在电子邮件或交易电子邮件模板中设置最大数量的附件。 如果超出此值，则在投放分析日志或发布事务电子邮件模板时，将显示警告。 默认值为1 attachment。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 分析期间的最大重试数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> 发布脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> 禁用推送消息的broadLogMsg计数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> 在投放向导中显示消息权重。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> 用户留空时，实例级别上用于电子邮件投放的默认“error”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 用户留空时，实例级别上用于电子邮件投放的默认“发件人”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 用户留空时，实例级别上用于电子邮件投放的默认“回复”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 客户的公用名称。 用于显示给收件人的一些警告消息。<br /> “您收到此消息是因为您与*****或某个附属公司联系。不再接收来自*****"的消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 用户留空时，实例级别上用于电子邮件投放的默认“from”电子邮件标签。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 用户留空时，实例级别上用于电子邮件投放的默认“回复”电子邮件标签。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 两重试电子邮件之间的句点（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 电子邮件的重试期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 用于计算临时投放消息的权重的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 列表授权转发电子邮件地址（来自入站邮件处理模块）。 地址必须用逗号隔开（或*以允许所有地址）。 例如xyz@abc.com,pqr@abc.com。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> “lineImage”servlet中用于对URL(LINE渠道)进行编码的AES键。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 在渠道“email”（用作默认值）时：在将收件人置入隔离之前，SOFT错误被接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailAmpirientErrorDelay</span> <br /> </td> 
   <td> 在渠道“email”（用作默认值）时：在考虑新的SOFT错误之前，自上一个引用的SOFT错误以来花费的最短时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 在渠道“移动”上：在将收件人置入隔离之前，SOFT错误被接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileAmpirentErrorDelay</span> <br /> </td> 
   <td> 在渠道“移动”上：在考虑新的SOFT错误之前，自上一个引用的SOFT错误以来花费的最短时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 允许指定最大时间段（以小时表示），以限制每次执行同步工作流时恢复的广播数。</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing会话中可以并行运行的最大调用数（默认为3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 自定义延迟（以分钟为单位），之后投放被视为“延迟”，默认为30分钟。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>在计算正在运行的投放数时， <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span>技术工作流会使用此选项。</p>它允许您定义超过天数，在运行投放计数中将排除状态不一致的投放。</p><p>默认情况下，该值设置为“7”，这意味着将排除7天以前不一致的投放。</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 发件人地址行1。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> 发件人地址行3。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> 发件人地址行4。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> 发件人地址行6。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 发件人地址行7。<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 镜像页面服务器的URL（默认情况下，应与NmsTracking_ServerUrl相同）。<br /> 在投放定义中未指定URL时，它是电子邮件路由的默认值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 已发送SMS消息的参数：发送到SMS网关以指示消息优先级的信息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> 发送SMS消息时的重试数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> 执行重试条SMS消息的期间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> <span class="uicontrol">NmsUserAgent</span>统计信息的上次合并日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 包含Web区段及其状态的选项的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> 启用/禁用对代码128的特殊字符的支持。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 电子邮件地址的有效字符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 将此选项与"0"值一起添加可禁用投放XML代码版本（右键单击/<span class="uicontrol">编辑XML源</span>或<span class="uicontrol">CTRL + F4</span>快捷键）。<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## 资源{#resources}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> 要在Adobe Campaign客户端控制台中发布的资源位置。 请参阅<a href="../../delivery/using/formatting.md#image-referencing">此小节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> 在Adobe Campaign客户端控制台中预览的资源位置。 请参阅<a href="../../delivery/using/formatting.md#image-referencing">此小节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 上传期间跳过的图像的URL列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 图像上传的配置。 这些值可以是无/跟踪/脚本/列表（可由运算符的可选设置覆盖）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 要存储服务器上映像的文件夹。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 显示徽标的空间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 发布的根文件夹。<br /> 有关HTML和文本内容生成的详细信息，请参 <a href="../../delivery/using/using-a-content-template.md">阅本节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 允许您定义存储投放中使用的图像的服务器，以使浏览器能够获取这些图像。<br /> 对于构建版本  &lt;&gt;<br /> 对于构建版本&gt; 5098，我们使用投放的公共URL或 <span class="uicontrol">XtkFileRes_Public_</span> URL选项的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> 用于配置图像上传的实例名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> 用于配置图像上传的密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> 允许您配置用于图像上传的媒体URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> 投放的联机资源的默认有效期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 公共资源文件的新URL。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 活动和工作流管理{#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> 为此月数显示的营销历史。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 活动的默认有效期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> 由operationMgt工作流启动的投放/工作流/假设验证/模拟作业一次可处理的最大数量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 允许您监视<a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>技术工作流执行。 激活（值“1”）后，执行信息将记录在工作流审核日志中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 在计划模式下定位和提取条件的时间段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 自动重新计算表统计信息后受影响的记录数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 要在导出的报表的右上角显示的标志。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 检查已暂停的工作流之间等待的天数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 通过输入“1”作为值，激活工序所有者对投放的验证。 要取消激活此选项，请输入"0"。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
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
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (安装兼容模式：build&gt;6000)激活时（值“1”），此选项允许使用存储在数据库中的旧口令来连接外部帐户或实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 此密钥用于加密数据库中的大多数口令。 (外部帐户, LDAP口令……)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 如果选择了1，则此选项允许javascript中的权限提升。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 如果选择1，则此选项在文件下载过程中（通过fileDownload.jsp）禁用ACL控件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 如果选择了1，则此选项将禁用Javascript中的文件沙盒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 如果设置为“true”，授权的非管理员操作员将通过部署向导更新xtkOption值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 如果选择了1，则此选项允许使用decryptString解密某些密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 输入“1”值，通过在删除记录之前修改其“修改者”字段，跟踪mData中包含审核跟踪信息的元素删除。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 消息中心{#message-center}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_ExcenshityCustomJs</span> <br /> </td> 
   <td> 个性化JavaScript库，以丰富事件。 必须包含以下两个函数的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">丰富RtEvents(aiEventId);</span> :丰富和保存事件在库中( <span class="uicontrol"></span> 其中aiEventId对应于处理的实时事件表)。</p> </li> 
     <li> <p> <span class="uicontrol">fetthingBatchEvents(aiEventId);</span> :丰富并保存事件在库中( <span class="uicontrol"></span> 其中aiEventId对应于已处理批次事件的ID表)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 通过投放日志进行上次事件状态更新的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 个性化JavaScript库以用于路由事件。 必须包含以下两个函数的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> :返回选定事务性消息的内部名称以处理实时事件(其 <span class="uicontrol"></span> 中iEventId对应于所处理实时事件的ID)。</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> :返回选定事务性消息的内部名称以处理批次事件(其 <span class="uicontrol"></span> 中iEventId对应于所处理批次事件的ID)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 实时事件平均发送时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 实时事件平均发送时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> 实时事件的平均处理时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 实时事件的平均处理时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 排队实时事件的平均数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 实时事件的平均排队时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 实时事件的平均排队时间警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 排队实时事件的平均数警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> 处理实时事件错误的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> 处理实时事件错误的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> 已排队实时事件的最大数目的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 最大排队实时事件数的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 最少排队实时事件数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 已排队实时事件的最小数目的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 等待实时事件队列的临界条件之前的阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 等待实时事件队列警告之前的阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> 实时事件吞吐量的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> 实时事件吞吐量的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> 事件路由的重组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> 更新RtEvent状态的指针（检索数据之前的最后一个日期）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 用于发送欢迎消息的消息中心服务器URL(LINE渠道)。<br /> </td> 
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
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> 定义上次运行清除进程的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>允许您定义从数据库中擦除广播的延迟。</p><p>在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 允许您定义从事件库中抹除数据历史记录的延迟。</p><p>
   在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 允许您定义事件从数据库擦除后的延迟。</p><p>在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 允许您定义从事件库中擦除数据统计信息的延迟。</p><p>在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_CompationPurgeDelay</span> <br /> </td> 
   <td><p> 允许您定义延迟，在延迟后，将从数据库中删除陈述。</p><p> 在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>允许您定义从隔离库中抹除的延迟。</p><p> 在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecylevedDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>允许您定义延迟，在此延迟之后，将从数据库中擦除可回收投放。</p><p> 在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>允许您定义延迟，在此延迟之后，将从数据库中擦除拒绝。</p><p>在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>允许您定义跟踪日志从数据库擦除后的延迟。</p><p>在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 允许您定义从数据库中擦除跟踪统计信息的延迟。</p><p> 在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>允许您定义访客从数据库擦除后的延迟。</p><p> 在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>允许您定义从数据库中擦除工作流结果的延迟。</p><p> 在接口中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse连接器选项。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>允许您根据以下潜在值影响所有工作流和PostgreSQL查询库的“无条件停止”行为：<ul>
    <li><p>0 — 默认：停止工作流进程，对数据库没有影响<p></li>
    <li><p>1 - pg_cancel_backend:停止工作流进程并取消数据库中的查询<p></li>
    <li><p>2 - pg_terminate_backend:停止工作流进程并终止查询库中的<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> 要包含Adobe Campaign表数据的表空间的名称。<br />请参 <a href="../../installation/using/creating-and-configuring-the-database.md">阅创建和配置数据库</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> 要包含Adobe Campaign表索引的表空间的名称。<br />请参 <a href="../../installation/using/creating-and-configuring-the-database.md">阅创建和配置数据库</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> 要包含Adobe Campaign工作表数据的表空间的名称。<br />请参 <a href="../../installation/using/creating-and-configuring-the-database.md">阅创建和配置数据库</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> 要包含Adobe Campaign工作表索引的表空间的名称。<br />请参 <a href="../../installation/using/creating-and-configuring-the-database.md">阅创建和配置数据库</a>。</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 允许您为Microsoft SQL Server上的工作表配置单独的数据库，以优化备份和复制。 该选项与临时数据库的名称相对应：如果指定，将在此数据库中写入工作表。 示例：'tempdb.dbo.' （请注意，名称必须以点结尾）。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">阅读更多</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign实例的时区。 请参阅<a href="../../installation/using/time-zone-management.md#configuration" target="_blank">配置</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> 数据库的字符串字段是否使用NChar定义？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> 数据库的“datetime”字段是否存储时区信息？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> 数据库的ID。 以'u'开头，对于Unicode DataBase。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 添加到自动生成的内部名称的前缀。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_模式_LineCount</span> <br /> </td> 
   <td> 查询在xtk:模式和xtk:srcSchema上返回的最大结果数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 在此之后创建的所有自定义模式（使用autopk="true"而不使用属性"pkSequence"）将获得自动生成的序列"auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq。 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 在迁移过程中，将根据新版本标准自动重新组织树结构。<br /> 此选项允许您禁用导航树的自动迁移。如果您使用它，则迁移后必须删除已废弃的文件夹，添加新文件夹并运行所有必要的检查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">数据类型：</span> Integer</p> </li> 
     <li> <p> <span class="uicontrol">值（文本）</span> :1 </p> </li> 
    </ul> 仅当现成的导航树发生了太多更改时，才应使用此选项。<br /> 有关此内容的详细信息，请参 <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> <span class="uicontrol">NmsEmailErrorStat</span>表清理的上次处理日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 有关Postupgrade中发生的错误的信息，请遵循以下语法：<br /> <strong>{Build number}:{mode:pre/post/...}:{出现错误的'lessThan'/'greaterOrEquelThan' +子步骤}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 输入“1”值，以便不通过清除工作流执行统计信息更新。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 集成{#integration}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> 可用于Adobe Campaign的AEM资源类型。 值必须用逗号分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> 允许您配置Experience Cloud触发器。 数据类型为“长文本”，且必须采用JSON格式。 请参阅<a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">如何将Experience Cloud触发器与Adobe Campaign Classic</a>一起使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;&gt;_&lt;&gt;</span> <br /> </td> 
   <td> 当通过CRM连接器从第三方系统导入数据时，会使用此选项。 通过启用此选项，您只能收集自上次导入以来修改的对象。 必须手动创建并填充此选项，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">内部名称</span> :LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（字段）</span> :上次导入的日期，格式为yyyy/MM/dd hh:mm:ss。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 用于集成的Adobe Target服务器。 默认情况下，此选项已被选中。 此值与Adobe Target域服务器相对应，后跟值/m2。 例如：tt.omtrdc.net/m2。<br /> 请参 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target组织名称。 此值与Adobe Target Client的名称相对应。<br /> 请参 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> 用于与Adobe Audience Manager集成的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> 用于与Adobe Audience Manager集成的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata连接器选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> 配置单元连接器选项。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 优惠{#offers}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> 每个SQL事务更新的优惠券数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompationSynchControl_</span> <br /> </td> 
   <td> '+ [提案的模式] + "_" + extAccountSource。@executionInstanceId + [命题的模式] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompationSynchExec_</span> <br /> </td> 
   <td> '+ [提案的模式] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget。@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 同步工作流跟踪。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 启用/禁用异步命题写入（“0”禁用，“1”启用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> 允许您启用优惠券。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服务器{#server}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> 执行实例标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> 发送帐单报表时使用的客户标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> 用于访问应用程序服务器的内部基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 上次升级前AC实例的内部版本号。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> 公共Web应用程序服务器的基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> 允许您在迁移后继续使用旧的未声明的SQL函数。 由于该选项会带来安全风险，我们强烈建议不要使用此选项。<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> 用于激活跟踪的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFomula</span> <br /> </td> 
   <td> Tracked-URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 用于定义跟踪服务器的外部帐户。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 用于定义跟踪服务器上的实例名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> 上次将跟踪信息与新数据合并的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFomula</span> <br /> </td> 
   <td> 打开URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> 跟踪服务器的口令<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> 指针会跟踪通过其ID和日期处理的最后一条消息事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> 额面跟踪服务器的安全URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 额面跟踪服务器的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> 列表用于联系跟踪服务器的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> 浏览器标识规则集。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFomula</span> <br /> </td> 
   <td> 用于计算Web 跟踪标记的脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> 为Web跟踪管理设计的虚拟投放的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
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
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> 如果选择选项1，则必须在第二步中手动确认在界面中的删除。 否则，将删除数据而不进行确认。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 请求之间等待删除确认的延迟已取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 处理/删除隐私请求时允许的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> 在队列中创建请求之间的延迟，并删除请求数据。<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> 启用LDAP服务器，以用于验证用户身份并向用户提供授权。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> 应用程序登录以联系服务器进行各种搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> 应用程序登录的加密密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> 启用在Adobe Campaign中自动创建运算符和权限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 基于登录名的LDAP DN计算公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 在目录中启用DN搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 搜索基。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN搜索筛选器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> 搜索范围。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> 用于联系LDAP服务器的身份验证类型(plain、md5、lds、ntlm、dpa)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> 启用从LDAP目录到Adobe Campaign中已命名权限的授权和组同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 包含授权名称的LDAP属性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 搜索基。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 搜索用户授权的筛选器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> 表达式从LDAP授权中提取Adobe Campaign权限的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> 搜索范围。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP服务器地址（可以通过指定“：”作为分隔符来指定端口）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web 窗体 {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> 值设置为1将允许在详细信息表单中添加滚动条。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> 要在“其他服务器”模式下用于Web表单失效的实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> 要在“其他服务器”模式下用于Web表单失效的实例的口令。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 用于指定Web表单的失效模式的选项：默认情况下，如果选项为“tracking”，则使用跟踪服务器，并对“other server(s)”选项使用个性化列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> 因Web表单失效而要与服务器联系的个性化地址列表（“其他服务器”模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>
