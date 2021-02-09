---
solution: Campaign Classic
product: campaign
title: 配置填充示例
description: 了解如何通过专用用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 3%

---


# 配置填充示例{#step-2--configuring-population-samples}

## 配置查询活动{#configuring-the-query-activity}

* 多次-单击&#x200B;**[!UICONTROL Query]**&#x200B;活动。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 单击&#x200B;**[!UICONTROL Edit query]**&#x200B;链接，然后选择要目标的收件人。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 将&#x200B;**[!UICONTROL Query]**&#x200B;活动链接到&#x200B;**[!UICONTROL Split]**&#x200B;活动。

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置拆分活动{#configuring-the-split-activity}

此活动允许您创建多个人群：接收投放A的投放B，以及剩余人口。 使用随机选择，您只能目标每个投放的一部分人口。

1. 创建人口A:

   * 多次-单击&#x200B;**[!UICONTROL Split]**&#x200B;活动。

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在现有选项卡中，将标签更改为填充A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 选择&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 单击&#x200B;**[!UICONTROL Edit]**&#x200B;链接，选择&#x200B;**[!UICONTROL Activate random sampling]**，然后单击&#x200B;**[!UICONTROL Next]**。

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 将阈值设置为10%，然后单击&#x200B;**[!UICONTROL Finish]**。

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 创建人口B:

   * 单击&#x200B;**[!UICONTROL Add]**&#x200B;为人口B创建新选项卡。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 将人口限制为以前的10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 创建剩余人口：

   * 转到 **[!UICONTROL General]** 选项卡。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 选择 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改标签以指定此填充不包括A和B，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;以关闭活动。

      ![](assets/use_case_abtesting_createrecipients_013.png)
