---
product: campaign
title: 模块和常见问题
description: 模块和常见问题
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---

# 模块和常见问题{#modules-and-frequent-issues}

![](../../assets/v7-only.svg)

以下是受常见问题影响的模块列表：

<table> 
 <thead> 
  <tr> 
   <th> 模块 </th> 
   <th> 执行范围 </th> 
   <th> 故障排除 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 导出 </td> 
   <td> 执行导出进程<br /> </td> 
   <td> 计划此导出的操作员需要重新启动它。 增量或完全重新启动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 导入 </td> 
   <td> 执行导入进程<br /> </td> 
   <td> 计划此导出的操作员需要重新启动它。 检查数据库是否存在重复项。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 读取退回邮箱<br /> </td> 
   <td> 如果退回邮件不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 发送电子邮件<br /> </td> 
   <td> 如果邮件不再发送，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> 维护MTA连接统计信息<br /> </td> 
   <td> 如果邮件不再发送，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 日志写入<br /> </td> 
   <td> 如果日志文件中缺少某些日志，请检查以确保模块使用的是端口6666。 请参阅<a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">打开端口列表</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪 </td> 
   <td> 整合和检索跟踪日志<br /> </td> 
   <td> 如果跟踪日志不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 跟踪日志写入和清除服务器<br /> </td> 
   <td> 如果跟踪日志不再转发，并且服务器上的文件中没有日志的跟踪，请检查此模块。 请参阅<a href="../../production/using/tracking-logs-issues.md" target="_blank">跟踪日志问题</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 监视 </td> 
   <td> 启动和监视实例<br /> </td> 
   <td> 如果没有进程启动，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> 应用程序服务器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web连接不工作，请检查此模块并触发<strong>xtk:session</strong>类型错误<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流实例的执行。<br /> </td> 
   <td> 如果遇到任何问题，请重新启动此模块。 如有必要，请应用该过程来提高<a href="../../production/using/log-precision.md" target="_blank">日志精度</a>部分中详细描述的日志精度。<br /> </td> 
  </tr> 
 </tbody> 
</table>
