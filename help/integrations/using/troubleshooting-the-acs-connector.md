---
product: campaign
title: ACS连接器故障诊断
description: ACS连接器故障诊断
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
hidefromtoc: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 1%

---

# ACS连接器故障诊断{#troubleshooting-the-acs-connector}



根据您的实施，您可能会遇到几个常见问题。

* **Campaign Standard与Campaign v7之间的UI有何区别？**

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
   <td> 用户档案<br /> </td> 
  </tr> 
  <tr> 
   <td> 列表<br /> </td> 
   <td> 受众<br /> </td> 
  </tr> 
  <tr> 
   <td> 活动工作流，定位工作流<br /> </td> 
   <td> 工作流<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作<br /> </td> 
   <td> 活动<br /> </td> 
  </tr> 
  <tr> 
   <td> Web应用程序<br /> </td> 
   <td> 登陆页面<br /> </td> 
  </tr> 
  <tr> 
   <td> 自定义表和模式扩展<br /> </td> 
   <td> 自定义资源和资源扩展<br /> </td> 
  </tr> 
  <tr> 
   <td> 种子成员<br /> </td> 
   <td> 测试用户档案<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **我的Campaign v7实例的收件人不同步或对Campaign Standard不可见。**

   这种情况发生的原因各不相同：

   * 刚刚在Campaign v7中创建或更新了收件人。 同步每15分钟触发一次。 这意味着在下次同步后，更新的或新创建的收件人将在Campaign Standard中可见。
   * 您的实施可以设置为仅同步特定文件夹中的收件人。 其他文件夹中的收件人不会同步。
   * 收件人可以同步，但在Campaign Standard中不可见。 检查文件夹权限映射。

* **我在Campaign Standard中找不到查询所基于的用户档案字段。**

   默认情况下，nms：recipient表中的20个字段与Campaign Standard同步。 请参阅已同步字段的详细列表。 您在Campaign Standard中需要检索的任何其他字段必须由您的顾问映射和配置。

   要确保要使用的字段可用，您可以从以下位置检查用户档案资源定义 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   此外，默认情况下，附加到收件人并存储在与nms：recipients相关的表中的所有数据都不会同步到Campaign Standard。

   为了仍然能够使用相关数据，您可以在Campaign v7中执行定位并添加其他数据，如中所述 [同步受众](../../integrations/using/synchronizing-audiences.md) 部分，或者您可以咨询顾问以探索自定义的可能性。

* **我在Campaign v7中使用除默认nms：recipient以外的其他配置文件维度，如何将其与Campaign Standard同步？**

   Campaign Standard使用名为的唯一定位资源 **用户档案**. Campaign Standard连接功能的基本实施提供了Campaign v7收件人与Campaign Standard配置文件之间的默认映射。

   如果您在Campaign v7中使用另一个用户档案维度，或者如果您使用多个用户档案维度，则必须使用Campaign Standard用户档案来映射所有用户档案维度。 请咨询您的顾问，以解决此特定需求。

* **我想通过工作流与Campaign Standard共享用户档案列表，但在Campaign Standard中找不到我的受众**.

   可在以下位置找到受众： **[!UICONTROL Audiences]** Campaign Standard中的菜单。 他们在 **[!UICONTROL List update]** 活动。 它们受实施期间定义的文件夹映射的约束。

   首先要检查的是，工作流是否已顺利完成。 如果您注意到 **[!UICONTROL List update]** 活动，这意味着与Campaign Standard的同步可能已失败。 要能够查看有关所发生问题的更多详细信息，请访问 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. 此文件夹包含由触发的同步工作流 **[!UICONTROL List update]** 活动执行。

   此外，确保 **[!UICONTROL Share with ACS]** 选项已勾选 **[!UICONTROL List update]** 活动并确保正确执行了工作流。

   请注意，在执行工作流之前，列表中包含的收件人配置文件必须与Campaign Standard同步。 与Campaign Standard共享后，列表的收件人将与Campaign Standard配置文件进行协调，这意味着他们必须存在那里。 列表中无法与Campaign Standard中的用户档案进行协调的收件人将被忽略。

   如果您共享由用户档案组成的列表，并且没有与Campaign Standard同步的用户档案，则它将在Campaign Standard中创建一个无法使用的空查询受众。

* **我收到一个通知，告诉我同步工作流处于错误状态。 我该怎么办？**

   通过测试连接检查Campaign Standard和Campaign v7中的外部帐户配置：

   * **[!UICONTROL acsDefaultRelayAccount]** 在Campaign Standard中。
   * **[!UICONTROL acsDefaultAccount]** 在Campaign v7中。

* **在Campaign v7和Campaign Standard之间映射文件夹时，我没有可用的安全组。**

   您需要首先从以下位置同步安全组： **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. 此操作检查Campaign Standard中可用的安全组。 同步后，您可以在配置文件夹映射时找到安全组。

* **我无法在Campaign Standard中编辑个人资料、受众或登陆页面。 这是什么意思？**

   从Campaign v7同步的资源在Campaign Standard中处于只读模式，以确保数据一致性。 如果您需要编辑这些元素之一，可以在Campaign v7中进行编辑，然后在Campaign Standard中复制更改。

* **中出现错误 [ACS] 配置文件投放日志复制工作流。 我该怎么办？**

   如果Campaign Classic实例和Campaign Standard实例都用于发送带有跟踪URL的电子邮件，则在同步期间可能会出现重复的URL tagId问题。 在本例中， **[ACS] 配置文件投放日志复制** (newRcpDeliveryLogReplication)工作流仍会失败，并出现以下错误：

   ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

   要解决问题并防止再次发生，请更新 **更新跟踪URL** (writerTrackingUrls)活动，并将“ACS”前缀添加到@tagId源表达式中。
