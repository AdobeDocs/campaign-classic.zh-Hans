---
product: campaign
title: 生产疑难解答
description: 了解与Adobe Campaign配置、监控、升级过程、数据处理和数据库维护过程相关的生产故障排除过程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 78c65b31-e3d9-4a46-a101-26f35d00a4ee
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 18%

---

# 生产疑难解答{#troubleshooting}



本节包含与Adobe Campaign一般生产问题相关的故障诊断过程，例如投放和工作流执行、监控、数据库维护、连接等。

## 常见问题和一般问题 {#common-and-general-issues}

* 此 [页面](../../production/using/modules-and-frequent-issues.md) 显示列出的模块中遇到的最常见问题。
* 此 [页面](../../production/using/workflow-execution.md) 列出了在遇到工作流执行问题时应遵循的常见疑难解答过程。
* 此 [页面](../../production/using/lost-password.md) 详细说明如何更改或恢复丢失的密码。
* 此 [页面](../../production/using/console-update.md) 详细介绍在停用相应选项时如何重新激活控制台更新请求。

## 投放疑难解答 {#delivery-troubleshooting}

在投放遇到问题时，可以执行特定操作：
* [投放能力问题](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [图像显示问题](../../production/using/image-display-issues.md)
* [缺少图像](../../production/using/images-missing.md)
* [临时文件问题](../../production/using/temporary-files.md) (*仅内部部署托管模型*)

**相关主题**：

[交付性能问题](../../delivery/using/delivery-performances.md)

## 使用日志 {#working-with-logs}

以下是一些有助于改善日志体验的提示：

* [日志精度](../../production/using/log-precision.md)
* [跟踪日志问题](../../production/using/tracking-logs-issues.md)

## 数据库问题 {#database-issues}

了解如何通过阅读以下章节来解决性能问题：

* [数据库性能](../../production/using/database-performances.md)
* [Oracle 数据库的编码](../../production/using/encoding-of-the-oracle-database.md)

## 连接改进 {#connection-improvements}

如果您遇到连接问题，请通过以下一些方法来修复这些问题：

* [连接失败](../../production/using/failure-to-connect.md)
* [连接阈值](../../production/using/connection-thresholds.md)

## 技术故障排除 {#technical-troubleshooting}

请转到以下部分，以了解更多具体问题：

* [Linux 中的堆栈跟踪](../../production/using/stack-trace-in-linux.md)
* [JSP 行为](../../production/using/jsp-behavior.md)
* [找到Tomcat版本](../../production/using/locate-tomcat-version.md)
