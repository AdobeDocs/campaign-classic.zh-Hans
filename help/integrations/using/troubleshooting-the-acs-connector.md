---
product: campaign
title: ACS Connector故障诊断
description: ACS Connector故障诊断
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# ACS Connector故障诊断{#troubleshooting-the-acs-connector}

![](../../assets/v7-only.svg)

根据您的实施，您可能会面临一些常见问题。

* **Campaign Standard与Campaign v7之间的UI有何区别？**

   Campaign Standard和Campaign v7的工作方式非常相似。 大多数概念是相同的，但在某些情况下，方法可能略有不同。 以下是ACS Connector上下文中可能不同的一些概念：

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 收件人（或任何其他用户档案维度）<br /> </td> 
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

* **我的Campaign v7实例的收件人未同步或对Campaign Standard可见。**

   这种情况的发生原因可能有所不同：

   * 刚刚在Campaign v7中创建或更新了收件人。 每15分钟触发一次同步。 这意味着更新的或新创建的收件人将在下次同步后的Campaign Standard中可见。
   * 可以将您的实施设置为仅同步特定文件夹中的收件人。 未同步来自其他文件夹的收件人。
   * 收件人可以同步，但在Campaign Standard中不可见。 检查文件夹权限映射。

* **在Campaign Standard中找不到我需要基于的查询的用户档案字段。**

   默认情况下， nms:recipient表中的20个字段会与Campaign Standard同步。 请参阅同步字段的详细列表。 您需要在Campaign Standard中检索的任何其他字段都必须由您的顾问进行映射和配置。

   要确保要使用的字段可用，您可以检查 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   此外，默认情况下，附加到收件人并存储在与nms:recipients相关的表中的所有数据都不会同步到Campaign Standard。

   为了仍然能够使用相关数据，您可以在Campaign v7中执行定位，并添加其他数据，如 [同步受众](../../integrations/using/synchronizing-audiences.md) 部分，或者您可以咨询顾问以探索自定义可能性。

* **我在Campaign v7中使用的是除默认nms:recipient之外的其他用户档案维度，如何将它们与Campaign Standard同步？**

   Campaign Standard使用唯一定位资源，该资源名为 **用户档案**. “Campaign Standard连接”功能的基本实施在Campaign v7收件人和Campaign Standard配置文件之间提供了默认映射。

   如果您在Campaign v7中使用其他用户档案维度，或者如果您使用多个用户档案维度，则所有用户档案都必须映射到Campaign Standard用户档案。 请咨询您的顾问，以满足此特殊需求。

* **我想通过工作流与Campaign Standard共享用户档案列表，但无法在Campaign Standard中找到我的受众**.

   受众可在 **[!UICONTROL Audiences]** 菜单Campaign Standard。 它们在 **[!UICONTROL List update]** 活动。 这些文件夹受实施期间定义的文件夹映射的约束。

   首先需要检查的是工作流是否已完成且没有错误。 如果您发现 **[!UICONTROL List update]** 活动，则表示与Campaign Standard的同步可能失败。 要查看有关错误情况的更多详细信息，请转到 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. 此文件夹包含由 **[!UICONTROL List update]** 活动执行。

   另外，请确保 **[!UICONTROL Share with ACS]** 选项 **[!UICONTROL List update]** 活动，且工作流已正确执行。

   请注意，列表中包含的收件人用户档案必须已在执行工作流之前与Campaign Standard同步。 与Campaign Standard共享后，列表的收件人将与Campaign Standard用户档案进行协调，这意味着他们必须存在于该位置。 列表中无法与Campaign Standard中的用户档案协调的收件人将被忽略。

   如果您共享由用户档案构成的列表，并且没有与Campaign Standard同步，则会在Campaign Standard中创建一个无法使用的空查询受众。

* **我收到通知，告诉我同步工作流处于错误状态。 我该怎么办？**

   通过测试连接，在Campaign Standard和Campaign v7中检查外部帐户配置：

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard。
   * **[!UICONTROL acsDefaultAccount]** 在Campaign v7中。

* **在Campaign v7和Campaign Standard之间映射文件夹时，我没有可用的安全组。**

   您需要首先从 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. 此操作会检查Campaign Standard中可用的安全组。 同步后，您可以在配置文件夹映射时找到安全组。

* **我无法在Campaign Standard中编辑用户档案、受众或登陆页面。 这是什么意思？**

   从Campaign v7同步的资源在Campaign Standard中处于只读模式，以确保数据一致性。 如果您需要编辑其中一个元素，可以在Campaign v7中执行该操作，然后在Campaign Standard中复制所做的更改。
