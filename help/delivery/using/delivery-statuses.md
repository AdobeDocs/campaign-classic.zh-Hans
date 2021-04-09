---
solution: Campaign Classic
product: campaign
title: 传递状态
description: 进一步了解您的投放仪表板中可用的状态。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 5%

---

# 传递状态 {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

发送投放后，投放仪表板将显示状态，允许您监视发送是否成功。 以下部分详细介绍了可能的状态。

![](assets/delivery-status.png)

有关您可能遇到的不同投放故障以及如何解决这些故障的详细信息，请参阅[此页](../../delivery/using/understanding-delivery-failures.md)。

**相关主题：**

* [传递仪表板](../../delivery/using/delivery-dashboard.md)
* [传递疑难解答](../../delivery/using/delivery-troubleshooting.md)
* [关于投放能力](../../delivery/using/about-deliverability.md)

## 列表投放状态{#list-delivery-statuses}

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
   <td> 投放已正确发送到消息提供程序(但收件人未必收到它)。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由于投放的地址出错，未将其发送到收件人。 它处于阻止列表、隔离、未提供或重复。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败<br /> </td> 
   <td> 例如，由于地址无效或收件箱已满，投放无法到达收件人。 它还可以链接到个性化块的问题，因为当模式与投放映射不匹配时，它们会生成错误。 请参阅<a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">了解投放故障</a><br /> </td> 
  </tr>
  <tr> 
   <td> 挂起<br /> </td> 
   <td> 投放已准备好发送，并将由投放服务器(MTA)处理。 请参阅<a href="#pending-status" target="_blank">挂起状态</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不适用<br /> </td> 
   <td> 服务器(MTA)已考虑投放，但未处理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 投放已取消<br /> </td> 
   <td> 操作符取消了投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由服务提供商<br />考虑 </td> 
   <td> SMS服务提供商收到投放。<br /> 对于托管或混合安装，如果您已升级到增强 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">MTA</a>，则消息已从活动成功中继到增强MTA。</td> 
  </tr> 
  <tr> 
   <td> 在移动设备上接收<br /> </td> 
   <td> 收件人在其移动设备上收到SMS。<br /> </td> 
  </tr>
  <tr> 
   <td> 已发送到服务提供商<br /> </td> 
   <td> 投放已发送到SMS服务提供商，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 准备<br /> </td> 
   <td> 中间状态仅用于外部连接器，如移动渠道。 它遵循“待定”状态，是将确定以下状态的外部连接器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

要了解如何优化Adobe Campaign电子邮件的可发送性，请参阅[本节](../../delivery/using/about-deliverability.md)。 有关可交付性的更深入了解，请参阅[《Adobe可交付性最佳实践指南》](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hans)。

## 挂起状态{#pending-status}

确认投放后，您可以看到投放的状态为&#x200B;**[!UICONTROL Pending]**。 此状态表示执行进程正在等待某些资源的可用性。

**[!UICONTROL Pending]**&#x200B;状态首先表示您的投放已计划并待处理到指定日期。 有关详细信息，请参阅[投放调度](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)部分。

如果未发送投放，且其状态仍为&#x200B;**[!UICONTROL Pending]**，则可能是以下结果：

* 在投放服务器上运行模块和进程并管理电子邮件发送的MTA（邮件传输代理）可能尚未启动或需要重新启动。

   要选中此项并在必要时开始模块，请应用以下步骤：

   >[!NOTE]
   >
   >此操作可以使用&#x200B;**内部部署**&#x200B;或&#x200B;**混合**&#x200B;托管模型执行，并访问活动服务器（请参阅[托管模型](../../installation/using/hosting-models.md)）。

   1. 检查您的`mta@<instance>`模块是否已在您的MTA服务器上启动。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果未列出MTA，请使用以下命令开始它：

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >将`<INSTANCENAME>`替换为实例的名称（生产、开发等）。 实例名称通过配置文件进行标识：`[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 投放可能使用在发送服务器上未配置的关联。

   在这种情况下，请检查流量管理(IP关联)的配置，并使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;字段将投放链接到管理关联的MTA。 有关关联的详细信息，请参阅[本节](../../installation/using/configure-delivery-settings.md)。

* 当运行的活动过多时，投放状态仍为“待定”状态。

   同时活动的限制在&#x200B;**[!UICONTROL NmsOperation_LimitConcurrency]**&#x200B;选项中定义。 默认值为 10。

   了解有关[本页](../../installation/using/configuring-campaign-options.md)中选项的更多信息。


**相关主题：**

* [投放日志和历史](#delivery-logs-and-history)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [投放失败类型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
