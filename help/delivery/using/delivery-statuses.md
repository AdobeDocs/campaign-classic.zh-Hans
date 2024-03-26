---
product: campaign
title: 投放状态
description: 了解有关投放仪表板上可用的状态的更多信息
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 3%

---

# 投放状态 {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

发送投放后，投放仪表板会显示一个状态，允许您监测发送是否成功。 可能的状态详见下节。

![](assets/delivery-status.png)

有关您可以遇到的不同投放失败以及如何解决它们的更多详细信息，请参阅 [此页面](understanding-delivery-failures.md).

**相关主题：**

* [投放仪表板](delivery-dashboard.md)
* [投放疑难解答](delivery-troubleshooting.md)
* [可投放性入门](about-deliverability.md)

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
   <td> 该投放已正确发送到消息提供商（但收件人不一定收到该投放）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由于收件人地址错误，该投放未发送给收件人。 该文件被阻止列表、隔离、未提供或重复。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 失败<br /> </td> 
   <td> 例如，由于地址无效或收件箱已满，投放无法到达收件人。 它还可能链接到个性化块的问题，因为它们可能会在架构与投放映射不匹配时生成错误。 请参阅 <a href="understanding-delivery-failures.md" target="_blank">了解投放失败</a><br /> </td> 
  </tr>
  <tr> 
   <td> 待处理<br /> </td> 
   <td> 投放已准备好发送，将由投放服务器(MTA)处理。 请参阅 <a href="#pending-status" target="_blank">待处理状态</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 不适用<br /> </td> 
   <td> 服务器(MTA)已考虑投放，但未处理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 投放已取消<br /> </td> 
   <td> 操作员已取消投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由服务提供商考虑<br /> </td> 
   <td> SMS服务提供商已收到投放。<br /> 对于托管或混合安装，如果已升级到 <a href="sending-with-enhanced-mta.md" target="_blank">增强MTA</a>，则消息已成功从Campaign中继到增强型MTA。</td> 
  </tr> 
  <tr> 
   <td> 已在移动设备上接收<br /> </td> 
   <td> 收件人在其移动设备上收到短信。<br /> </td> 
  </tr>
  <tr> 
   <td> 已发送给服务提供商<br /> </td> 
   <td> 投放已发送到SMS服务提供商，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 已准备<br /> </td> 
   <td> 仅用于外部连接器（如移动渠道）的中间状态。 它遵循“挂起”状态，是确定以下状态的外部连接器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

要了解如何优化Adobe Campaign电子邮件的可投放性，请参阅 [本节](about-deliverability.md). 要更深入地了解可投放性，请参阅 [Adobe可投放性最佳实践指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans).

## 待处理状态 {#pending-status}

确认投放后，您可以看到投放状态为 **[!UICONTROL Pending]**. 此状态表示执行进程正在等待某些资源的可用性。

此 **[!UICONTROL Pending]** 状态可以首先表示您的投放已计划并处于待定状态，直到给定日期。 有关详细信息，请参见 [投放计划](steps-sending-the-delivery.md#scheduling-the-delivery-sending) 部分。

如果您的投放未发送，并且其状态保持不变 **[!UICONTROL Pending]**，这可能是以下结果：

* 在投放服务器上运行模块和进程并管理电子邮件发送的MTA（消息传输代理）可能尚未启动，或需要重新启动。

  要选中此复选框，并在必要时启动模块，请应用以下步骤：

  >[!NOTE]
  >
  >此操作可以使用 **内部部署** 或 **混合** 有权访问Campaign服务器的托管模型(请参阅 [托管模型](../../installation/using/hosting-models.md))。

   1. 检查您的 `mta@<instance>` 模块在MTA服务器上启动。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果未列出MTA，请使用以下命令启动它：

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >替换 `<instance-name>` 使用实例的名称（生产、开发等）。 实例名称通过配置文件进行标识： `[path of application]nl6/conf/config-<instance-name>.xml`

* 投放可能使用未在发送服务器上配置的关联性。

  在这种情况下，请检查流量管理（IP关联）的配置并使用 **[!UICONTROL Managing affinities with IP addresses]** 用于将投放链接到管理亲和度的MTA的字段。 有关关联的更多信息，请参阅 [本节](../../installation/using/configure-delivery-settings.md).

* 当运行过多营销活动时，投放状态仍为“待定”状态。

  在中定义了同时营销活动的限制 **[!UICONTROL NmsOperation_LimitConcurrency]** 选项。 默认值为 10。

  了解更多有关选项的信息，请参阅 [此页面](../../installation/using/configuring-campaign-options.md).


**相关主题：**

* [投放日志和历史记录](#delivery-logs-and-history)
* [了解投放失败](understanding-delivery-failures.md)
* [投放失败类型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
