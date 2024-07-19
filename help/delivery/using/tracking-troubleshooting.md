---
product: campaign
title: 跟踪故障排除
description: 本节提供了与Adobe Campaign中的跟踪配置和实施相关的常见问题
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring, Troubleshooting
role: User
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 1%

---

# 跟踪故障排除 {#tracking-troubleshooting}

在此部分中，您将找到与Adobe Campaign Classic中的跟踪配置和实施相关的常见问题。

## 跟踪工作流失败 {#tracking-workflow-failing}

我的跟踪工作流失败，如何检测跟踪文件中的损坏行？

>[!NOTE]
>
>仅适用于Windows

损坏的跟踪日志文件……/nl6/var/&lt;instance_name>/redir/log/0x0000日志可以停止跟踪工作流。 要轻松检测损坏的行并删除它们以恢复跟踪工作流，您可以使用以下命令。

### 我知道损坏的行位于哪个文件中

在这种情况下，可以在0x00000000000A0000.log文件中找到损坏的行，但相同的过程可以应用到一组文件 — 一个一个文件。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然后，您可以停止跟踪工作流，删除损坏的行并重新启动工作流。

### 我现在没有损坏行的文件

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

## 跟踪链接间歇性失败 {#tracking-links-fail-intermittently}

在尝试访问跟踪链接时，会显示以下消息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

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

## 是否更新NmsTracking_Pointer选项？ {#updating-option}

更新NmsTracking_Pointer选项时，请按照以下步骤操作：

1. 停止跟踪工作流。

1. 停止trackinglog服务。

1. 将NmsTracking_Pointer选项更新为所需的值。

1. 重新启动trackinglogd服务。

1. 重新启动跟踪工作流。

## 跟踪似乎不适用于某些WebMail {#webmail}

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

## 跟踪日志检索速度太慢 {#slow-retrieval}

当实例不直接检索跟踪日志，而是从远程的Adobe Campaign Classic服务器中检索日志时，将通过GetTrackingLogs SOAP调用（在remoteTracking模式中定义）来检索日志。

serverConf.xml文件中的选项允许您设置通过此方法一次检索的日志数： logCountPerRequest。

logCountPerRequest的默认值为1000，在某些情况下，它可能会证明太小。 接受的值必须介于0和10.000之间。

## 跟踪日志无法链接到收件人 {#link-recipients}

在Adobe Campaign Classic中，根据收件人架构与broadlog / trackinglog架构，目标映射应该是唯一的。

![](assets/tracking-troubleshooting.png)

不能将多个定位架构与同一个trackinglog架构一起使用，因为跟踪工作流将无法协调数据与定位id。

如果不希望将现成的目标映射与nms：recipient一起使用，我们建议使用以下方法：

* 如果要使用自定义定位维度，则需要使用nms：broadlog作为模板创建自定义broadLog/trackingLog架构（例如nms：broadLogRcp、nms：broadLogSvc等）。

* 如果要使用OOB trackingLogRcp/broadLogRcp，则定向维度必须是nms：recipient，并且筛选维度可以是自定义架构。
