---
product: campaign
title: 配置Campaign选项
description: 了解如何配置Campaign选项
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: b99de2a47bac08578d6e660595eb14c0858bf9fd
workflow-type: tm+mt
source-wordcount: '3961'
ht-degree: 0%

---

# Campaign Classic 选项列表{#configuring-campaign-options}

**[!UICONTROL Administration / Platform / Options]**&#x200B;节点允许您配置Adobe Campaign选项。 其中一些是安装Campaign时内置的，而另一些则可在需要时手动添加。 可用选项因随实例一起安装的包而异。

>[!CAUTION]
>
>* 此页面中未列出的选项仅限内部，且&#x200B;**不得修改**。
   >
   >
* 修改或更新Adobe Campaign选项只能由专家用户执行。


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
   <td> 从可交付性实例中检索到的最后一个broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 发送到可交付性实例的上次broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 投放报表标识符。 请联系支持人员以获取您的标识符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 要将测试地址用于收件箱呈现的架构列表。 （元素名称之间用逗号分隔）例如：custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> Enhanced MTA将向其发送已发送电子邮件原始副本的密件抄送电子邮件地址。<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 如果指定了特定的运算符或一组运算符以在投放的属性中开始投放，则允许负责投放的运算符确认发送。</p><p> 为此，请输入“1”作为值以激活选项。 要取消激活此选项，请输入“0”。</p><p> 然后，发送确认流程将起默认作用：只有在投放属性（或管理员）中为发送指定的操作员或操作员组才能确认和执行发送。 请参阅<a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">此小节</a>。</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:recipient)对话。<br /> 选项值必须与与外部收件人表匹配的架构的名称相对应。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 最小收件人数，以便将投放视为计费报表中的主投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 新模板的默认路由服务提供程序。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 一次为投放创建的广泛日志数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 按事务插入日志(broadLogs)（在表中）：每批要处理的行数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 分析中间源投放时对投放部分的分组大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 投放的默认投放期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 用于标准化投放消息的正则表达式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 在值中输入“1”可排除不再希望与之联系的收件人。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 在值中输入“1”可自动忽略双重。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 用于定义回复消息时使用的错误地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 用于定义发送消息时使用的发件人地址的语法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 用于定义在检索从个性化URL下载并附加到电子邮件的图像时从服务器获取响应的超时限制（以秒为单位）。 如果超出此值，则无法发送消息。 默认值为60秒。<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 用于定义允许从个性化URL下载并附加到电子邮件的图像的最大大小（以字节为单位）。 默认值为100,000字节。 在发送校样并下载图像以处理电子邮件时，如果图像大小超过此值或出现下载问题，则投放日志中将显示错误，并且校样投放将失败。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 允许您在电子邮件或事务型电子邮件模板中设置最大数量的附件。 如果超出此值，则投放分析日志或发布事务型电子邮件模板时将显示警告。 默认值为1个附件。<br /> </td> 
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
   <td> 用户留空时，实例级别用于电子邮件投放的默认“error”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 如果用户将留空，则在实例级别使用默认的“发件人”电子邮件地址进行电子邮件投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 用户留空时，实例级别用于电子邮件投放的默认“回复”电子邮件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 客户的通用名称。 用于向收件人显示的一些警告消息。<br /> “您之所以收到这条消息，是因为您已与*****或一家关联公司联系。不再从*****"接收消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 如果用户将留空，则在实例级别使用默认的“发件人”电子邮件标签进行电子邮件投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 用户留空时，实例级别用于电子邮件投放的默认“回复”电子邮件标签。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 电子邮件两次重试之间的间隔时间（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 电子邮件的重试时间段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 用于计算临时投放消息权重的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 授权转发电子邮件地址的列表（来自入站邮件处理模块）。 地址必须用逗号分隔（或*才允许所有地址）。 例如xyz@abc.com,pqr@abc.com。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> 在“lineImage”Servlet中使用AES键对URL（LINE通道）进行编码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 在渠道“电子邮件”（用作默认设置）上：在将收件人隔离之前，发送期间SOFT错误所接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailImporigentErrorDelay</span> <br /> </td> 
   <td> 在渠道“电子邮件”（用作默认设置）上：在考虑新的SOFT错误之前，自上次引用的SOFT错误以来所花费的最短时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 在渠道“移动”上：在将收件人隔离之前，发送期间SOFT错误所接受的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileAmprigentErrorDelay</span> <br /> </td> 
   <td> 在渠道“移动”上：在考虑新的SOFT错误之前，自上次引用的SOFT错误以来所花费的最短时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 允许将最长时间段（以小时为单位）指定为，以限制每次执行同步工作流时恢复的广播日志数量。</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> 中间源会话中可并行运行的最大调用数（默认为3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 自定义延迟（以分钟为单位），在该延迟后，投放被视为“延迟”，默认为30分钟。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>在计数正在运行的投放数量时， <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span>技术工作流会使用此选项。</p>利用该功能，可定义在运行投放计数中排除状态不一致的投放的天数。</p><p>默认情况下，该值设置为“7”，这表示将排除7天以前不一致的投放。</p></td> 
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
   <td> 镜像页面服务器的URL（默认情况下，应与NmsTracking_ServerUrl相同）。<br /> 当路由定义中未指定URL时，它是电子邮件投放的默认值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 已发送短信消息的参数：发送给短信网关以指示消息优先级的信息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> 发送短信消息时的重试次数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> 执行短信消息重试的时间段。<br /> </td> 
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
   <td> 启用/禁用对代码128特殊字符的支持。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 电子邮件地址的有效字符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 将此选项与"0"值一起添加，以禁用投放XML代码的编辑（右键单击/ <span class="uicontrol">编辑XML源</span>或<span class="uicontrol">CTRL + F4</span>快捷键）。<br /> </td> 
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
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> 在Adobe Campaign客户端控制台中要发布的资源的位置。 请参阅<a href="../../delivery/using/formatting.md#image-referencing">此小节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourcesDirPreview</span> <br /> </td> 
   <td> 在Adobe Campaign客户端控制台中进行预览的资源位置。 请参阅<a href="../../delivery/using/formatting.md#image-referencing">此小节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 上传期间跳过的图像的URL掩码列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 图像上传的配置。 这些值可以是无/跟踪/脚本/列表（可以由运算符的可选设置来覆盖）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 存储服务器上映像的文件夹。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 显示徽标的空间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 发布的根文件夹。<br /> 有关HTML和文本内容生成的更多信息，请参阅 <a href="../../delivery/using/using-a-content-template.md">此章节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 允许您定义存储投放中使用的图像的服务器，以便浏览器获取这些图像。<br /> 对于内部版本  &lt;&gt;<br /> 对于版本&gt; 5098，我们改为使用投放的公共URL或 <span class="uicontrol">XtkFileRes_Public_</span> URL选项的URL。<br /> </td> 
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
   <td> 用于配置用于图像上传的媒体URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> 投放在线资源的默认有效期（以秒为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 公共资源文件的新URL。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 营销活动和工作流管理{#campaign-e-workflow-management}

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
   <td> 一次可由operationMgt工作流启动的投放/工作流/假设/模拟作业的最大数量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 用于监视<a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>技术工作流的执行情况。 激活后（值“1”），执行信息将记录在工作流审核日志中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 在计划模式下定位和提取条件的时间段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 自动重新计算表统计信息之后受影响的记录数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 要在导出的报表的右上角显示的徽标。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 检查已暂停的工作流之间需要等待的天数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 通过输入“1”作为值，激活操作所有者对投放的验证。 要取消激活此选项，请输入"0"。<br /> </td> 
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
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (安装兼容模式：build&gt;6000)激活（值“1”）后，此选项允许使用存储在数据库中的旧密码连接到外部帐户或实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 此密钥用于加密数据库中的大多数密码。 （外部帐户， LDAP密码……）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 如果选择1，则此选项将允许Javascript中的特权升级。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 如果选择1，则此选项在文件下载期间（通过fileDownload.jsp）禁用ACL控件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 如果选择1，则此选项将禁用Javascript中的文件沙盒。<br /> </td> 
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
   <td> 输入“1”值，以在mData中通过修改其“修改者”字段来跟踪删除包含审核跟踪信息的元素。<br /> </td> 
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
   <td> <span class="uicontrol">MC_ExcressionCustomJs</span> <br /> </td> 
   <td> JavaScript库进行个性化，以扩充事件。 必须包含以下两个函数的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">mythredRtEvents(aiEventId);</span> :丰富并保存数据库中的事件( <span class="uicontrol"></span> 其中aiEventId对应于已处理的实时事件表)。</p> </li> 
     <li> <p> <span class="uicontrol">methringBatchEvents(aiEventId);</span> :丰富并保存数据库中的事件(其中 <span class="uicontrol"></span> aiEventId对应于已处理批量事件的ID表)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 通过投放日志更新上次事件状态的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 要为路由事件进行个性化设置的JavaScript库。 必须包含以下两个函数的实现：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> :返回选定用于处理实时事件的事务型消息的内部名称(其 <span class="uicontrol"></span> 中iEventId对应于所处理实时事件的ID)。</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> :返回选定用于处理批处理事件的事务型消息的内部名称(其 <span class="uicontrol"></span> 中iEventId对应于已处理批处理事件的ID)。</p> </li> 
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
   <td> 实时事件平均处理时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 实时事件平均处理时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 已排队实时事件的平均数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 实时事件平均排队时间的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 实时事件平均排队时间的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 已排队实时事件的平均数的警告阈值。<br /> </td> 
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
   <td> 已排队实时事件的最大数的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 已排队实时事件的最大数量的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 已排队实时事件的最小数量的警报阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 已排队实时事件的最小数量的警告阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 挂起实时事件队列的临界条件之前的阈值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 挂起实时事件队列警告前的阈值。<br /> </td> 
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
   <td> 更新RtEvent状态的指针（在检索数据之前的最后一个日期）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 消息中心服务器URL，用于发送欢迎消息（LINE渠道）。<br /> </td> 
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
   <td> 定义上次运行清理进程的时间。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除broadlog的延迟。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义从数据库中擦除事件历史记录的延迟。</p><p>
   在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义事件从数据库中擦除后的延迟。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义从数据库中擦除事件统计信息的延迟。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_CompationPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义从数据库中擦除命题后的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除隔离的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除循环投放的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除拒绝的延迟。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除跟踪日志的延迟。</p><p>在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 用于定义从数据库中擦除跟踪统计信息的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义访客从数据库中擦除后的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>用于定义从数据库中擦除工作流结果后的延迟。</p><p> 在界面中修改延迟后，将自动创建此选项。 如果修改选项列表中的值，该值应以秒为单位。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL数据仓库连接器选项。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>允许您根据以下潜在值影响所有工作流和PostgreSQL数据库查询上的无条件停止行为：<ul>
    <li><p>0 — 默认：停止工作流进程，对数据库没有影响<p></li>
    <li><p>1 - pg_cancel_backend:停止工作流进程并取消数据库中的查询<p></li>
    <li><p>2 - pg_terminate_backend:停止工作流进程并终止数据库中的查询<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> 要包含Adobe Campaign ootb表数据的表空间的名称。<br />请参 <a href="../../installation/using/creating-and-configuring-the-database.md">阅创建和配置数据库</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> 要包含Adobe Campaign ootb表索引的表空间的名称。<br />请参 <a href="../../installation/using/creating-and-configuring-the-database.md">阅创建和配置数据库</a>。</td> 
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
   <td> 用于为Microsoft SQL Server上的工作表配置单独的数据库，以优化备份和复制。 选项对应于临时数据库的名称：如果指定，将在此数据库中写入工作表。 示例：'tempdb.dbo' （请注意，名称必须以圆点结尾）。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">阅读更多</a> <br /> </td> 
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
   <td> 数据库的ID。 对于Unicode数据库，以“u”开头。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 为自动生成的内部名称添加前缀。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> 查询在xtk:schema和xtk:srcSchema.<br />上返回的结果的最大数量 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 在此之后创建的所有自定义架构（使用autopk="true"且不使用属性"pkSequence"）都将获得自动生成的序列"auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq。 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 在迁移过程中，会根据新版本标准自动重新组织树结构。<br /> 利用此选项，可禁用导航树的自动迁移。如果您使用它，则在迁移后，必须删除过时的文件夹，添加新文件夹并运行所有必要的检查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">数据类型：</span> 整数</p> </li> 
     <li> <p> <span class="uicontrol">值（文本）</span> :1 </p> </li> 
    </ul> 仅当现成的导航树发生了太多更改时，才应使用此选项。<br /> 有关更多信息，请参阅 <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">此章节</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> <span class="uicontrol">NmsEmailErrorStat</span>表清理的上次处理日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 有关Postupgrade中发生的错误的信息，请遵循以下语法：<br /> <strong>{内部版本号}:{mode:pre/post/...}:{发生错误的'lessThan'/'greaterOrEquelThan' +子步骤}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 输入“1”值，以便不会通过清理工作流执行统计信息更新。<br /> </td> 
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
   <td> 可在Adobe Campaign中使用的AEM资源类型。 值必须用逗号分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> 允许您配置Experience Cloud触发器。 数据类型为“长文本”，且必须为JSON格式。 请参阅<a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">如何将Experience Cloud触发器与Adobe Campaign Classic一起使用</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;&gt;_&lt;&gt;</span> <br /> </td> 
   <td> 通过CRM连接器从第三方系统导入数据时，会使用此选项。 启用选项后，您只能收集自上次导入以来修改的对象。 必须手动创建并填充此选项，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">内部名称</span> :LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（字段）</span> :上次导入的日期，格式为yyyy/MM/dd hh:mm:ss。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 用于集成的Adobe Target服务器。 默认情况下，此选项已被选中。 此值对应于Adobe Target域服务器，后跟值/m2。 例如：tt.omtrdc.net/m2。<br /> 请参 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">阅此部分</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target组织名称。 此值对应于Adobe Target客户端的名称。<br /> 请参 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">阅此部分</a>。<br /> </td> 
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

## 选件 {#offers}

<table> 
 <thead> 
  <tr> 
   <th> 选项名称 </th> 
   <th> 说明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoopuns_MaxPerTransac</span> <br /> </td> 
   <td> 每个SQL事务更新的优惠券数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCampationSynchControl_</span> <br /> </td> 
   <td> '+ [建议的架构] + "_" + extAccountSource。@executionInstanceId + [建议的架构] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCampositionSynchExec_</span> <br /> </td> 
   <td> '+ [建议的架构] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget。@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 同步工作流跟踪。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 启用/禁用异步建议写入（“0”禁用，“1”启用）。<br /> </td> 
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
   <td> 允许您在迁移后继续使用旧的未声明的SQL函数。 由于此选项会带来安全风险，我们强烈建议不要使用此选项。<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> 跟踪的URL计算脚本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 用于定义跟踪服务器的外部帐户。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 用于在跟踪服务器上定义实例名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> 上次使用新数据合并跟踪信息时。<br /> </td> 
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
   <td> 额面跟踪服务器的安全URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 额面跟踪服务器的URL。<br /> </td> 
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
   <td> 为Web跟踪管理而设计的虚拟投放的名称。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> 用于定义Web跟踪模式。<br /> </td> 
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
   <td> 如果选择了选项1，则必须在第二步的界面中手动确认删除。 否则，数据将在未经确认的情况下删除。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 请求之间等待删除确认的延迟，请求被取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 处理/删除隐私请求时允许的最大错误数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> 启用LDAP服务器以用于验证用户并向用户提供授权。<br /> </td> 
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
   <td> 在Adobe Campaign中启用自动创建运算符和权限。<br /> </td> 
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
   <td> 搜索基数。<br /> </td> 
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
   <td> 启用从LDAP目录到Adobe Campaign中命名权限的授权和组同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 包含授权名称的LDAP属性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 搜索基数。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 搜索用户授权的筛选器。<br /> </td> 
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
   <td> 值设置为1后，将允许在详细信息表单中添加滚动条。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> 用于在“其他服务器”模式下使Web窗体失效的实例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> 用于在“其他服务器”模式下使Web窗体失效的实例的密码。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 用于指定Web窗体失效模式的选项：默认情况下，如果选项为“tracking”，则使用跟踪服务器，并将个性化列表与“其他服务器”选项一起使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> 要联系以进行Web窗体失效的服务器的个性化地址列表（“其他服务器”模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>
