---
product: campaign
title: 加载 (SOAP)
description: 加载 (SOAP)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# 加载 (SOAP){#loading-soap}



>[!CAUTION]
>
>此 **加载(SOAP)** 仅当满足以下条件时，活动才可用 **联合数据访问(FDA)** 模块已安装。 请核实您的许可协议。

此 **加载(SOAP)** 除了使用活动之外， **数据加载(RDBMS)** 在无法直接通过FDA在外部数据库中收集数据时的活动。

操作如下：

1. 选择使用XML示例或WSDL。

   以下示例来自消息中心模块的技术工作流。

   ![](assets/load_soap_002.png)

1. 对于XML示例，请选择一个样例文件。 对文件进行分析，建立结果实例。

   对于WSDL，输入匹配的访问URL，然后生成骨架代码。 系统会自动更新和显示选定的服务和呼叫。

   ![](assets/soap_load_003.png)

1. 选择 **[!UICONTROL Click here to view and edit analysis results]** 以指定每个标识的列。

   ![](assets/soap_load_001.png)

   如果要更新示例，请选择 **[!UICONTROL Re-analyze the example]**.

   您还可以通过以下方式个性化列数据的格式 **[!UICONTROL Advanced parameters]** 链接。 有关格式化导入数据的更多信息，请参阅此 [部分](../../platform/using/executing-import-jobs.md).

1. 您可以使用行号作为标识符和/或指定SOAP调用返回多个元素。
1. 根据函数输入以下选项卡脚本：

   * **[!UICONTROL Initialization]**：建立SOAP连接。
   * **[!UICONTROL Iteration]**：执行对SOAP服务的调用。 此函数的返回必须是一个与示例或WSDL的说明兼容的XML对象。

      此选项卡的代码将由Adobe Campaign在循环中调用，直到返回空的XML对象。

   * **[!UICONTROL Finalization]**：关闭连接和/或释放在处理期间创建的其他资源。
