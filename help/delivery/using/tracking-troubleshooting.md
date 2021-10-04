---
product: campaign
title: 跟踪故障排除
description: 本节提供与在Adobe Campaign Classic中跟踪配置和实施相关的常见问题。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 1%

---

# 跟踪故障排除 {#tracking-troubleshooting}

![](../../assets/common.svg)

在此部分中，您将在Adobe Campaign Classic中找到与跟踪配置和实施相关的常见问题。

## 跟踪工作流失败 {#tracking-workflow-failing}

我的跟踪工作流失败，如何检测跟踪文件中的损坏行？

>[!NOTE]
>
>仅适用于Windows

损坏的跟踪日志文件……/nl6/var/&lt;instance_name>/redir/log/0x0000日志可以停止跟踪工作流。 要轻松检测损坏的行并删除它们以恢复跟踪工作流，您可以使用以下命令。

### 我知道哪个文件中的损坏行

在这种情况下，在0x00000000000A0000.log文件中可以找到损坏的行，但同一过程可以应用于一组文件 — 逐个。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然后，您可以停止跟踪工作流，删除损坏的行并重新启动工作流。

### 我现在没有文件中损坏的行

1. 使用以下命令行签入所有跟踪文件。

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 命令会列出所有损坏的行。 例如：

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >在用户代理之前添加了回车符，以便更好地读取内容，且不会反映有效渲染。

1. 运行grep命令以查找相应的文件。

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. 找到文件名和行号错误的日志。 例如：

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >在用户代理之前添加了回车符，以便更好地读取内容，且不反映有效渲染。

然后，您可以停止跟踪工作流，删除损坏的行并重新启动工作流。

## 跟踪链接间歇性失败 {#tracking-links-fail-intermittently}

尝试访问跟踪链接时，会显示以下消息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. 访问&lt;redirection_server>/r/test URL ，并检查请求是否返回了内部版本号和localhost。

1. 检查serverConf.xml文件中的spareServer配置，以获取跟踪服务器。 此配置应处于重定向模式。

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

1. 手动检查&lt;deliveryID>.xml文件是否存在于……的计算机上/nl6/var/&lt;instance_name>/redir/url/&lt;YYYY>目录（YYYY表示交付年）。

1. 手动检查是否可以在&lt;deliveryID>.xml文件中找到&lt;trackingUrlId>。

1. 手动检查相关deliveryID投放中是否存在broadlogID。

1. 检查……中的&lt;deliveryID>.xml文件权限/nl6/var/&lt;instance_name>/redir/url/year目录。

   他们应至少拥有644个权限，以便Apache可以读取跟踪url以重定向请求的链接。

## 是否更新NmsTracking_Pointer选项？ {#updating-option}

在更新NmsTracking_Pointer选项时，请按照以下步骤操作：

1. 停止跟踪工作流。

1. 停止trackinglogd服务。

1. 将NmsTracking_Pointer选项更新为所需值。

1. 重新启动trackinglogd服务。

1. 重新启动跟踪工作流。

## 跟踪似乎不适用于某些WebMail {#webmail}

您可以自定义点击跟踪公式并指定自定义Adobe Analytics跟踪公式。

这种自定义操作需要谨慎进行，以避免添加额外的换行字符。 JavaScript表达式外存在的所有换行字符都将出现在最终公式中。

跟踪URL中的这种额外换行字符将导致在某些WebMail（AOL、GMail等）中出现问题。

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

* 正确的语法

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

要了解额外换行的位置，可以使用固定字符串STRING替换JavaScript表达式。

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

* 正确的语法

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

要了解额外换行的位置，可以使用固定字符串STRING替换JavaScript表达式。

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## 跟踪日志检索过慢 {#slow-retrieval}

当实例不直接检索跟踪日志，而是从远程Adobe Campaign Classic服务器中检索时，将通过GetTrackingLogs SOAP调用（在remoteTracking架构中定义）来检索日志。

serverConf.xml文件中的一个选项允许您通过此方法设置一次检索的日志数：logCountPerRequest。

logCountPerRequest的默认值为1000，在某些情况下可能证明它太小。 接受的值必须介于0和10.000之间。

## 跟踪日志无法链接到收件人 {#link-recipients}

在Adobe Campaign Classic中，就收件人架构与broadlog/trackinglog架构而言，目标映射应该是唯一的。

![](assets/tracking-troubleshooting.png)

无法使用具有相同跟踪日志模式的多个定位模式，因为跟踪工作流将无法将数据与定位ID协调。

如果您不想对nms:recipient使用即装即用的目标映射，我们建议采用以下方法：

* 如果要使用自定义定向维度，您需要使用nms:broadlog作为模板（例如nms:broadLogRcp、nms:broadLogSvc等）创建自定义broadLog/trackingLog模式。

* 如果要使用OOB trackingLogRcp/broadLogRcp，则定向维度必须是nms:recipient ，而筛选维度可能是自定义模式。
