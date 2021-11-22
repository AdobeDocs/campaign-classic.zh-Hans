---
product: campaign
title: '"用例：配置字段替换"'
description: '"用例：配置字段替换"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---

# 用例：配置字段替换{#use-case-configuring-the-field-substitution}

![](../../assets/common.svg)

随机字段替换允许您将收件人列表中的某个值归因于用户在投放中使用此值时的种子地址为空(例如：名称、城市等)。

通过此替换，您可以在创建投放时节省时间：替代不会手动将所需值添加到种子地址，而是会在投放所定向的收件人列表中随机取回此值，并将其应用于种子地址。

## 上下文 {#context}

在此用例中，站点 **我的在线图书馆** 想根据客户最喜爱的文学风格，给客户打折。

投放管理器已将与收藏流派关联的个性化字段集成到其电子邮件中。 目的是使用一些种子地址：这些种子地址的表中包含个性化字段，但此处未保存任何值。

要使用随机字段替换，您必须具有：

* 包含一个或多个个性化字段的投放，
* 种子地址 **数据模式** 将根据投放中使用的个性化字段进行修改。

## 创建投放 {#step-1---creating-a-delivery}

有关创建投放的详细步骤，请参见 [创建电子邮件投放](creating-an-email-delivery.md) 中。

在此示例中，投放管理器已创建新闻稿。

![](assets/dlv_seeds_usecase_24.png)

## 编辑种子地址数据模式 {#editing-the-seed-addresses-data-schema}

有关如何修改数据架构的说明，请参阅一节。

在本例中，种子地址数据架构采用从收件人数据架构创建的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此枚举允许用户指定其客户最喜爱的文学类型。

要在种子地址中查看此数据模式修改 **输入表单**，则必须更新它。 请参阅 [更新输入表单](use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) 中。

## 配置个性化 {#configuring-personalization}

1. 打开投放。

   在本例中，投放有两个个性化字段：收件人的 **名字** 和收件人的 **最受欢迎的文学流派**.

   ![](assets/dlv_seeds_usecase_25.png)

1. 配置投放列表和种子地址。 请参阅 [确定目标群体](steps-defining-the-target-population.md).

   在本例中，用户会选择 **最受欢迎的文学流派** 是以Sci-Fi为主目标群体。

   ![](assets/dlv_seeds_usecase_26.png)

   用户向投放添加种子地址。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >有关 **[!UICONTROL Edit the dynamic condition...]** 链接，请参阅 [用例：根据条件选择种子地址](use-case--selecting-seed-addresses-on-criteria.md).

1. 单击 **[!UICONTROL Preview]** 选项卡，然后选择种子地址以测试个性化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一个个性化字段为空。 由于种子地址没有此字段的数据，因此HTML内容预览无法显示值。

   执行字段的随机替换 **投放时**.

1. 单击 **[!UICONTROL Send]** 按钮。
1. 分析投放，然后 **确认投放**.

   种子地址会在其收件箱中接收投放内容。

   字段个性化非常有效。

   ![](assets/dlv_seeds_usecase_08.png)
