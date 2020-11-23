---
solution: Campaign Classic
product: campaign
title: '"用例：配置字段替换"'
description: '"用例：配置字段替换"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---


# 用例：配置字段替换{#use-case-configuring-the-field-substitution}

随机字段替换允许您将收件人列表中的值归因为用户在投放中使用此值时种子地址为空(例如：名称、城市等)。

通过此替换，您可以在创建投放时节省时间：替代不会手动将所需的值添加到种子地址，而是在投放所针对的收件人列表中随机恢复此值，并将其应用于种子地址。

## 上下文 {#context}

在这种情况下，“我的 **在线图书馆** ”网站希望根据客户喜爱的文学类型给客户打折。

该投放经理已将一个与喜爱的类型关联的个性化领域集成到其电子邮件中。 他想用一些种子地址。 这些种子地址的表中包含个性化字段，但没有保存任何值。

要使用随机字段替换，您必须具有：

* 一个投放，一个个性化字段,
* 根据 **种子地址中** 使用的个性化字段修改其模式的投放。

## 创建投放 {#step-1---creating-a-delivery}

创建投放的步骤详见创建 [电子邮件投放部分](../../delivery/using/creating-an-email-delivery.md) 。

在此示例中，投放管理器已创建Newsletter。

![](assets/dlv_seeds_usecase_24.png)

## 编辑种子地址模式 {#editing-the-seed-addresses-data-schema}

有关如何修改数据模式的说明，请参见一节。

在此示例中，种子地址数据模式使用从收件人数据模式创建的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此明细列表允许用户指定客户最喜爱的文学类型。

要使此模式修改在种子地址输入表单中 **可查看**，您必须更新它。 请参阅更 [新输入表单部分](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) 。

## 配置个性化 {#configuring-personalization}

1. 打开投放。

   在此示例中，投放具有两个个性化字段:收件人的 **名字** ,收件人最喜 **欢的文学类型**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 配置投放列表和种子地址。 请参阅 [确定目标群](../../delivery/using/steps-defining-the-target-population.md)。

   在本例中，用户选择其最喜 **欢的文学流派是** Sci-Fi的用户作为主要目标群体。

   ![](assets/dlv_seeds_usecase_26.png)

   用户向种子地址添加投放。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >有关链接的详 **[!UICONTROL Edit the dynamic condition...]** 细信息，请参 [阅使用案例：选择标准种子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)。

1. 单击选 **[!UICONTROL Preview]** 项卡，然后选择种子地址以测试个性化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一个个性化字段是空的。 由于种子地址没有此字段的预览，因此HTML内容地址无法显示值。

   在投放时进行 **场的随机替换**。

1. 单击 **[!UICONTROL Send]** 按钮。
1. 分析投放，然 **后确认投放**。

   种子地址会在其收件箱中接收投放。

   现场个性化非常有效。

   ![](assets/dlv_seeds_usecase_08.png)
