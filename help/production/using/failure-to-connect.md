---
product: campaign
title: 连接失败
description: 连接失败
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# 连接失败{#failure-to-connect}



连接问题的原因可能多种多样，并且取决于不同的上下文。

您可以尝试以下测试，如果连接失败仍然存在，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>支票<br /> </th> 
<th>分辨率<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您是否可从计算机访问Internet？</td> 
<td>检查您是否可以连接到Internet上的网站（例如）。 如果无法连接，则问题出现在您的计算机上。 请与系统管理员联系。</td>
</tr>
<tr> 
<td>能否通过其他服务连接到托管Adobe Campaign的服务器？</td> 
<td>通过SSH或任何其他方式连接到服务器。 如果无法执行此操作，则表明您的托管公司存在问题。 联系其系统管理员。</td>
</tr>
<tr> 
<td>Web服务器是否响应？</td> 
<td>使用Web浏览器连接到Adobe Campaign服务器访问URL： <b>http(s)：// &lt;urlserver&gt;</b>. 如果不响应，则计算机上的Web服务器将停止。 请与主机公司的系统管理员联系以重新启动该服务。</td>
</tr>
<tr> 
<td>Adobe Campaign是否已正确集成？</td> 
<td>登录到： <b>http(s)：//&lt;urlserver&gt;/r/test</b> URL。 服务器应返回以下类型的消息： &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
如果没有获得此结果，请检查Web服务器配置，确认集成已考虑在内。:MM:</td>
</tr>
<tr> 
<td>连接到以下URL： <b>http(s)：//&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果您收到Tomcat Java错误，请检查是否正确执行JAVA集成。 它集成在文件[应用程序路径]/nl6/customer.sh中</td>
</tr>
<tr> 
<td>连接到以下URL： <b>http(s)：//&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果获得空白页面，请检查Adobe Campaign Web模块是否已启动。 命令nlserver pdump应返回DD/MM/YYYY的Adobe Campaign Classic Application Server (7.X YY.R内部版本XXX@SHA1)。 如果不能，请使用命令nlserver start web重新启动模块</td>
</tr>
<tr>
<td>检查安全区域的常规配置。</td>
<td>有关配置安全区域的详细信息，请参阅 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>本节。</a></td>
</tr>
<tr>
<td>命令nlserver pdump返回 <b>无任务</b></td>
<td>您必须重新启动整个Adobe Campaign应用程序。 要执行此操作，请使用以下命令： <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
