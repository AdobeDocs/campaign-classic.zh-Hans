---
solution: Campaign Classic
product: campaign
title: 连接失败
description: 连接失败
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 85fae38f864b031f069058dae79ce6753dc4bf03
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# 连接失败{#failure-to-connect}

连接问题的原因可能是多个，并取决于各种上下文。

您可以尝试以下测试，如果连接故障仍然存在，请与&#x200B;**Adobe Campaign支持**&#x200B;联系。



<table> 
<thead> 
<tr> 
<th>检查<br /> </th> 
<th>解决方案<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您是否可以从计算机访问Internet?</td> 
<td>检查是否可以连接到Internet上的网站（例如）。 如果无法连接，则问题出在您的计算机上。 与系统管理员联系。</td>
</tr>
<tr> 
<td>是否可以通过其他服务连接到承载Adobe Campaign的服务器？</td> 
<td>通过SSH或任何其他方式连接到服务器。 如果这不可能，则主机公司有问题。 与系统管理员联系。</td>
</tr>
<tr> 
<td>Web服务器是否响应？</td> 
<td>使用Web浏览器连接到Adobe Campaign服务器访问URL:<b>http(s):// &lt;urlserver&gt;</b>。 如果它没有响应，则计算机上停止Web服务器。 请与主机公司的系统管理员联系以重新启动该服务。</td>
</tr>
<tr> 
<td>Adobe Campaign是否已正确集成？</td> 
<td>登录到：<b>http(s)://&lt;urlserver&gt;/r/test</b> URL。 服务器应返回以下类型的消息：&lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;
如果未获得此结果，请检查Web服务器配置中是否考虑了集成。</td>
</tr>
<tr> 
<td>连接到以下URL:<b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>如果获得Tomcat Java错误，请检查JAVA集成是否正确执行。 它集成在文件[应用程序路径]/nl6/customer.sh中</td>
</tr>
<tr> 
<td>连接到以下URL:<b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>如果获得空白页面，请检查Adobe CampaignWeb模块是否已启动。 命令nlserver转储应返回DD/MM/YYYY的Adobe Campaign Classic(7.X YY.R内部版本XXX@SHA1)的应用程序服务器。 如果不是，请使用命令nlserver开始web重新启动模块</td>
</tr>
<tr>
<td>检查安全区域的常规配置。</td>
<td>有关配置安全区域的详细信息，请参阅<a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>此部分。</a></td>
</tr>
<tr>
<td>命令nlserver转储返回<b>没有任务</b></td>
<td>必须重新启动整个Adobe Campaign应用程序。 为此，请使用以下命令：<b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
