---
product: campaign
title: 创建导入和导出模板
description: 了解如何在Campaign中创建导入和导出模板
feature: Templates
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1180e664-5ead-4d5d-b1c3-6fe397c1f3a2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 22%

---

# 创建导入和导出模板 {#creating-import-export-templates}



导入和导出模板存储在中 **[!UICONTROL Resources > Templates > Job templates]** Adobe Campaign树的目录。

默认情况下，此目录中存在三个导入模板和一个导出模板。不得更改它们。

* 本机模板 **[!UICONTROL Import denylist]** 列入阻止列表已配置为导入添加到的电子邮件地址列表。

* 此 **[!UICONTROL New text import]** 和 **[!UICONTROL New text export]** 模板允许您从头开始配置导入或导出。

![](assets/s_ncs_user_export_wizard_template_create.png)

您可以复制现有模板以创建自己的模板，或通过创建新模板 **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** 菜单。

然后，配置模板的过程与以下部分中显示的过程相同：

* [配置导入作业](../../platform/using/executing-import-jobs.md)
* [配置导出作业](../../platform/using/executing-export-jobs.md)
