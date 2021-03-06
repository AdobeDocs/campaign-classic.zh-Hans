---
product: campaign
title: 连接失败
description: 连接失败
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 4%

---

# 连接失败{#failure-to-connect}

![](../../assets/v7-only.svg)

出现连接问题的原因可能有多种，具体取决于不同的上下文。

您可以尝试以下测试，如果连接故障仍然存在，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>检查<br /> </th> 
<th>解决方法<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您的计算机是否可以访问Internet?</td> 
<td>检查是否可以连接到Internet上的网站（例如）。 如果无法连接，则计算机上出现问题。 请与系统管理员联系。</td>
</tr>
<tr> 
<td>能否通过其他服务连接到托管Adobe Campaign的服务器？</td> 
<td>通过SSH或任何其他方式连接到服务器。 如果这不可能，则您的主机公司遇到问题。 请联系系统管理员。</td>
</tr>
<tr> 
<td>Web服务器是否做出响应？</td> 
<td>使用Web浏览器连接到Adobe Campaign服务器访问URL: <b>http(s):// &lt;urlserver&gt;</b>. 如果它未响应，则计算机上将停止Web服务器。 请与主机公司的系统管理员联系以重新启动该服务。</td>
</tr>
<tr> 
<td>Adobe Campaign是否已正确集成？</td> 
<td>登录到： <b>http(s)://&lt;urlserver&gt;/r/test</b> URL。 服务器应返回以下类型的消息： &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
如果未获得此结果，请检查Web服务器配置中是否考虑了集成。:MM:</td>
</tr>
<tr> 
<td>连接到以下URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果获取Tomcat Java错误，请检查JAVA集成是否正确执行。 它集成在文件[应用程序路径]/nl6/customer.sh中</td>
</tr>
<tr> 
<td>连接到以下URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果获取空白页面，请检查Adobe Campaign Web模块是否已启动。 命令nlserver转储应返回DD/MM/YYYY的Adobe Campaign Classic(7.X YY.R内部版本XXX@SHA1)的Application Server。 如果没有，请使用命令nlserver start web重新启动模块</td>
</tr>
<tr>
<td>检查安全区的常规配置。</td>
<td>有关配置安全区的更多信息，请参阅 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>此部分。</a></td>
</tr>
<tr>
<td>nlserver pdump命令返回 <b>无任务</b></td>
<td>必须重新启动整个Adobe Campaign应用程序。 要实现此目的，请使用以下命令： <b>nlserver watkdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
