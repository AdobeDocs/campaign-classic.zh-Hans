---
solution: Campaign Classic
product: campaign
title: 重新生成模式
description: 重新生成模式
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# 重新生成模式{#regenerating-schemas}

修改模式并保存修改时，将自动生成扩展模式。 但是，您可能需要手动重新生成模式以应用修改。 操作步骤：

1. 选择需要重新生成的模式。
1. 右键单击并选择&#x200B;**[!UICONTROL Actions > Regenerate selected schemas...]**。
1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;以确认并启动进程。

然后，您可以在“预览”和“文档”选项卡中检查生成模式的结构。 有关详细信息，请参阅[原则](../../configuration/using/data-schemas.md#principles)部分。

>[!NOTE]
>
>如果需要强制重新生成所有模式（例如，要解决反向链接中的某些依赖关系问题），可以从Adobe Campaign应用程序服务器启动以下命令：
>
>**nlserver config -postupgrade -instance:&#39;&lt;instance_name>&#39; -force**
>
>然后，必须重新启动Adobe Campaign应用程序服务器，并断开／重新连接至客户端控制台。
