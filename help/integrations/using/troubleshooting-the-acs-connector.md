---
title: ACS连接器故障排除
seo-title: ACS连接器故障排除
description: ACS连接器故障排除
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# ACS连接器故障排除{#troubleshooting-the-acs-connector}

根据您的实施，您可能会面临几个常见问题。

* **Campaign standard和Campaign v7之间的UI区别是什么？**

   Campaign standard和Campaign v7的工作方式非常相似。 大多数概念相同，但在某些情况下，方法可能略有不同。 以下是ACS连接器上下文中可能不同的一些概念：

<table> 
 <thead> 
  <tr> 
   <th> 营销活动v7<br /> </th> 
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
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销活动工作流程，定位工作流程<br /> </td> 
   <td> 工作流程<br /> </td> 
  </tr> 
  <tr> 
   <td> 运营<br /> </td> 
   <td> 营销活动<br /> </td> 
  </tr> 
  <tr> 
   <td> Web应用程序<br /> </td> 
   <td> landing pages<br /> </td> 
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

* **我的Campaign v7实例的收件人未同步或对Campaign standard可见。**

   此案可能因以下不同原因而发生：

   * 收件人刚刚在Campaign v7中创建或更新。 同步每15分钟触发一次。 这意味着更新的或新创建的收件人在下次同步后将显示在Campaign standard中。
   * 您的实施可以设置为仅同步特定文件夹中的收件人。 其他文件夹的收件人不会同步。
   * 收件人可以同步，但在Campaign standard中不可见。 检查文件夹权限映射。

* **在Campaign standard中，我找不到需要基于其查询的配置文件字段。**

   默认情况下，nms:recipient表中的20个字段与Campaign Standard同步。 请参阅同步字段的详细列表。 您需要在Campaign standard中检索的任何其他字段都必须由顾问进行映射和配置。

   要确保要使用的字段可用，您可以从中检查配置文件资源定义 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**。

   此外，默认情况下，附加到收件人并存储在与nms：收件人相关的表中的所有数据都不会同步到Campaign Standard。

   要仍能使用相关数据，您可以在Campaign v7中执行定位并添加其他数据（如同步受众部分所述） [](../../integrations/using/synchronizing-audiences.md) ，也可以咨询顾问来探索自定义可能性。

* **我使用的配置文件维度不同于Campaign v7中的默认nms:recipient，我如何将它们与Campaign standard同步？**

   Campaign standard使用唯一的定位资源，该资源名为配 **置文件**。 Campaign Standard connect功能的基本实施提供了Campaign v7收件人与Campaign standard配置文件之间的默认映射。

   如果您在Campaign v7中使用其他配置文件维，或者如果您使用多个维，则必须将所有配置文件映射到Campaign Standard配置文件。 请咨询您的顾问，解决此特殊需求。

* **我希望通过工作流与Campaign standard共享配置文件列表，但无法在Campaign standard中找到我的受众**。

   可在Campaign standard的菜单 **[!UICONTROL Audiences]** 中找到受众。 它们具有在Campaign v7工作流 **[!UICONTROL List update]** 程中的活动中指定的标签。 它们受实施过程中定义的文件夹映射的约束。

   首先要检查的工作流是否已完成且没有错误。 如果您注意到活动中出 **[!UICONTROL List update]** 现错误，则表示与Campaign standard的同步可能失败。 要查看更多关于出问题的详细信息，请转到 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此文件夹包含由活动执行触发的同步 **[!UICONTROL List update]** 工作流。

   此外，请确保在活动 **[!UICONTROL Share with ACS]** 中选中了该选 **[!UICONTROL List update]** 项，并且工作流正确执行。

   请注意，在执行工作流之前，列表中包含的收件人配置文件必须已与Campaign Standard同步。 与Campaign standard共享后，列表的收件人将与Campaign standard配置文件进行对话，这意味着它们必须存在于该位置。 将忽略列表中无法与Campaign standard中的配置文件进行协调的收件人。

   如果您共享由配置文件组成的列表，并且如果没有配置文件与Campaign Standard同步，则会在Campaign standard中创建一个无法使用的空查询受众。

* **我收到通知，告知我同步工作流处于错误状态。 我该怎么办？**

   通过测试连接，检查Campaign standard和Campaign v7中的外部帐户配置：

   * **[!UICONTROL acsDefaultRelayAccount]** 在Campaign standard中。
   * **[!UICONTROL acsDefaultAccount]** 在Campaign v7中。

* **在Campaign v7和Campaign standard之间映射文件夹时，我没有可用的安全组。**

   您需要首先从中同步安全组 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**。 此操作会检查Campaign standard中可用的安全组。 同步后，您可以在配置文件夹映射时找到安全组。

* **我无法在Campaign standard中编辑个人资料、受众或登录页面。 这意味着什么？**

   从Campaign v7同步的资源在Campaign standard中处于只读模式，以确保数据一致性。 如果需要编辑其中一个元素，您可以在Campaign v7中执行该操作，然后在Campaign standard中复制更改。

