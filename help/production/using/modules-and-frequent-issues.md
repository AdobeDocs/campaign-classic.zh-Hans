---
product: campaign
title: 模块和常见问题
description: 模块和常见问题
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

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
   <td> 计划此导出的操作员需要重新启动它。 增量或完全重新启动。<br /> </td> 
  </tr> 
  <tr> 
   <td> 导入 </td> 
   <td> 导入过程的执行<br /> </td> 
   <td> 计划此导出的操作员需要重新启动它。 检查数据库是否存在重复项。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 读取退回邮箱<br /> </td> 
   <td> 如果退回的邮件不再转发，则检查此模块。<br /> </td> 
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
   <td> 如果日志文件中缺少某些日志，请检查以确保模块使用的是端口6666。 请参阅 <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">打开的端口列表</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟踪 </td> 
   <td> 合并和检索跟踪日志<br /> </td> 
   <td> 如果不再转发跟踪日志，请选中此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 跟踪日志写入和清除服务器<br /> </td> 
   <td> 如果跟踪日志不再转发，并且服务器上的文件中没有日志跟踪，则选中此模块。 请参阅 <a href="../../production/using/tracking-logs-issues.md" target="_blank">跟踪日志问题</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 监视程序 </td> 
   <td> 启动和监控实例<br /> </td> 
   <td> 如果未启动任何进程，则选中此模块。<br /> </td> 
  </tr> 
  <tr> 
   <td> Web </td> 
   <td> 应用程序服务器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web连接不起作用并触发 <strong>xtk：session</strong> 类型错误<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流实例的执行。<br /> </td> 
   <td> 如果遇到任何问题，请重新启动此模块。 如有必要，请应用此过程以提高日志的精度，详见 <a href="../../production/using/log-precision.md" target="_blank">日志精度</a> 部分。<br /> </td> 
  </tr> 
 </tbody> 
</table>
