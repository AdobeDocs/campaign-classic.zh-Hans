---
product: campaign
title: 配置人群样本
description: 了解如何通过专用用例执行A/B测试
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 7%

---

# 配置人群样本 {#step-2--configuring-population-samples}



## 配置查询活动 {#configuring-the-query-activity}

* 双击 **[!UICONTROL Query]** 活动。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击 **[!UICONTROL Edit query]** 链接并选择要定位的收件人。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 链接 **[!UICONTROL Query]** 的活动 **[!UICONTROL Split]** 活动。

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置拆分活动 {#configuring-the-split-activity}

通过此活动，可创建多个群体：接收投放A的群体、接收投放B的群体和其余群体。 通过使用随机选择，您可以只定向每次投放的部分群体。

1. 创建群体A：

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

1. 创建群体B：

   * 单击 **[!UICONTROL Add]** 为群体B创建新选项卡。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 与以前一样，将人口限制在10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余群体：

   * 转到 **[!UICONTROL General]** 选项卡。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 选择 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此群体既不包括A也不包括B，然后单击 **[!UICONTROL OK]** 以关闭活动。

      ![](assets/use_case_abtesting_createrecipients_013.png)

您现在可以创建这两个投放模板。 [了解详情](a-b-testing-uc-delivery-templates.md)).
