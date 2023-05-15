---
product: campaign
title: 投放状态
description: 了解有关投放仪表板上可用状态的更多信息
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 8%

---

# 投放状态 {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

发送投放后，投放仪表板会显示一个状态，用于监视发送是否成功。 以下部分详细介绍了可能的状态。

![](assets/delivery-status.png)

有关您可能遇到的不同投放失败以及如何解决这些失败的详细信息，请参阅 [本页](understanding-delivery-failures.md).

**相关主题：**

* [投放仪表板](delivery-dashboard.md)
* [投放疑难解答](delivery-troubleshooting.md)
* [投放能力入门](about-deliverability.md)

## 投放状态列表 {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> 状态<br /> </th> 
   <th> 定义和解决方案<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已发送<br /> </td> 
   <td> 投放已正确发送到消息提供程序（但收件人不一定会收到它）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由于收件人地址出错，未将投放发送给收件人。 已、已隔阻止列表离、未提供或存在重复项。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 已失败<br /> </td> 
   <td> 由于地址无效或收件箱已满等原因，投放无法到达收件人。 它还可以链接到个性化块的问题，因为当架构与投放映射不匹配时，这些块可能会生成错误。 请参阅 <a href="understanding-delivery-failures.md" target="_blank">了解投放失败</a><br /> </td> 
  </tr>
  <tr> 
   <td> 待处理<br /> </td> 
   <td> 投放已准备就绪，可供投放服务器(MTA)处理。 请参阅 <a href="#pending-status" target="_blank">待定状态</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 不适用<br /> </td> 
   <td> 服务器(MTA)已考虑投放，但未处理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 投放已取消<br /> </td> 
   <td> 操作员取消了投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由服务提供商考虑<br /> </td> 
   <td> 短信服务提供商收到了投放。<br /> 对于托管安装或混合安装(如果已升级到 <a href="sending-with-enhanced-mta.md" target="_blank">增强的MTA</a>，则该消息已成功从Campaign中继到增强MTA。</td> 
  </tr> 
  <tr> 
   <td> 已在移动设备上接收<br /> </td> 
   <td> 收件人在其移动设备上收到了短信。<br /> </td> 
  </tr>
  <tr> 
   <td> 已发送给服务提供商<br /> </td> 
   <td> 已将投放发送到短信服务提供商，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 已准备<br /> </td> 
   <td> 中间状态仅用于外部连接器（如移动渠道）。 它遵循“待定”状态，是将确定以下状态的外部连接器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

要了解如何优化Adobe Campaign电子邮件的投放能力，请参阅 [此部分](about-deliverability.md). 要更深入地了解投放能力，请参阅 [Adobe投放能力最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

## 待定状态 {#pending-status}

确认投放后，您可以看到投放的状态为 **[!UICONTROL Pending]**. 此状态表示执行进程正在等待某些资源的可用性。

的 **[!UICONTROL Pending]** 状态首先表示您的投放已计划，在给定日期之前处于待处理状态。 有关更多信息，请参阅 [投放计划](steps-sending-the-delivery.md#scheduling-the-delivery-sending) 中。

如果未发送投放，且其状态仍为 **[!UICONTROL Pending]**，则可能是以下结果：

* MTA（邮件传输代理）在投放服务器上运行模块和进程并管理电子邮件发送，它可能尚未启动，或可能需要重新启动。

   要选中此复选框并在必要时启动模块，请应用以下步骤：

   >[!NOTE]
   >
   >此操作可以通过 **内部部署** 或 **混合** 使用访问Campaign服务器的托管模型(请参阅 [托管模型](../../installation/using/hosting-models.md))。

   1. 检查 `mta@<instance>` 模块会在您的MTA服务器上启动。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果MTA未列出，请使用以下命令启动它：

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >替换 `<INSTANCENAME>` ，其名称为实例（生产、开发等）。 实例名称通过配置文件进行标识： `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 投放可能使用未在发送服务器上配置的亲和度。

   在这种情况下，请检查流量管理（IP亲和度）的配置，并使用 **[!UICONTROL Managing affinities with IP addresses]** 字段，将投放链接到管理亲和度的MTA。 有关相关性的更多信息，请参阅 [此部分](../../installation/using/configure-delivery-settings.md).

* 当运行的营销活动过多时，投放状态仍为“待定”状态。

   在 **[!UICONTROL NmsOperation_LimitConcurrency]** 选项。 默认值为 10。

   了解有关 [本页](../../installation/using/configuring-campaign-options.md).


**相关主题：**

* [投放日志和历史记录](#delivery-logs-and-history)
* [了解投放失败](understanding-delivery-failures.md)
* [投放失败类型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
