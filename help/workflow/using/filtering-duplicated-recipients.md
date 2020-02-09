---
title: 过滤重复的收件人
description: 了解如何过滤重复的收件人
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 过滤重复的收件人 {#filtering-duplicated-recipients}

在此示例中，我们希望过滤在分发中显示两次或两次以上的收件人，以恢复重复的配置文件。

要创建此示例，请应用以下步骤：

1. 在工作流中拖 **[!UICONTROL Query]** 放活动，然后打开该活动。
1. 单击 **[!UICONTROL Edit query]** 并将目标和筛选维设置为 **[!UICONTROL Recipients]**。

   ![](assets/query_recipients_1.png)

1. 为分发日志中存在的目标收件人定义以下过滤条件。 在“ **表达式”列中选择“日志(broadlog)”****，选择“运算符收件人传送列中存** 在的信息”(如 **“运****** 算符收件人传送列)。

   ![](assets/query_recipients_2.png)

1. 定义以下筛选条件以定位您的分发。 在“ **[!UICONTROL Internal name]** 表达式”列和“运 **[!UICONTROL equal to]** 算符”列中选择。
1. 在值列中，添加目标交付的内部名称。

   ![](assets/query_recipients_3.png)

1. 使用运 **[!UICONTROL AND]** 算符，重复相同的操作以定位其他交付。

   ![](assets/query_recipients_4.png)

您的出站过渡包含在传送中目标的重复收件人。
