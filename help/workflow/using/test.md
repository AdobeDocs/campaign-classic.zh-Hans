---
title: 测试
seo-title: 测试
description: 测试
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 6%

---


# 测试{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

条件是必须计算为“true”或“false”的JavaScript表达式。 要输入表达式，请单击条件名称右侧的图标，然后选择 **[!UICONTROL Edit...]**。

![](assets/edit_test.png)

有关可通过工作流JavaScript访问的应用程序服务器的所有附加JavaScript函数和SOAP方法的详细信息，请参阅 [JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

您还可以直接从此编辑器插入变量。 有关如何使用变量的详细信息，请参 [阅本节](../../workflow/using/javascript-scripts-and-templates.md#variables)。

条件可以从活动属性编辑窗口添加、删除或排序，也可以从过渡修改。

如果计算结果要被不同的条件重用，则可以在活动的初始化脚本中计算它。 结果必须存储在要由条件脚本访问的任务的变量中(任务.vars.xxx)。
