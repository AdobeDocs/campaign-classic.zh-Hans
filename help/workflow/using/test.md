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
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 测试{#test}

“测 **试类型** ”活动激活满足与其关联的条件的第一个过渡。 如果未满足任何条件，并且激活 **[!UICONTROL Use the default fork]** 了该选项，则将激活默认过渡。

条件是必须计算为“true”或“false”的JavaScript表达式。 要输入表达式，请单击条件名称右侧的图标，然后选择 **[!UICONTROL Edit...]**。

![](assets/edit_test.png)

有关通过工作流JavaScript可访问的应用程序服务器的所有其他JavaScript函数和SOAP方法的详细信息，请参阅 [JSAPI文档](http://docs.campaign.adobe.com/doc/AC/en/jsapi/p-1.html)。

您还可以直接从此编辑器插入变量。

可以从活动属性编辑窗口添加、删除或排序条件，也可以从转换中进行修改。

如果计算的结果要被不同的条件重用，则可以在活动的初始化脚本中计算它。 结果必须存储在要由条件脚本访问的任务的变量中(task.vars.xxx)。
