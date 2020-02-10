---
title: 阅读列表
seo-title: 阅读列表
description: 阅读列表
seo-description: null
page-status-flag: never-activated
uuid: 34e28675-f28b-407f-8d60-41a5383af0db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 96a7aea4-4799-4ac7-8dff-666b075a1c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 阅读列表{#read-list}

在工作流中处理的数据可以来自列表，其中数据事先已经准备或结构化（在先前的分段或文件上传之后）。

通过 **[!UICONTROL Read list]** 该活动，您可以从工作流工作台的列表中复制数据，如查询中的数据。 然后，可在整个工作流程中访问它。

可以显式指定要处理的列表，由脚本计算，或根据所选选项和活动中定义的参数动态本地化该列 **[!UICONTROL Read list]** 表。

![](assets/list_edit_select_option_01.png)

如果未明确指定列表，则必须提供一个用作模板的列表以找出其结构。

![](assets/s_advuser_list_template_select.png)

配置列表选择后，您可以使用选项添加过滤器，以 **[!UICONTROL Edit query]** 保留下一个工作流的一部分人群。

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>要能够在读取列表活动中创建过滤器，相关列表必须是“文件”类型。

可通过主页链接直接在Adobe Campaign **[!UICONTROL Profiles and Targets > Lists]** 中创建列表。 还可以使用活动在工作流中创建这些 **[!UICONTROL List update]** 活动。

**示例：排除发送地址列表**

以下示例允许您使用电子邮件地址列表从电子邮件分发目标中排除。

![](assets/s_advuser_list_read_sample_1.png)

“新建联系人”文 **件夹中包含的** “配置文件”必须通过提交操作来定位。 要从目标中排除的电子邮件地址存储在外部列表中。 在我们的示例中，排除时只需要有关电子邮件地址的信息。

1. “新 **联系人** ”文件夹选择查询必须允许您加载选定配置文件的电子邮件地址，以便能够与列表中的信息对齐。

   ![](assets/s_advuser_list_read_sample_0.png)

1. 此处，列表存储在 **Lists文件夹** ，并计算其标签。

   ![](assets/s_advuser_list_read_sample_2.png)

1. 要从主目标中排除外部列表的电子邮件地址，必须配置排除活动并指定 **New Contacts** 文件夹包含要保留的数据。 将从目标中删除此集与来自排除活动的任何其他入站集之间的联合数据。

   ![](assets/s_advuser_list_read_sample_3.png)

   排除规则在编辑工具的中央部分进行配置。 单击 **[!UICONTROL Add]** 按钮以定义要应用的排除类型。

   您可以根据活动的传入过渡的数量定义多个排除。

1. 在字段 **[!UICONTROL Exclusion set]** 中，选择活 **[!UICONTROL Read list]** 动：此活动中的数据将从主集中排除。

   在我们的示例中，我们在连接上有一个排除条件：列表中包含的数据将与包含电子邮件地址的字段中的主集数据协调。 要配置连接，请在字 **[!UICONTROL Joins]** 段中选 **[!UICONTROL Change dimension]** 择。

   ![](assets/s_advuser_list_read_sample_4.png)

1. 然后，选择与两组（源和目标）中的电子邮件地址对应的字段。 随后将链接这些列，并且目标中将不包括电子邮件地址列表中收件人。

