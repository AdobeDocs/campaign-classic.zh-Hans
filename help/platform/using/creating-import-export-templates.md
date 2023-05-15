---
product: campaign
title: 创建导入和导出模板
description: 了解如何在Campaign中创建导入和导出模板
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1180e664-5ead-4d5d-b1c3-6fe397c1f3a2
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 22%

---

# 创建导入和导出模板 {#creating-import-export-templates}



导入和导出模板存储在 **[!UICONTROL Resources > Templates > Job templates]** Adobe Campaign树的目录。

默认情况下，此目录中存在三个导入模板和一个导出模板。不得更改它们。

* 本机模板 **[!UICONTROL Import denylist]** 已配置为导入已添加到的电子邮件地址列阻止列表表。

* 的 **[!UICONTROL New text import]** 和 **[!UICONTROL New text export]** 模板允许您从头开始配置导入或导出。

![](assets/s_ncs_user_export_wizard_template_create.png)

您可以复制现有模板以创建自己的模板，或通过 **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** 菜单。

然后，配置模板的过程与以下章节中介绍的过程相同：

* [配置导入作业](../../platform/using/executing-import-jobs.md)
* [配置导出作业](../../platform/using/executing-export-jobs.md)
