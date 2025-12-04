---
product: campaign
title: 跟踪入门
description: 了解更多Adobe Campaign中跟踪的一般准则
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# 消息跟踪入门 {#get-started-tracking}

>[!IMPORTANT]
>
>有关同时适用于Campaign Classic v7和Campaign v8的&#x200B;**常规跟踪指南**，请参阅[Campaign v8消息跟踪文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}：
>
>* [配置跟踪的链接](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [配置 URL 跟踪选项](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [跟踪个性化链接](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [访问跟踪日志](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [测试跟踪](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [跟踪报告](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**此页面仅记录特定于Campaign Classic v7的跟踪功能**，主要用于混合部署和内部部署。

## 跟踪功能

### 跟踪配置 {#configure-tracking}

对于Campaign Classic v7 **混合/内部部署**，您需要在使用它之前在实例级别配置跟踪。

>[!NOTE]
>
>对于Campaign v8托管云服务，跟踪配置由Adobe执行。

**工作原理**

在使用跟踪之前，您需要先为实例配置它。 需要在Adobe Campaign应用程序服务器和Web服务器上执行配置。

在Campaign中，有两种类型的跟踪：

* **Web跟踪**：此模式允许您跟踪对网站页面的访问
* **消息跟踪**：此模式允许您跟踪消息投放和收件人行为

在安装期间选择跟踪模式。 对于内部部署，必须在实例级别定义跟踪配置。 [了解详情](../../installation/using/deploying-an-instance.md#operating-principle)

**跟踪服务器**

要配置跟踪，必须声明您的实例并在跟踪服务器中注册。 跟踪服务器用于记录和检索有关收件人单击的URL的信息。

对于内部部署，跟踪服务器通常是运行Adobe Campaign Web应用程序的Web服务器。 必须在实例配置中定义跟踪服务器URL。 [了解详情](../../installation/using/deploying-an-instance.md#tracking-server)

**正在保存跟踪**

配置跟踪并填充URL后，必须注册跟踪服务器。 注册后，Adobe Campaign可以保存跟踪信息，并提供有关跟踪活动的报告和统计信息。

对于内部部署，跟踪信息存储在数据库中，并通过技术工作流进行检索。 **Tracking**&#x200B;技术工作流处理并存储从重定向服务器收集的跟踪数据。 [了解详情](../../installation/using/deploying-an-instance.md#saving-tracking)

### Web应用程序跟踪 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**Web应用程序跟踪特定于Campaign Classic v7**，在Campaign v8中不可用。

**跟踪 Web 应用程序**

您还可以跟踪和测量带有跟踪标记的Web应用程序页面上的访问次数。 此功能可用于所有Web应用程序类型，例如表单和登陆页面。 [了解详情](../../web/using/tracking-a-web-application.md)

**选择退出 Web 应用程序跟踪**

通过选择退出Web应用程序跟踪，您可以停止跟踪选择退出行为跟踪的最终用户的Web行为。 您可以包括在Web应用程序或登陆页中显示横幅的功能，以允许用户选择退出。 [了解详情](../../web/using/web-application-tracking-opt-out.md)

## 跟踪故障排除 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

以下故障排除提示适用于&#x200B;**Campaign Classic v7混合/内部部署**。 某些信息也可能适用于Campaign v8内部部署。 对于Campaign v8托管云服务，请联系您的Adobe代表寻求帮助。

有关Campaign v8中的基本跟踪故障排除步骤，请参阅Campaign v8中的[跟踪故障排除文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}。

### 基本检查 {#basic-checks}

**检查trackinglogd进程是否正在运行**

此进程从IIS/Web服务器共享内存中读取并写入重定向日志。

您可以通过选择实例中的监视选项卡，从主页访问它。 您还可以在实例上执行以下命令： `<user>@<instance>:~$ nlserver pdump`

如果trackinglogd进程未出现在列表中，请在实例上使用以下命令启动它： `<user>@<instance>:~$ nlserver start trackinglogd`

**检查跟踪技术工作流最近是否正在运行**

您可以在文件夹“管理” > “生产” > “技术工作流”中找到“跟踪”技术工作流。

### 高级故障排除 {#advanced-troubleshooting}

+++跟踪工作流失败

>[!NOTE]
>
>仅适用于Windows

损坏的跟踪日志文件……/nl6/var/&lt;instance_name>/redir/log/0x0000日志可以停止跟踪工作流。 要轻松检测损坏的行并删除它们以恢复跟踪工作流，您可以使用以下命令。

**我知道损坏的行位于哪个文件中**

在这种情况下，可以在0x00000000000A0000.log文件中找到损坏的行，但相同的过程可以应用到一组文件 — 一个一个文件。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然后，您可以停止跟踪工作流，删除损坏的行并重新启动工作流。

**我不知道损坏的行位于哪个文件中**

1. 使用以下命令行签入所有跟踪文件。

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 该命令列出了所有损坏的行。 例如：

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在用户代理之前添加了回车符，以便更好地读取，并且不会反映有效的渲染。

1. 运行grep命令以查找相应的文件。

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. 找到带有文件名和行号的错误日志。 例如：

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在用户代理之前添加了回车符，以便更好地读取，并且不反映有效渲染。

然后，您可以停止跟踪工作流，删除损坏的行并重新启动工作流。

+++

+++跟踪链接间歇性失败

在尝试访问跟踪链接时，会显示以下消息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. 访问&lt;redirection_server>/r/test URL并检查请求是否返回了内部版本号和localhost。

1. 检查serverConf.xml文件中用于跟踪服务器的spareServer配置。 此配置应处于重定向模式。

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. 手动检查计算机上是否存在……/nl6/var/&lt;instance_name>/redir/url/&lt;YYYY>目录中的&lt;deliveryID>.xml文件（YYYY表示投放年份）。

1. 手动检查是否在&lt;deliveryID>.xml文件中找到&lt;trackingUrlId>。

1. 检查相关的deliveryID投放中是否手动存在broadlogID。

1. 检查……/nl6/var/&lt;实例名称>/redir/url/year目录中的&lt;deliveryID>.xml文件权限。

   执行用户应具有至少644个权限，以便Apache可以读取跟踪url以将请求的链接重定向。

+++

+++更新NmsTracking_Pointer选项

更新NmsTracking_Pointer选项时，请按照以下步骤操作：

1. 停止跟踪工作流。

1. 停止trackinglog服务。

1. 将NmsTracking_Pointer选项更新为所需的值。

1. 重新启动trackinglogd服务。

1. 重新启动跟踪工作流。

+++

+++跟踪功能不适用于某些WebMail

您可以自定义点击跟踪公式并指定自定义Adobe Analytics跟踪公式。

此类自定义需要谨慎进行，以避免添加额外的换行符。 JavaScript表达式外部存在的所有换行字符都将出现在最终公式中。

跟踪URL中这种额外的换行字符将导致某些webMail（AOL、GMail等）中出现问题。

**第一个示例：**

* 语法不正确

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* 语法正确

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

要了解额外换行符的位置，您可以使用固定字符串STRING替换JavaScript表达式。

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**第二个示例**

* 语法不正确

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* 语法正确

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

要了解额外换行符的位置，您可以使用固定字符串STRING替换JavaScript表达式。

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++跟踪日志检索速度太慢

当实例不直接检索跟踪日志，而是从远程的Adobe Campaign Classic服务器中检索日志时，将通过GetTrackingLogs SOAP调用（在remoteTracking模式中定义）来检索日志。

serverConf.xml文件中的选项允许您设置通过此方法一次检索的日志数： logCountPerRequest。

logCountPerRequest的默认值为1000，在某些情况下，它可能会证明太小。 接受的值必须介于0和10.000之间。

+++

+++跟踪日志无法链接到收件人

在Adobe Campaign Classic中，根据收件人架构与broadlog / trackinglog架构，目标映射应该是唯一的。

![](assets/tracking-troubleshooting.png)

不能将多个定位架构与同一个trackinglog架构一起使用，因为跟踪工作流将无法协调数据与定位id。

如果不想将现成的目标映射与nms:recipient一起使用，我们建议使用以下方法：

* 如果要使用自定义定位维度，则需要使用nms:broadlog作为模板（例如nms:broadLogRcp、nms:broadLogSvc等）创建自定义broadLog/trackingLog架构。

* 如果要使用OOB trackingLogRcp/broadLogRcp，则定向维度必须是nms:recipient，并且筛选维度可以是自定义架构。

+++
