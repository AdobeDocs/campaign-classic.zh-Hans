---
product: campaign
title: 模块和常见问题
description: 模块和常见问题
feature: Monitoring, Troubleshooting
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 7%

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
   <td> 正在读取退回邮箱<br /> </td> 
   <td> 如果退回邮件不再转发，则检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 发送电子邮件<br /> </td> 
   <td> 如果不再发送邮件，则检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> 维护MTA连接统计信息<br /> </td> 
   <td> 如果不再发送邮件，则检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 日志写入<br /> </td> 
   <td> 如果日志文件中缺少某些日志，请检查以确保模块使用的是端口6666。 请参阅<a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">打开的端口列表</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪 </td> 
   <td> 合并和检索跟踪日志<br /> </td> 
   <td> 如果跟踪日志不再转发，则检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 正在写入和清除服务器<br />的跟踪日志 </td> 
   <td> 如果跟踪日志不再转发，并且服务器上文件没有日志跟踪，则选中此模块。 请参阅<a href="../../production/using/tracking-logs-issues.md" target="_blank">跟踪日志问题</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 监视程序 </td> 
   <td> 启动和监视实例<br /> </td> 
   <td> 如果未启动任何进程，则检查此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> Web </td> 
   <td> 应用程序服务器(HTTP和SOAP)<br /> </td> 
   <td> 如果控制台和Web连接不起作用并触发<strong>xtk：session</strong>类型错误，则检查此模块<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流实例的执行。<br /> </td> 
   <td> 如果遇到任何问题，请重新启动此模块。 如有必要，请应用此过程以提高在<a href="../../production/using/log-precision.md" target="_blank">日志精度</a>部分中详述的日志精度。<br /> </td> 
  </tr> 
 </tbody> 
</table>
