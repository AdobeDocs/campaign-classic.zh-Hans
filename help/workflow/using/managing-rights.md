---
product: campaign
title: 管理工作流权限
description: 了解如何管理工作流权限
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 管理工作流权限{#managing-rights}

如果Adobe Campaign操作员不是管理员，则需要拥有创建、执行或修改工作流的访问权限。

通常，对工作流执行操作的操作员需要访问包含各种活动（收件人、收件人列表、订阅、投放等）期间所用数据的文件，可能还需要访问其子文件。

还必须将这些权限映射到与工作流执行的操作（收件人导入、文件访问、融合、SQL脚本执行等）一致的命名权限。

有关管理运算符和权限的更多信息，请参阅此[部分](../../platform/using/access-management.md)。

## 运算符组{#operator-groups-wf}

以下运算符组与工作流关联：

* 通过&#x200B;**[!UICONTROL Workflow execution]**&#x200B;组，您可以控制定向工作流的执行和批准：名为权限的工作流已映射到此组的运算符。 除了对数据文件的访问权限之外，工作流上的所有操作都需要此参数。 默认情况下，**[!UICONTROL Workflow execution]**&#x200B;组对标准定向工作流文件和工作流模板具有只读访问权限。 此组中的操作员也具有对待批准文件的读写权限。
* **[!UICONTROL Workflow supervisors]**&#x200B;组允许操作员管理工作流批准。
* 用于访问营销活动工作流的&#x200B;**[!UICONTROL Operation Managers]**&#x200B;组。

## 命名权限{#named-rights}

只有名为权限的工作流才特定于工作流：它允许您创建、启动和停止工作流。 需要具有工作流文件的读取权限，才能适用命名权限。 对于定位工作流，需要在&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;文件上具有读取权限。

## 工作流执行帐户{#workflow-execution-account}

您可以配置要在工作流模板级别使用的执行帐户。 执行帐户允许您直接将授权映射到工作流，而不考虑开始执行的Adobe Campaign运算符。 默认情况下，每个工作流都使用启动该工作流的操作员的权限执行。

要将执行帐户映射到工作流，请转到工作流模板列表，然后右键单击链接到工作流的模板。 选择&#x200B;**[!UICONTROL Action > Change execution account...]**，然后选择要使用的帐户。
