---
product: campaign
title: '"用例：配置字段替换"'
description: '"用例：配置字段替换"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---

# 用例：配置字段替换{#use-case-configuring-the-field-substitution}

随机字段替换允许您将收件人列表中的某个值归因于用户在投放中使用此值时的种子地址为空(例如：名称、城市等)。

通过此替换，您可以在创建投放时节省时间：替代不会手动将所需值添加到种子地址，而是会在投放所定向的收件人列表中随机取回此值，并将其应用于种子地址。

## 上下文 {#context}

在此用例中，网站&#x200B;**My online library**&#x200B;希望根据客户喜爱的文学流派向客户发放折扣。

投放管理器已将与收藏流派关联的个性化字段集成到其电子邮件中。 他想用一些种子地址。 这些种子地址的表中包含个性化字段，但那里没有保存任何值。

要使用随机字段替换，您必须具有：

* 包含一个或多个个性化字段的投放，
* 根据投放中使用的个性化字段修改&#x200B;**数据架构**&#x200B;的种子地址。

## 创建投放{#step-1---creating-a-delivery}

有关创建投放的详细步骤，请参见[创建电子邮件投放](../../delivery/using/creating-an-email-delivery.md)一节。

在此示例中，投放管理器已创建新闻稿。

![](assets/dlv_seeds_usecase_24.png)

## 编辑种子地址数据架构{#editing-the-seed-addresses-data-schema}

有关如何修改数据架构的说明，请参阅一节。

在本例中，种子地址数据架构采用从收件人数据架构创建的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此枚举允许用户指定其客户最喜爱的文学类型。

若要在种子地址&#x200B;**输入表单**&#x200B;中查看此数据架构修改，必须更新它。 请参阅[更新输入表单](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form)一节。

## 配置个性化{#configuring-personalization}

1. 打开投放。

   在本例中，投放有两个个性化字段：收件人的&#x200B;**名字**&#x200B;和收件人的&#x200B;**最喜爱的文学流派**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 配置投放列表和种子地址。 请参阅[识别目标群体](../../delivery/using/steps-defining-the-target-population.md)。

   在本例中，用户选择&#x200B;**最喜爱的文学流派**&#x200B;为Sci-Fi的用户作为主要目标群体。

   ![](assets/dlv_seeds_usecase_26.png)

   用户向投放添加种子地址。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >有关&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;链接的更多信息，请参阅[用例：根据条件](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)选择种子地址。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡，然后选择种子地址以测试个性化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一个个性化字段为空。 由于种子地址没有此字段的数据，因此HTML内容预览无法显示值。

   在投放&#x200B;**时，将执行**&#x200B;字段的随机替换。

1. 单击 **[!UICONTROL Send]** 按钮。
1. 分析投放，然后&#x200B;**确认投放**。

   种子地址会在其收件箱中接收投放内容。

   字段个性化非常有效。

   ![](assets/dlv_seeds_usecase_08.png)
