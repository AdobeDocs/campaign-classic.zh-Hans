---
product: campaign
title: 重新生成架构
description: 了解如何重新生成Campaign模式
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# 重新生成架构{#regenerating-schemas}

![](../../assets/v7-only.svg)

修改架构并保存修改时，将自动生成扩展架构。 但是，您可能需要手动重新生成架构以应用修改。 操作步骤：

1. 选择需要重新生成的架构。
1. 右键单击并选择 **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. 单击 **[!UICONTROL OK]** 以确认并启动该进程。

然后，您可以在预览和文档选项卡中检查生成的架构的结构。 有关更多信息，请参阅 [原则](../../configuration/using/data-schemas.md#principles) 中。

>[!NOTE]
>
>如果需要强制重新生成所有模式（例如，为了解决反向链接中的某些依赖关系问题），可以从Adobe Campaign应用程序服务器中启动以下命令：
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>然后，必须重新启动Adobe Campaign应用程序服务器，并断开/重新连接到客户端控制台。
