---
solution: Campaign Classic
product: campaign
title: 管理权限
description: 管理权限
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---


# 管理权限{#managing-rights}

如果Adobe Campaign操作员不是管理员，则工作流操作员需要访问权限才能创建、执行或修改管理员。

通常，对工作流执行操作的操作员需要访问包含在各种活动(收件人、收件人列表、订阅、投放等)中使用的数据的文件，并可能访问其子文件。

它们还必须映射到与它们将影响的已命名权限(收件人导入、文件访问、融合、SQL脚本执行等)所执行的工作流一致的。

有关管理操作符和权限的详细信息，请参阅此[部分](../../platform/using/access-management.md)。

## 运算符组{#operator-groups}

以下运算符组与工作流相关联：

* 通过&#x200B;**[!UICONTROL Workflow execution]**&#x200B;组，您可以控制目标工作流的执行和批准：名为right的工作流将映射到此组的运算符。 除了对工作流文件的访问权限外，对数据执行所有操作都需要此选项。 默认情况下，**[!UICONTROL Workflow execution]**&#x200B;组对标准定位工作流文件和工作流模板具有只读访问权限。 此组中的操作员也具有对待处理批准文件的读写权限。
* **[!UICONTROL Workflow supervisors]**&#x200B;组允许操作员管理工作流批准。
* 用于访问活动工作流的&#x200B;**[!UICONTROL Operation Managers]**&#x200B;组。

## 已命名权限{#named-rights}

只有名为right的WORKFLOW特定于工作流:它允许您创建、开始和停止工作流。 要使命名权限适用，必须对工作流文件具有读取权限。 对于定位工作流,**[!UICONTROL Profiles and Targets]**&#x200B;文件上的读取权限是必需的。

## 工作流执行帐户{#workflow-execution-account}

您可以配置要在工作流模板级别使用的执行帐户。 通过执行帐户，您可以直接将授权映射到工作流，而不管启动执行的Adobe Campaign运算符。 默认情况下，每个工作流都由启动该工作流的操作员权限执行。

要将执行帐户映射到工作流，请转到工作流模板的列表，然后右键单击链接到该工作流的模板。 选择&#x200B;**[!UICONTROL Action > Change execution account...]**，然后选择要使用的帐户。
