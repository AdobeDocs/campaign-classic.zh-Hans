---
product: campaign
title: 配置Campaign选项
description: 了解如何配置Campaign选项
feature: Installation, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '3838'
ht-degree: 1%

---

# Campaign Classic选项列表{#configuring-campaign-options}

此 **[!UICONTROL Administration / Platform / Options]** 节点允许您配置Adobe Campaign选项。 其中一些是在安装Campaign时内置的，而其他则可以在需要时手动添加。 可用选项因随实例一起安装的软件包而异。


>[!CAUTION]
>
>* 此页面中未列出的选项仅供内部使用，并且 **不得修改**.
>
>* 修改或更新Adobe Campaign选项只能由专家用户执行。

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
   <td> 从可投放性实例检索的最后一个broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 上次发送到可投放性实例的broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 投放报告标识符。 请联系支持人员以获取您的标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 您希望使用测试地址进行收件箱呈现的架构列表。 （元素名称用逗号分隔）例如： custom_nms_recipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> 密件抄送电子邮件地址，Enhanced MTA会向其发送已发送电子邮件的原始副本。 <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 允许您允许负责投放的操作员确认发送，如果指定了特定操作员或操作员组来在投放的属性中开始投放。</p><p> 要执行此操作，请通过输入“1”作为值激活选项。 要停用此选项，请输入“0”。</p><p> 然后，发送确认流程将默认运行：只有投放属性中为发送指定的操作员或操作员组（或管理员）才能确认并执行发送。 请参阅<a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">此小节</a>。</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms：recipient)进行对话。<br /> 选项值必须对应于与外部收件人表匹配的架构的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 为了在账单报告中将投放视为主要投放而允许的最小收件人数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 新模板的默认路由服务提供商。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 在投放准备期间插入broadLog的最小批次大小（行数）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 批次持续时间阈值（毫秒数），在投放准备期间插入broadLog的批次大小加倍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 分析中间源投放时投放部分的分组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 投放的默认投放期限（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 用于标准化投放消息的正则表达式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 输入“1”作为值可排除不再希望被联系的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 输入“1”作为值可自动忽略翻倍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 用于定义答复消息时使用的错误地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 用于定义发送消息时使用的发件人地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 用于定义超时限制（以秒为单位），以便在检索从个性化URL下载并附加到电子邮件的图像时从服务器获取响应。 如果超过此值，则无法发送消息。 默认值为60秒。<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 用于定义从个性化URL下载并附加到电子邮件的图像允许的最大大小（以字节为单位）。 默认值为100,000字节(100 KB)。 发送验证并下载图像以处理电子邮件时，如果图像大小超过此值，或者存在下载问题，则投放日志中将显示错误，验证投放将失败。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 允许您在电子邮件或事务性电子邮件模板中设置最大附件数。 如果超过此值，则在投放分析日志中或发布事务性电子邮件模板时，将显示警告。 默认值为1个附件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 分析期间的最大重试次数。<br /> </td> 
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
   <td> 如果用户留空，则在用于电子邮件投放的实例级别使用默认的“error”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 如果用户留空，则在用于电子邮件投放的实例级别使用默认的“发件人”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 如果用户留空，则在用于电子邮件投放的实例级别使用默认的“回复”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 客户的公用名称。 用于向收件人显示的某些警告消息中。<br /> “您收到此消息是因为您与‘组织’或关联公司有联系。 不再接收来自“组织”的消息<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 如果用户留空，则在用于电子邮件投放的实例级别使用默认的“发件人”电子邮件标签。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 如果用户留空，则在用于电子邮件投放的实例级别使用默认的“回复”电子邮件标签。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 电子邮件两次重试之间的时段（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 电子邮件的重试周期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 用于计算临时投放的消息权重的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 授权转发电子邮件地址列表（来自入站邮件处理模块）。 地址必须以逗号分隔（或*表示允许全部使用）。 例如xyz@abc.com、pqr@abc.com。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> “lineImage”servlet中用于编码URL的AES键（LINE渠道）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 在渠道“电子邮件”（用作默认值） ：对于在将收件人隔离之前发送期间出现的SOFT错误，接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignalErrorDelay</span> <br /> </td> 
   <td> 渠道“电子邮件”（用作默认值） ：自上次引用的SOFT错误以来，在考虑新的SOFT错误之前的最短逗留时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 在渠道“移动设备”上：对于在将收件人隔离之前发送的软错误，接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignalErrorDelay</span> <br /> </td> 
   <td> 渠道“移动” ：自上次引用的SOFT错误以来，在考虑新的SOFT错误之前的最短逗留时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 允许指定最大时段（以小时为单位）以限制每次执行同步工作流时恢复的broadlog的数量。</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing会话中可并行运行的最大调用数（默认为3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 自定义延迟（以分钟为单位），超过该时间后，投放将被视为“延迟”，默认为30分钟。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>此选项由 <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationmgt</a></span> 技术工作流。</p>利用此功能，可定义天数，超过该天数后，状态不一致的投放将从运行的投放计数中排除。</p><p>默认情况下，该值设置为“7”，这意味着将排除超过7天的不一致投放。</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 发件人地址的第1行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> 发件人地址的第3行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> 发件人地址的第4行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> 发件人地址的第6行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 发件人地址的第7行。<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 镜像页面服务器的URL（默认情况下，应与NmsTracking_ServerUrl相同）。<br /> 如果未在路由定义中指定URL，则它是电子邮件投放的默认值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 已发送SMS消息的参数：发送到SMS网关的信息以指示消息的优先级。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> 发送短信消息时的重试次数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> 执行短信消息重试的时段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> 上次合并日期 <span class="uicontrol">NmsUserAgent</span> 统计数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 包含Web区段及其状态的选项的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> 启用/禁用对Code128的特殊字符的支持。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 电子邮件地址的有效字符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 添加具有“0”值的此选项以禁用投放的XML代码的版本(右键单击/ <span class="uicontrol">编辑XML源</span> 或 <span class="uicontrol">CTRL + F4</span> 快捷键)。<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

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
   <td> <span class="uicontrol">NcmResourcesDir</span> <br /> </td> 
   <td> 在Adobe Campaign客户端控制台中发布资源的位置。 请参阅 <a href="../../delivery/using/formatting.md#image-referencing">本节</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourcesDirPreview</span> <br /> </td> 
   <td> 在Adobe Campaign客户端控制台中用于预览的资源位置。 请参阅 <a href="../../delivery/using/formatting.md#image-referencing">本节</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 上载期间跳过的图像的URL掩码列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 图像上传的配置。 该值可以为无/跟踪/脚本/列表（可以由运算符的可选设置覆盖）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 服务器上要存储图像的文件夹。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 用于显示徽标的空间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 出版物的根文件夹。<br /> 有关HTML和文本内容生成的详细信息，请参阅 <a href="../../delivery/using/using-a-content-template.md">本节</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 用于定义存储投放中使用的图像的服务器，以便浏览器获取这些图像。<br /> 对于内部版本&lt;= 5098，我们使用已上传到实例的图像的URL。<br /> 对于版本号&gt; 5098的内部版本，我们改用投放的公共URL或 <span class="uicontrol">XtkFileRes_Public_URL</span> 选项的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> 允许您配置用于图像上传的实例名称。<br /> </td> 
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
   <td> 投放在线资源的默认有效期（秒）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 公共资源文件的新URL。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 活动与工作流管理 {#campaign-e-workflow-management}

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
   <td> 显示此月数的营销历史记录。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 营销活动的默认有效期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> 由operationMgt工作流启动的一次可处理的最大投放/工作流/假设验证/模拟作业数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 允许您监视 <a href="../../workflow/using/about-technical-workflows.md">operationmgt</a> 技术工作流执行。 激活后（值为“1”），执行信息会记录到工作流审核日志中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 在计划模式下定位和提取条件的时间段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 受影响的记录数，之后将自动重新计算表统计信息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 徽标将显示在导出的报告的右上角。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 检查暂停的工作流之间等待的天数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 通过输入“1”作为值，由操作的所有者激活投放验证。 要停用此选项，请输入“0”。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> 要在工作流活动“营销资源通知”中加载的其他JS库。<br /> </td> 
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
   <td> <span class="uicontrol">RestrictEditingOOTBSchema</span> <br /> </td> 
   <td> （从21.1.3版本开始）如果选择1（默认值），则此选项将禁用内置架构的版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> （从21.1.3版本开始）如果选择1（默认值），则此选项将禁用内置JavaScript代码的版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> （安装兼容模式：内部版本&gt;6000）激活时（值为“1”），此选项允许使用数据库中存储的旧密码连接到外部帐户或实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 此密钥用于加密数据库中的大多数口令。 （外部帐户、LDAP密码……）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 如果选择1，则此选项允许在JavaScript中进行privilegeEscalation。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 如果选择1，则此选项会在文件下载期间（通过fileDownload.jsp）禁用ACL控件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 如果选择1，则此选项将在Javascript中禁用文件沙盒。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 如果设置为“true”，则授权非管理员操作员通过部署向导更新xtkOption值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 如果选择1，则此选项允许使用decryptString解密某些密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 输入“1”值以跟踪在mData中删除带有审核记录信息的元素的情况，方法是先修改其“修改者”字段，然后再删除记录。<br /> </td> 
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
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> 要个性化JavaScript库以丰富事件。 必须包含这两个函数的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">extrendsRtEvents(aiEventId)；</span> ：丰富并保存数据库中的事件(其中 <span class="uicontrol">aiEventId</span> 对应于已处理的实时事件表)。</p> </li> 
     <li> <p> <span class="uicontrol">extrendsBatchEvents(aiEventId)；</span> ：丰富并保存数据库中的事件(其中 <span class="uicontrol">aiEventId</span> 对应于已处理的批处理事件的ID表)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 上次通过投放日志更新事件状态的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript库将针对路由事件进行个性化。 必须包含这两个函数的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId)；</span> ：返回选定用于处理实时事件的事务型消息的内部名称，其中 <span class="uicontrol">iEventId</span> 对应于已处理的实时事件的ID)。</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId)；</span> ：返回选定用于处理批处理事件的事务型消息的内部名称(其中 <span class="uicontrol">iEventId</span> 对应于已处理的批处理事件的ID)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 实时事件的平均发送时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 实时事件的平均发送时间的警告阈值。<br /> </td> 
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
   <td> 平均已排队实时事件数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 实时事件的平均排队时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 实时事件的平均排队时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 平均已排队实时事件数的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> 实时事件的处理错误的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> 实时事件的处理错误的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> 最大已排队实时事件数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 最大已排队实时事件数的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 已排队实时事件的最小数目的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 最小已排队实时事件数的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 待处理实时事件队列的严重情况之前的阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 待处理实时事件队列的警告前阈值。<br /> </td> 
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
   <td> 事件路由的重新分组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> 更新RtEvent状态的指针（检索数据之前的截止日期）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 用于发送欢迎消息的Message Center服务器URL（LINE通道）。<br /> </td> 
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
   <td> 定义上次运行清理过程的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义延迟，超过此延迟将从数据库中清除broadlog。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义延迟，在此之后将从数据库中擦除事件历史记录。</p><p>
   在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义从数据库中擦除事件之后的延迟。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义延迟，在此之后将从数据库中擦除事件统计信息。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义延迟，建议将在此延迟之后从数据库中清除。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除隔离的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>可让您定义延迟，过了此延迟后，循环投放将从数据库中清除。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义延迟，之后会从数据库中清除拒绝项。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义延迟，跟踪日志将在此延迟之后从数据库中清除。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义延迟，跟踪统计信息将在此延迟之后从数据库中清除。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义从数据库中拭除访客之后的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义延迟，在此之后将从数据库中擦除工作流结果。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，应以秒为单位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL数据仓库连接器选项。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>允许您根据以下潜在值影响所有工作流和PostgreSQL数据库查询的无条件停止行为：<ul>
    <li><p>0 — 默认值：停止工作流进程，对数据库没有影响<p></li>
    <li><p>1 - pg_cancel_backend：停止工作流进程并取消数据库中的查询<p></li>
    <li><p>2 - pg_terminate_backend：停止工作流进程并终止数据库中的查询<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> 用于包含Adobe Campaign ootb表数据的表空间的名称。<br />请参阅 <a href="../../installation/using/creating-and-configuring-the-database.md">创建和配置数据库</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> 用于包含Adobe Campaign ootb表索引的表空间的名称。<br />请参阅 <a href="../../installation/using/creating-and-configuring-the-database.md">创建和配置数据库</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> 用于包含Adobe Campaign工作表数据的表空间的名称。<br />请参阅 <a href="../../installation/using/creating-and-configuring-the-database.md">创建和配置数据库</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> 用于包含Adobe Campaign工作表索引的表空间的名称。<br />请参阅 <a href="../../installation/using/creating-and-configuring-the-database.md">创建和配置数据库</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 允许您为Microsoft SQL Server上的工作表配置单独的数据库，以优化备份和复制。 该选项对应于临时数据库的名称：如果指定，将在此数据库中写入工作表。 示例： 'tempdb.dbo.' （请注意，名称必须以点结尾）。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">了解更多</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign实例的时区。 请参阅 <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">配置</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> 是否使用NChar定义数据库的字符串字段？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> 数据库的“datetime”字段是否存储时区信息？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> 数据库的ID。 对于Unicode数据库，以“u”开头。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 添加到自动生成的内部名称的前缀。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> 查询在xtk：schema和xtk：srcSchema上返回的最大结果数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 在此时间之后创建的所有自定义架构（具有autopk="true"并且没有属性"pkSequence"）都将获得自动生成的序列"auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       序列(_S)。 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 在迁移期间，将根据新版本标准自动重新组织树结构。<br /> 使用此选项可禁用导航树的自动迁移。 如果您使用它，则在迁移后，您将必须删除过时的文件夹，添加新文件夹并运行所有必要的检查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">数据类型：</span> 整数</p> </li> 
     <li> <p> <span class="uicontrol">值（文本）</span> ：1 </p> </li> 
    </ul> 仅当现成的导航树发生了太多更改时，才应使用此选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> 的上次处理日期 <span class="uicontrol">NmsEmailErrorStat</span> 表格清理。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 有关升级后发生错误的信息，请遵循以下语法：<br /> <strong>{内部版本号}：{mode： pre/post/...}：{发生错误的“lessThan”/“greaterOrEquelThan”+子步骤}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 输入“1”值，以便不通过清除工作流执行统计更新。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 集成 {#integration}

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
   <td> 可在Adobe Campaign中使用的AEM资源类型。 值必须以逗号分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> 允许您配置Experience Cloud触发器。 数据类型是“长文本”，必须采用JSON格式。 请参阅 <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">如何将Experience Cloud触发器与Adobe Campaign Classic结合使用</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> 通过CRM连接器从第三方系统导入数据时，可使用此选项。 启用选项可让您仅收集自上次导入以来修改的对象。 此选项必须手动创建并填充，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">内部名称</span> ： LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（字段）</span> ：上次导入的日期，格式为yyyy/MM/dd hh:mm:ss格式。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 用于集成的Adobe Target服务器。 默认情况下已选中此选项。 此值对应于Adobe Target Domain Server，后跟值/m2。 例如：tt.omtrdc.net/m2。<br /> 请参阅 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">本节</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target组织名称。 此值对应于Adobe Target客户端的名称。<br /> 请参阅 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">本节</a>.<br /> </td> 
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
   <td> teradata连接器选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> 配置单元连接器选项。<br /> </td> 
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
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> 每个SQL事务更新的优惠券数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [建议架构] + "_" + extAccountSource。@executionInstanceId + [建议架构] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> “+ [建议架构] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 同步工作流跟踪。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 启用/禁用异步建议写入（“0”表示禁用，“1”表示启用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> 执行实例标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> 发送计费报告时使用的客户标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> 访问应用程序服务器的内部基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 上次升级前的AC实例内部版本号。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> 公共Web应用程序服务器的基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> 允许您在迁移后继续使用旧的未声明的SQL函数。 由于此选项会带来安全风险，因此我们强烈建议不要使用此选项。<br /> </td> 
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
   <td> 允许您激活跟踪的选项。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> 跟踪的URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 用于定义跟踪服务器的外部帐户。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 允许您在跟踪服务器上定义实例名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> 上次使用新数据合并跟踪信息的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> 打开URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> 跟踪服务器的密码<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> 指针会跟踪通过其ID和日期处理的最后一个消息事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> 前端跟踪服务器的安全URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 前端跟踪服务器的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> 用于联系跟踪服务器的URL列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> 浏览器标识规则集。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> 用于计算Web跟踪标记的脚本。<br /> </td> 
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
   <td> 如果选择了选项1，则必须在第二步中在界面中手动确认删除。 否则，将在不确认的情况下删除数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 请求等待删除确认与请求之间的延迟已被取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 处理/删除隐私请求时允许的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> 在队列中创建请求之间的延迟并删除请求数据。<br /> </td> 
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
   <td> 启用LDAP服务器以用于对用户进行身份验证并向用户提供授权。<br /> </td> 
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
   <td> 在Adobe Campaign中启用自动创建操作员和权限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 基于登录的LDAP DN计算公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 在目录中启用DN搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 搜索基础。<br /> </td> 
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
   <td> 在Adobe Campaign中启用授权和组从LDAP目录到已命名权限的同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 包含授权名称的LDAP属性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 搜索基础。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 搜索筛选条件以查找用户授权。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> 用于从LDAP授权中提取Adobe Campaign权限名称的表达式。<br /> </td> 
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

## Web窗体 {#web-forms}

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
   <td> 值设置为1将允许向详细信息表单添加滚动条。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> 在“其他服务器”模式下用于Web窗体失效的实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> 在“其他服务器”模式下用于Web窗体失效的实例的密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 允许您指定Web窗体失效模式的选项：默认情况下为本地，如果选项为“跟踪”，则使用跟踪服务器，并使用带有“其他服务器”选项的个性化列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> 为Web窗体失效而联系的服务器的个性化地址列表（“其他服务器”模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>
