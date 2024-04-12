---
product: campaign
title: 重新生成架构
description: 了解如何重新生成Campaign模式
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 2%

---

# 重新生成架构{#regenerating-schemas}

修改架构并保存修改后，将自动生成扩展架构。 但是，可能需要手动重新生成架构以应用修改。 操作步骤：

1. 选择需要重新生成的架构。
1. 右键单击并选择 **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. 单击 **[!UICONTROL OK]** 以确认并启动该流程。

然后，您可以在“预览”和“文档”选项卡中检查生成的架构的结构。 有关详细信息，请参见 [原则](../../configuration/using/data-schemas.md#principles) 部分。

>[!NOTE]
>
>如果需要强制重新生成所有架构（例如解决反向链接中的某些依赖性问题），则可以从Adobe Campaign应用程序服务器中启动以下命令：
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>然后，必须重新启动Adobe Campaign应用程序服务器，并断开与客户端控制台的连接/重新连接。
