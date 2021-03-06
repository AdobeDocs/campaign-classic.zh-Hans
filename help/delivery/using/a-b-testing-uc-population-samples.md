---
product: campaign
title: 配置人群样本
description: 了解如何通过专用用例执行A/B测试
feature: A/B Testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 7%

---

# 配置人群样本 {#step-2--configuring-population-samples}

![](../../assets/common.svg)

## 配置查询活动 {#configuring-the-query-activity}

* 双击 **[!UICONTROL Query]** 活动。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击 **[!UICONTROL Edit query]** 链接，然后选择要定位的收件人。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 链接 **[!UICONTROL Query]** 活动 **[!UICONTROL Split]** 活动。

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置拆分活动 {#configuring-the-split-activity}

此活动允许您创建多个群体：接收投放A的，接收投放B的，以及剩余的群体。 通过使用随机选择，您只能定位每个投放的一部分群体。

1. 创建群体A:

   * 双击 **[!UICONTROL Split]** 活动。

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在现有选项卡中，将标签更改为群体A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 选择 **[!UICONTROL Limit the selected records]** 选项。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 单击 **[!UICONTROL Edit]** 链接，选择 **[!UICONTROL Activate random sampling]**，然后单击 **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 将阈值设置为10%，然后单击 **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 创建群体B:

   * 单击 **[!UICONTROL Add]** 为群体B创建新选项卡。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 将群体限制为以前的10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余群体：

   * 转到 **[!UICONTROL General]** 选项卡。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 选择 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此群体既不包含A也不包含B，然后单击 **[!UICONTROL OK]** 来关闭活动。

      ![](assets/use_case_abtesting_createrecipients_013.png)

您现在可以创建两个投放模板。 [了解详情](a-b-testing-uc-delivery-templates.md)).
