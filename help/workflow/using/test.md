---
solution: Campaign Classic
product: campaign
title: 测试
description: 进一步了解测试工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---


# 测试{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

条件是必须计算为“true”或“false”的JavaScript表达式。 要输入表达式，请单击条件名称右侧的图标，然后选择 **[!UICONTROL Edit...]**。

![](assets/edit_test.png)

有关可通过工作流JavaScript访问的应用程序服务器的所有附加JavaScript函数和SOAP方法的详细信息，请参阅 [JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

您还可以直接从此编辑器插入变量。 有关如何使用变量的详细信息，请参 [阅本节](../../workflow/using/javascript-scripts-and-templates.md#variables)。

条件可以从活动属性编辑窗口添加、删除或排序，也可以从过渡修改。

如果计算结果要被不同的条件重用，则可以在活动的初始化脚本中计算它。 结果必须存储在要由条件脚本访问的任务的变量中(任务.vars.xxx)。
