---
title: 重新生成模式
seo-title: 重新生成模式
description: 重新生成模式
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 8%

---


# 重新生成模式{#regenerating-schemas}

修改模式并保存修改时，将自动生成扩展模式。 但是，您可能需要手动重新生成模式以应用修改。 操作步骤：

1. 选择需要重新生成的模式。
1. 右键单击并选择 **[!UICONTROL Actions > Regenerate selected schemas...]** 。
1. 单击 **[!UICONTROL OK]** 以确认并启动该流程。

然后，您可以在“预览”和“文档”选项卡中检查生成模式的结构。 For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>如果需要强制重新生成所有模式（例如，要解决反向链接中的某些依赖关系问题），可以从Adobe Campaign应用程序服务器启动以下命令：
>
>**nlserver config -postupgrade -instance:`&lt;instance name>&#39; -force**
>
>然后，必须重新启动Adobe Campaign应用程序服务器，并断开／重新连接至客户端控制台。
