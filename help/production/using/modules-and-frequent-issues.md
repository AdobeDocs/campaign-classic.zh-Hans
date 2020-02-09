---
title: 模块和常见问题
seo-title: 模块和常见问题
description: 模块和常见问题
seo-description: null
page-status-flag: never-activated
uuid: d53324ce-b6e2-40d7-932d-36ce4a6f5cf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: a44f5e71-3f9b-4d02-8b7a-a9782bb6bdd8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 模块和常见问题{#modules-and-frequent-issues}

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
   <td> 执行导出过程<br /> </td> 
   <td> 计划此导出操作员需要重新启动它。 增量或完全重新启动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 导入 </td> 
   <td> 执行导入进程<br /> </td> 
   <td> 计划此导出操作员需要重新启动它。 检查数据库是否有重复项。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 阅读弹回邮件箱<br /> </td> 
   <td> 如果弹回邮件不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 发送电子邮件<br /> </td> 
   <td> 如果不再发送邮件，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> 维护MTA连接统计数据<br /> </td> 
   <td> 如果不再发送邮件，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 日志编写<br /> </td> 
   <td> 如果日志文件中缺少某些日志，请检查以确保模块使用端口6666。 请参阅 <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">打开的端口列表</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪 </td> 
   <td> 合并和检索跟踪日志<br /> </td> 
   <td> 如果跟踪日志不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 跟踪日志写入和清除服务器<br /> </td> 
   <td> 如果跟踪日志不再转发并且服务器上的文件中没有日志的跟踪，请检查此模块。 请参阅 <a href="../../production/using/tracking-logs-issues.md" target="_blank">跟踪日志问题</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 监视 </td> 
   <td> 启动和监视实例<br /> </td> 
   <td> 如果没有进程启动，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> 应用程序服务器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web连接不工作并触发 <strong>xtk:session</strong> type错误，请检查此模块<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流实例的执行。<br /> </td> 
   <td> 如果遇到任何问题，请重新启动此模块。 如果需要，请应用该过程以提高日志精度部分中详细 <a href="../../production/using/log-precision.md" target="_blank">的日志精度</a> 。<br /> </td> 
  </tr> 
 </tbody> 
</table>

