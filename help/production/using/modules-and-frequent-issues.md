---
solution: Campaign Classic
product: campaign
title: 模块和常见问题
description: 模块和常见问题
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---


# 模块和常见问题{#modules-and-frequent-issues}

以下是受常见问题影响的模块列表:

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
   <td> 计划此导出的操作员需要重新启动它。 检查重复。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 阅读弹回邮件框<br /> </td> 
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
   <td> 日志写入<br /> </td> 
   <td> 如果日志文件中缺少某些日志，请检查以确保模块使用端口6666。 请参阅<a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">打开端口列表</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪 </td> 
   <td> 合并和检索跟踪日志<br /> </td> 
   <td> 如果跟踪日志不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 跟踪日志写入和清除服务器<br /> </td> 
   <td> 如果跟踪日志不再转发，且服务器上的文件中没有日志的跟踪，请检查此模块。 请参阅<a href="../../production/using/tracking-logs-issues.md" target="_blank">跟踪日志问题</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 监视 </td> 
   <td> 启动和监视实例<br /> </td> 
   <td> 如果没有进程开始，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> 应用程序服务器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web连接不工作并触发<strong>xtk:session</strong>类型错误<br />，请检查此模块 </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流实例的执行。<br /> </td> 
   <td> 如果遇到任何问题，请重新启动此模块。 如果需要，应用该过程以提高<a href="../../production/using/log-precision.md" target="_blank">日志精度</a>部分中详细描述的日志的精度。<br /> </td> 
  </tr> 
 </tbody> 
</table>

