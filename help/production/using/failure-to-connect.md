---
solution: Campaign Classic
product: campaign
title: 连接失败
description: 连接失败
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: cb6a2247e3b7617511aecf3d2d19985af0216494
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---


# 连接失败{#failure-to-connect}

连接问题的原因可能是多个，并取决于各种上下文。

您可以尝试以下测试，如果连接故障仍然存在，请与Adobe Campaign支 **持联系**。



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
   <td>使用Web浏览器连接到Adobe Campaign服务器访问URL:**`http(s):// <urlserver>`**. 如果它没有响应，则计算机上停止Web服务器。 请与主机公司的系统管理员联系以重新启动该服务。</td>
  </tr>
  <tr> 
   <td>Adobe Campaign是否已正确集成？</td> 
   <td>登录到：**`http(s)://<urlserver>/r/test`** URL。 服务器应返回以下类型的消息

    &quot;
    &lt;redir status=&#39;OK&#39; date=&#39;YYYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &quot;
    
    如果您未获得此结果，请检查已考虑集成的Web服务器配置。&lt;/td>
</tr>
  <tr> 
   <td>Adobe CampaignWeb模块是否已启动？</td> 
   <td>
   连接到以下URL:**`http(s)://<URLSERVER>/nl/jsp/logon.jsp`** *如果您获得Tomcat Java错误：

    JAVA集成是否正确执行？ Adobe Campaign需要SUN JDK。
    
    它集成在文件**`[应用程序路径]`/nl6/customer.sh*
    
    **中，如果您获得空白页面：是
    
    否已启动Adobe CampaignWeb模块？ 您应获得
    
    DD/MM/YYYY
    [...]web@default(27515)- 55.2 Mb
    [...)*的“Adobe Campaign Classic的Application Server(7.X YY.R build XXX@SHA1)”
    
    
    
    
    
    
    
    
    
    的“nlserver pdumpHH:MM:SS”否则，请使用以下命令重新启动它：“服务器开始Web”&lt;/td>
</tr>
  <tr>
  	<td>检查安全区域的常规配置。</td>
  	<td>有关配置安全区域的详细信息，请参阅[本节](../../installation/using/configuring-campaign-server.md#defining-security-zones)</td>
  </tr>
 </tbody> 
</table>
