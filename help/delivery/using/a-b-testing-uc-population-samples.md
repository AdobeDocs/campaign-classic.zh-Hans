---
product: campaign
title: 配置人群样本
description: 了解如何通过专用用例执行A/B测试
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 4%

---

# AB测试：配置群体示例 {#step-2--configuring-population-samples}

## 配置查询活动 {#configuring-the-query-activity}

* 双击&#x200B;**[!UICONTROL Query]**&#x200B;活动。

  ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击&#x200B;**[!UICONTROL Edit query]**&#x200B;链接并选择要定位的收件人。

  ![](assets/use_case_abtesting_createrecipients_002.png)

* 将&#x200B;**[!UICONTROL Query]**&#x200B;活动链接到&#x200B;**[!UICONTROL Split]**&#x200B;活动。

  ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置“拆分”活动 {#configuring-the-split-activity}

利用此活动，可创建多个群体：接收投放A的群体、接收投放B的群体和其余群体。 通过使用随机选择，您可以只定向每次投放的部分群体。

1. 创建群体A：

   * 双击&#x200B;**[!UICONTROL Split]**&#x200B;活动。

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在现有选项卡中，将标签更改为群体A。

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * 选择&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项。

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * 单击&#x200B;**[!UICONTROL Edit]**&#x200B;链接，选择&#x200B;**[!UICONTROL Activate random sampling]**，然后单击&#x200B;**[!UICONTROL Next]**。

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * 将阈值设置为10%，然后单击&#x200B;**[!UICONTROL Finish]**。

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. 创建群体B：

   * 单击&#x200B;**[!UICONTROL Add]**&#x200B;为群体B创建新选项卡。

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * 与之前一样，将人口限制为10%。

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余群体：

   * 转到&#x200B;**[!UICONTROL General]**&#x200B;选项卡。

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * 选择 **[!UICONTROL Generate complement]**。

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此群体既不包括A也不包括B，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;以关闭活动。

     ![](assets/use_case_abtesting_createrecipients_013.png)

您现在可以创建这两个投放模板。 [了解详情](a-b-testing-uc-delivery-templates.md))。
