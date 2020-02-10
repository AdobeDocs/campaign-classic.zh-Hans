---
title: 创建分发模板
seo-title: 创建分发模板
description: 创建分发模板
seo-description: null
page-status-flag: never-activated
uuid: 8ceae1ec-9e02-4809-aa8b-1e6bd7790950
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 0e67d9dd-3ee8-4c06-98a4-3a2c644b6c0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Creating a delivery template{#creating-a-delivery-template}

## 将现有交付转换为模板 {#converting-an-existing-delivery-to-a-template}

交付可以转换为模板以执行新的重复交付操作。 要将分发转换为模板，请从分发列表中选择它，可通过树的节 **[!UICONTROL Campaign management]** 点访问该模板。

Right-click and select **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

此操作会根据选定的分发创建分发模板。 您必须输入保存该模板的文件夹（在字段中），以及创建基于此模板创建的提交的文件夹(在字 **[!UICONTROL Folder]****[!UICONTROL Execution folder]** 段中)。

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

有关配置模式的详细信息，请参 [阅将模板关联到分发](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery)。

## 创建新模板 {#creating-a-new-template}

要配置传送模板，请执行以下步骤：

1. 打开营销活动浏览器。
1. 在“资源 **”文件夹** ，依次选择“模 **板** ” **、“交**&#x200B;付模板”。

   ![](assets/delivery_template_1.png)

1. 单击 **工具栏** 中的“新建”以创建新的分发模板。

   ![](assets/delivery_template_2.png)

1. 修改文 **件夹的** “标签” **和“内部** ”名称。
1. 保存模板并重新打开它。
1. 单击“ **属性** ”按钮，然后根据您的要求修改值。

   ![](assets/delivery_template_3.png)

1. 在“常规 **** ”选项卡中，确认或更改在“执行文件夹 **”、“文件夹**”和“路由选 ******** 择”下拉菜单中选择的位置。

   ![](assets/delivery_template_4.png)

1. 使用电子邮件 **主题和目标人群** ，填写“电子邮件参数”类别。
1. 添加 **HTML内容** ，以个性化模板，您可以显示镜像页面链接和取消订阅链接。
1. 选择“预 **览** ”选项卡。 在“测 **试个性化** ”下拉菜单中，选择“收件 **人** ”以预览模板作为所选配置文件。

   ![](assets/delivery_template_5.png)

1. 单击“ **保存**”。 您的模板现已准备好用于分发。

>[!NOTE]
>
>为避免出现配置错误，建议您复制本机模板并更改其属性，而不要创建新模板。
