---
product: campaign
title: 配置人群样本
description: 了解如何通过专用用例执行A/B测试
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 6%

---

# AB测试：配置群体示例 {#step-2--configuring-population-samples}

## 配置查询活动 {#configuring-the-query-activity}

* 双击 **[!UICONTROL Query]** 活动。

  ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击 **[!UICONTROL Edit query]** 链接并选择要定位的收件人。

  ![](assets/use_case_abtesting_createrecipients_002.png)

* 链接 **[!UICONTROL Query]** 的活动 **[!UICONTROL Split]** 活动。

  ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置拆分活动 {#configuring-the-split-activity}

利用此活动，可创建多个群体：接收投放A的群体、接收投放B的群体和其余群体。 通过使用随机选择，您可以只定向每次投放的部分群体。

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

   * 与之前一样，将人口限制为10%。

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余群体：

   * 转到 **[!UICONTROL General]** 选项卡。

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * 选择 **[!UICONTROL Generate complement]**。

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此群体既不包括A也不包括B，然后单击 **[!UICONTROL OK]** 以关闭活动。

     ![](assets/use_case_abtesting_createrecipients_013.png)

您现在可以创建这两个投放模板。 [了解详情](a-b-testing-uc-delivery-templates.md)).
