---
product: campaign
title: 读取列表
description: 了解有关读取列表工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 读取列表{#read-list}

在工作流中处理的数据可以来自列表，其中数据已预先准备或结构化（在先前的分段或文件上传之后）。

利用&#x200B;**[!UICONTROL Read list]**&#x200B;活动，可复制工作流工作表列表中的数据，如查询中的数据。 然后，可以在整个工作流中访问该选件。

要处理的列表可以显式指定，由脚本计算，或根据&#x200B;**[!UICONTROL Read list]**&#x200B;活动中选择的选项和定义的参数动态本地化。

![](assets/list_edit_select_option_01.png)

如果未明确指定该列表，则必须提供一个用作模板以查找其结构的列表。

![](assets/s_advuser_list_template_select.png)

配置列表选择后，您可以使用&#x200B;**[!UICONTROL Edit query]**&#x200B;选项添加过滤器，以保留下一个工作流的一部分群体。

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>要在读取列表活动中创建过滤器，相关列表必须是“文件”类型。

可以通过主页的&#x200B;**[!UICONTROL Profiles and Targets > Lists]**&#x200B;链接直接在Adobe Campaign中创建列表。 也可以使用&#x200B;**[!UICONTROL List update]**&#x200B;活动在工作流中创建活动。

**示例：排除发送地址列表**

以下示例允许您使用电子邮件地址列表从电子邮件投放目标中排除。

![](assets/s_advuser_list_read_sample_1.png)

**New Contacts**&#x200B;文件夹中包含的用户档案必须通过投放操作进行定位。 要从目标中排除的电子邮件地址会存储在外部列表中。 在我们的示例中，排除项只需要提供关于电子邮件地址的信息。

1. **New Contacts**&#x200B;文件夹选择查询必须允许您加载所选用户档案的电子邮件地址，以便能够与列表中的信息保持一致。

   ![](assets/s_advuser_list_read_sample_0.png)

1. 在此，列表存储在&#x200B;**Lists**&#x200B;文件夹中，并计算其标签。

   ![](assets/s_advuser_list_read_sample_2.png)

1. 要从主目标中排除外部列表的电子邮件地址，必须配置排除活动，并指定&#x200B;**New Contacts**&#x200B;文件夹包含要保留的数据。 此集与来自排除活动的任何其他集客集之间的联合数据将从目标中删除。

   ![](assets/s_advuser_list_read_sample_3.png)

   排除规则在编辑工具的中心部分中配置。 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以定义要应用的排除类型。

   您可以根据活动的传入过渡的数量定义多个排除项。

1. 在&#x200B;**[!UICONTROL Exclusion set]**&#x200B;字段中，选择&#x200B;**[!UICONTROL Read list]**&#x200B;活动：此活动中的数据将从主集中排除。

   在我们的示例中，我们在连接上排除了以下项：列表中包含的数据将通过包含电子邮件地址的字段与主集的数据协调一致。 要配置连接，请在&#x200B;**[!UICONTROL Change dimension]**&#x200B;字段中选择&#x200B;**[!UICONTROL Joins]**。

   ![](assets/s_advuser_list_read_sample_4.png)

1. 然后，在两组（源和目标）中选择与电子邮件地址对应的字段。 随后将链接这些列，并且目标中将排除电子邮件地址列表中的收件人。
