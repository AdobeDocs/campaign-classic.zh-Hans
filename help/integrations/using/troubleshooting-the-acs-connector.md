---
title: ACS连接器故障诊断
seo-title: ACS连接器故障诊断
description: ACS连接器故障诊断
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 0%

---


# Troubleshooting the ACS Connector{#troubleshooting-the-acs-connector}

根据您的实施，您可能会面临几个常见问题。

* **Campaign Standard与活动v7之间的UI有何差异？**

   Campaign Standard和活动v7的工作方式非常相似。 大多数概念是相同的，但在某些情况下，方法可能略有不同。 以下是ACS连接器上下文中可能不同的一些概念：

<table> 
 <thead> 
  <tr> 
   <th> 活动v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 收件人(或任何其他用户档案维)<br /> </td> 
   <td> profiles<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> 活动工作流，定位工作流<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> 运营<br /> </td> 
   <td> campaigns<br /> </td> 
  </tr> 
  <tr> 
   <td> web applications<br /> </td> 
   <td> landing pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 自定义表和模式扩展<br /> </td> 
   <td> 自定义资源和资源扩展<br /> </td> 
  </tr> 
  <tr> 
   <td> 种子成员<br /> </td> 
   <td> test profiles<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **我的活动v7实例的收件人未同步或对Campaign Standard可见。**

   本案可能因以下原因而发生：

   * 收件人刚在活动v7中创建或更新。 同步每15分钟触发一次。 这意味着更新的收件人或新创建的Campaign Standard在下次同步后在中可见。
   * 您的实施可以设置为仅同步来自特定文件夹的收件人。 来自其他文件夹的收件人不会同步。
   * 收件人可以同步，但在Campaign Standard中不可见。 检查文件夹权限映射。

* **我找不到用户档案字段，我需要用Campaign Standard来查询。**

   默认情况下， nms:收件人表中的20个字段与Campaign Standard同步。 请参阅同步字段的详细列表。 您需要以Campaign Standard检索的任何其他字段都必须由顾问进行映射和配置。

   要确保要使用的字段可用，您可以从中检查用户档案资源定义 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**。

   此外，默认情况下，与收件人连接并存储在与nms:收件人相关的表中的所有数据都不会同步到Campaign Standard。

   要仍然能够使用相关活动，您可以在v7中执行定位并添加其他数据(如同 [步受众部分所述](../../integrations/using/synchronizing-audiences.md) )，也可以咨询顾问探索自定义可能性。

* **我使用的用户档案维不是活动v7中的默认nms:收件人，我如何将它们与Campaign Standard同步？**

   Campaign Standard使用一个名为用户档案的唯一定位 **资源**。 Campaign Standard连接功能的基本实现提供了活动v7收件人和Campaign Standard用户档案之间的默认映射。

   如果您在活动v7中使用其他用户档案维，或者如果您使用多个维，则必须用Campaign Standard用户档案映射这些维。 请咨询您的顾问，以解决此特定需求。

* **我希望通过工作流与Campaign Standard共享一列表用户档案，但找不到我的Campaign Standard**。

   受众位于菜单的 **[!UICONTROL Audiences]** Campaign Standard中。 它们具有在活动中指定 **[!UICONTROL List update]** 的活动v7工作流的标签。 它们受实施过程中定义的文件夹映射的约束。

   首先要检查的是工作流是否已完成并且没有错误。 如果您注意到活动上出 **[!UICONTROL List update]** 现错误，则表示与Campaign Standard的同步可能失败。 要查看有关出错情况的更多详细信息，请转 **[!UICONTROL Administration]** 到> **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此文件夹包含由工作流执行触发的 **[!UICONTROL List update]** 同步活动。

   另外，请确保在活动 **[!UICONTROL Share with ACS]** 中选中了该选 **[!UICONTROL List update]** 项，并且工作流已正确执行。

   请注意，在执行工作流之前，收件人中包含的用户档案必须已与Campaign Standard同步。 与Campaign Standard共享后，列表的收件人与Campaign Standard用户档案进行协调，这意味着它们必须存在于。 将忽略列表中无法与Campaign Standard中的用户档案进行协调的收件人。

   如果您共享由用户档案构成的列表，并且如果没有与Campaign Standard同步，则它会在Campaign Standard中创建一个无法使用的空查询受众。

* **我收到通知，告知我同步工作流处于错误状态。 我该怎么办？**

   通过测试连接，检查Campaign Standard和活动v7中的外部帐户配置：

   * **[!UICONTROL acsDefaultRelayAccount]** campaign standard。
   * **[!UICONTROL acsDefaultAccount]** 在活动v7中。

* **在活动v7和Campaign Standard之间映射文件夹时，我没有可用的安全组。**

   您首先需要从中同步安全组 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**。 此操作检查Campaign Standard中可用的安全组。 同步后，您可以在配置文件夹映射时找到安全组。

* **我无法编辑用户档案、受众或Campaign Standard。 这是什么意思？**

   从活动v7同步的资源处于Campaign Standard的只读模式，以确保数据一致性。 如果您需要编辑其中一个元素，您可以在v7活动中进行编辑，然后在Campaign Standard中复制更改。

