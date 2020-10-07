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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 6%

---


# 模块和常见问题{#modules-and-frequent-issues}

下面是受频繁问题影响的一列表模块：

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
   <td> 计划此导出的操作员需要重新启动它。 增量或完全重新启动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 导入 </td> 
   <td> 执行导入进程<br /> </td> 
   <td> 计划此导出的操作员需要重新启动它。 检查重复。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 阅读弹回邮箱<br /> </td> 
   <td> 如果弹回邮件不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 发送电子邮件<br /> </td> 
   <td> 如果不再发送邮件，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> 维护MTA连接统计<br /> </td> 
   <td> 如果不再发送邮件，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 日志写入<br /> </td> 
   <td> 如果日志文件中缺少某些日志，请检查以确保模块使用端口6666。 请参阅 <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">打开端口的列表</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪 </td> 
   <td> 整合和检索跟踪日志<br /> </td> 
   <td> 如果跟踪日志不再转发，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪日志 </td> 
   <td> 跟踪日志写入和清除服务器<br /> </td> 
   <td> 如果跟踪日志不再转发，且服务器上的文件中没有日志的痕迹，请检查此模块。 请参阅 <a href="../../production/using/tracking-logs-issues.md" target="_blank">跟踪日志问题</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 监视 </td> 
   <td> 启动和监视实例<br /> </td> 
   <td> 如果没有进程开始，请检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> 应用程序服务器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web连接不工作，请检查此模块并触发xtk: <strong>session类型错误</strong> 。<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流实例执行。<br /> </td> 
   <td> 如果遇到任何问题，请重新启动此模块。 如果需要，请应用该过程以提高日志精度部分中详 <a href="../../production/using/log-precision.md" target="_blank">述的日志</a> 精度。<br /> </td> 
  </tr> 
 </tbody> 
</table>

