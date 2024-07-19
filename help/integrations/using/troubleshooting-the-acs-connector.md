---
product: campaign
title: ACS连接器故障排除
description: ACS连接器故障排除
feature: ACS Connector, Troubleshooting
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
hidefromtoc: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---

# ACS连接器故障排除{#troubleshooting-the-acs-connector}



根据您的实施，您可能会遇到几个常见问题。

* **Campaign Standard与Campaign v7在UI上有什么区别？**

  Campaign Standard和Campaign v7的工作方式非常相似。 大多数概念是相同的，但在某些情况下，方法可能会略有不同。 以下是一些在ACS Connector上下文中可能不同的概念：

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 收件人（或任何其他配置文件维度）<br /> </td> 
   <td> 配置文件<br /> </td> 
  </tr> 
  <tr> 
   <td> 列表<br /> </td> 
   <td> 受众<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销活动工作流，定位工作流<br /> </td> 
   <td> 工作流<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作<br /> </td> 
   <td> 营销活动<br /> </td> 
  </tr> 
  <tr> 
   <td> Web应用程序<br /> </td> 
   <td> 登陆页面<br /> </td> 
  </tr> 
  <tr> 
   <td> 自定义表和架构扩展<br /> </td> 
   <td> 自定义资源和资源扩展<br /> </td> 
  </tr> 
  <tr> 
   <td> 种子成员<br /> </td> 
   <td> 测试配置文件<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **我的Campaign v7实例的收件人未同步或对Campaign Standard不可见。**

  发生此情况的原因可能有所不同：

   * 刚刚在Campaign v7中创建或更新了收件人。 同步每15分钟触发一次。 这意味着在下次同步后，更新的或新创建的收件人将在Campaign Standard中可见。
   * 您的实施可以设置为仅同步特定文件夹中的收件人。 来自其他文件夹的收件人不同步。
   * 收件人可以同步，但在Campaign Standard中不可见。 检查文件夹权限映射。

* **我在Campaign Standard中找不到查询所基于的配置文件字段。**

  默认情况下，nms：recipient表中的20个字段会与Campaign Standard同步。 请参阅已同步字段的详细列表。 您需要在Campaign Standard中检索的任何其他字段必须由您的顾问映射和配置。

  要确保要使用的字段可用，可以从&#x200B;**[!UICONTROL Administration > Development > Diagnosis > Data schemas]**&#x200B;中检查配置文件资源定义。

  此外，默认情况下，附加到收件人并存储在与nms：recipients相关的表中的所有数据都不会同步到Campaign Standard。

  为了仍然能够使用相关数据，您可以在Campaign v7中执行定位并添加其他数据，如[同步受众](../../integrations/using/synchronizing-audiences.md)部分中所述，或者您可以咨询顾问以探索自定义可能性。

* **我在Campaign v7中使用除默认nms：recipient之外的其他配置文件维度，如何将其与Campaign Standard同步？**

  Campaign Standard使用名为&#x200B;**配置文件**&#x200B;的唯一定位资源。 Campaign Standard连接功能的基本实施提供了Campaign v7收件人与Campaign Standard配置文件之间的默认映射。

  如果您在Campaign v7中使用其他用户档案维度，或者如果您使用多个用户档案维度，则必须使用Campaign Standard用户档案来映射所有这些维度。 请咨询您的顾问，以解决此特定需求。

* **我想通过工作流与Campaign Standard共享用户档案列表，但在Campaign Standard**&#x200B;中找不到我的受众。

  可以在Campaign Standard的&#x200B;**[!UICONTROL Audiences]**&#x200B;菜单中找到受众。 他们有在Campaign v7工作流的&#x200B;**[!UICONTROL List update]**&#x200B;活动中指定的标签。 它们受实施期间定义的文件夹映射的约束。

  首先要检查的是，工作流是否已顺利完成。 如果您在&#x200B;**[!UICONTROL List update]**&#x200B;活动上发现错误，则表示与Campaign Standard的同步可能已失败。 要能够查看有关所发生问题的更多详细信息，请转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此文件夹包含由&#x200B;**[!UICONTROL List update]**&#x200B;活动执行触发的同步工作流。

  另外，请确保在&#x200B;**[!UICONTROL List update]**&#x200B;活动中选中&#x200B;**[!UICONTROL Share with ACS]**&#x200B;选项并且正确执行了工作流。

  请注意，在执行工作流之前，列表中所包含的收件人用户档案必须与Campaign Standard同步。 在与Campaign Standard共享后，列表的收件人将与Campaign Standard配置文件进行协调，这意味着他们必须存在于那里。 列表中无法与Campaign Standard中的用户档案进行协调的收件人将被忽略。

  如果您共享由用户档案构成的列表，并且没有与Campaign Standard同步的列表，则它将在Campaign Standard中创建无法使用的空查询受众。

* **我收到通知，告知我同步工作流处于错误状态。 我应该怎么做？**

  通过测试连接检查Campaign Standard和Campaign v7中的外部帐户配置：

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard。
   * Campaign v7中的&#x200B;**[!UICONTROL acsDefaultAccount]**。

* **在Campaign v7和Campaign Standard之间映射文件夹时，**&#x200B;我没有可用的安全组。

  您需要首先从&#x200B;**[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**&#x200B;同步您的安全组。 此操作检查Campaign Standard中可用的安全组。 同步后，您可以在配置文件夹映射时找到安全组。

* **我无法在Campaign Standard中编辑个人资料、受众或登陆页面。 这是什么意思？**

  从Campaign v7同步的资源在Campaign Standard中处于只读模式，以确保数据一致性。 如果需要编辑这些元素之一，可以在Campaign v7中进行编辑，然后在Campaign Standard中复制更改。

* **在[ACS]配置文件投放日志复制工作流中发生错误。 我应该怎么做？**

  如果使用Campaign Classic和Campaign Standard实例发送包含跟踪URL的电子邮件，则同步期间可能会出现与重复URL tagId有关的问题。 在这种情况下，**[ACS]配置文件投放日志复制** (newRcpDeliveryLogReplication)工作流仍会失败，并出现以下错误：

  ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

  要解决问题并防止再次发生此问题，请更新工作流中的&#x200B;**更新跟踪URL** (writerTrackingUrls)活动，并将“ACS”前缀添加到@tagId源表达式中。
