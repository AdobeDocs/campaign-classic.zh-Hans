---
product: campaign
title: “用例：配置字段替换”
description: “用例：配置字段替换”
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 2%

---

# 用例：配置字段替换{#use-case-configuring-the-field-substitution}



通过随机字段替换，您可以将收件人列表中的值归因于用户在投放中使用此值时为空的种子地址（例如：名称、城市等）。

通过此替换，您可以在创建投放时节省时间：替换不会将所需值手动添加到种子地址，而是会在投放定向的收件人列表中随机恢复此值，并将其应用于种子地址。

## 上下文 {#context}

在此使用案例中，网站&#x200B;**我的在线库**&#x200B;希望根据客户喜爱的文学流派向客户发送折扣。

投放经理已将与最喜爱的流派关联的个性化字段集成到其电子邮件中。 目的是使用一些种子地址：这些种子地址在表中具有个性化字段，但没有保存任何值。

要使用随机字段替换，您必须具有：

* 包含一个或多个个性化字段的投放，
* 根据投放中使用的个性化字段修改了&#x200B;**数据架构**&#x200B;的种子地址。

## 创建投放 {#step-1---creating-a-delivery}

有关创建投放的详细步骤，请参见[创建电子邮件投放](creating-an-email-delivery.md)一节。

在本例中，投放经理已创建了新闻稿。

![](assets/dlv_seeds_usecase_24.png)

## 编辑种子地址数据架构 {#editing-the-seed-addresses-data-schema}

有关如何修改数据模式的说明详情，请参阅部分。

在此示例中，种子地址数据模式采用从收件人数据模式创建的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此枚举允许用户指定其客户最喜爱的文学流派。

要使此数据架构修改可在种子地址&#x200B;**输入表单**&#x200B;中查看，您必须更新它。 请参阅[更新输入表单](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form)部分。

## 配置个性化 {#configuring-personalization}

1. 打开投放。

   在此示例中，投放有两个个性化字段：收件人的&#x200B;**名字**&#x200B;和收件人的&#x200B;**最喜爱的文学流派**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 配置投放列表和种子地址。 请参阅[识别目标群体](steps-defining-the-target-population.md)。

   在此示例中，用户选择其&#x200B;**最喜爱的文学流派**&#x200B;是科幻小说的用户作为主要目标群体。

   ![](assets/dlv_seeds_usecase_26.png)

   用户向投放添加种子地址。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >有关&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;链接的详细信息，请参阅[用例：根据条件选择种子地址](use-case-selecting-seed-addresses-on-criteria.md)。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，然后选择一个种子地址以测试个性化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一个个性化字段为空。 由于种子地址没有此字段的数据，因此HTML内容预览无法显示值。

   在投放时&#x200B;**执行了字段的随机替换**。

1. 单击 **[!UICONTROL Send]** 按钮。
1. 分析您的投放，然后&#x200B;**确认投放**。

   种子地址会在收件箱中接收投放。

   字段个性化有效。

   ![](assets/dlv_seeds_usecase_08.png)
