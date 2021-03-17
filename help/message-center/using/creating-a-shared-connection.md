---
solution: Campaign Classic
product: campaign
title: 创建共享连接
description: 创建共享连接
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 2%

---


# 创建共享连接{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* 对[消息中心技术工作流](../../message-center/using/technical-workflows.md)在控件或执行实例上使用的模式进行的模式扩展需要在Adobe Campaign事务消息模块使用的其他实例上进行复制。
>* 控制实例和执行实例必须安装在不同的计算机上。 他们不能共享同一活动实例。

>



## 控制实例{#control-instance}

如果您有一个分解的架构，您需要指定链接到该控制实例的执行实例并连接它们。 事务性消息模板部署到执行实例。 通过配置&#x200B;**[!UICONTROL Execution instance]**&#x200B;类型控制实例，可创建外部帐户与执行实例之间的连接。 您需要创建任意数量的外部帐户，以便创建执行实例。

>[!NOTE]
>
>当执行实例被多个控制实例使用时，数据可以按文件夹和运算符划分。 有关详细信息，请参阅[使用多个控制实例](#using-several-control-instances)。

要创建执行实例类型外部帐户，请应用以下步骤：

1. 转到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;文件夹。
1. 选择附带Adobe Campaign的现成执行实例类型外部帐户之一，右键单击并选择&#x200B;**[!UICONTROL Duplicate]**。

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根据您的需要更改标签。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 选择&#x200B;**[!UICONTROL Enabled]**&#x200B;选项以使外部帐户可操作。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安装执行实例的服务器的地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帐户必须与操作员文件夹中定义的消息中心代理匹配。 默认情况下，Adobe Campaign提供的现成帐户为&#x200B;**[!UICONTROL mc]**。

   ![](assets/messagecenter_create_extaccount_005.png)

1. 输入操作符文件夹中定义的帐户密码。

   >[!NOTE]
   >
   >要避免每次登录实例时输入口令，可以在执行实例中指定控制实例的IP地址。 有关详细信息，请参阅[执行实例](#execution-instance)。

1. 指定要由执行实例使用的恢复方法。

   要恢复的控制实例由执行实例转发到事务性消息，以添加到和事件存档。

   ![](assets/messagecenter_create_extaccount_007.png)

   通过使用HTTP/HTTPS访问的Web服务或通过联合数据访问(联合数据访问)模块进行数据收集。

   >[!NOTE]
   >
   >请注意，在HTTP上使用联合数据访问时，仅支持使用PostgreSQL执行实例库的。 不支持MSSQL或Oracle数据库。

   如果控制实例可以直接访问执行实例的数据库，则建议使用第二种方法。 否则，选择Web服务访问。 要指定的联合数据访问帐户与到在控制实例上创建的各种执行实例的数据库的连接一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   有关联合数据访问(联合数据访问)的详细信息，请参阅[访问外部数据库](../../installation/using/about-fda.md)。

1. 单击&#x200B;**[!UICONTROL Test the connection]**&#x200B;以确保控制实例和执行实例已链接。

   ![](assets/messagecenter_create_extaccount_006.png)

1. 每个执行实例必须与标识符关联。 此标识符可以通过使用部署向导(请参阅[标识执行实例](../../message-center/using/identifying-execution-instances.md))手动分配给每个执行实例，也可以通过单击控制实例中的&#x200B;**初始化连接**&#x200B;按钮自动分配给每个。

   ![](assets/messagecenter_create_extaccount_006bis.png)

## 执行实例{#execution-instance}

为了使控制实例能够连接到执行实例而不必提供密码，只需在&#x200B;**消息中心**&#x200B;访问权限部分中输入控制实例的IP地址。 但是，默认情况下禁止空密码。

要使用空密码，请转到执行实例，并定义一个限制为传送事件的信息系统的IP地址的安全区域。 此安全区域必须允许空密码并接受`<identifier> / <password>`类型连接。 如需详细信息，请参阅[此部分](../../installation/using/security-zones.md)。

>[!NOTE]
>
>当执行实例被多个控制实例使用时，数据可以按文件夹和运算符划分。 有关详细信息，请参阅[使用多个控制实例](#using-several-control-instances)。

1. 转到执行实例(**[!UICONTROL Administration > Access management > Operators]**)中的运算符文件夹。
1. 选择&#x200B;**消息中心**&#x200B;代理。

   ![](assets/messagecenter_operator_001.png)

1. 选择&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡，单击&#x200B;**[!UICONTROL Access rights]**，然后单击&#x200B;**[!UICONTROL Edit the access parameters...]**&#x200B;链接。

   ![](assets/messagecenter_operator_002.png)

1. 在&#x200B;**[!UICONTROL Access settings]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Add a trusted IP mask]**&#x200B;链接并添加控制实例的IP地址。

   ![](assets/messagecenter_operator_003.png)

## 使用多个控制实例{#using-several-control-instances}

您可以与各种控制实例共享执行群集。 此类型的架构需要以下配置。

例如，如果您的公司管理两个品牌，每个品牌都有其自己的控制实例:**控制1**&#x200B;和&#x200B;**控制2**。 还使用了两个执行实例。 您需要为每个控制实例输入不同的消息中心运算符：**Control 1**&#x200B;实例的&#x200B;**mc1**&#x200B;运算符和&#x200B;**Control 2**&#x200B;实例的&#x200B;**mc2**&#x200B;运算符。

在所有执行实例的树中，为每个运算符创建一个文件夹（**文件夹1**&#x200B;和&#x200B;**文件夹2**），并限制每个运算符对其文件夹的数据访问。

### 配置控制实例{#configuring-control-instances}

1. 在&#x200B;**Control 1**&#x200B;控制实例中，为每个执行实例创建一个外部帐户，并在每个外部帐户中输入&#x200B;**mc1**&#x200B;运算符。 此后，将在所有执行实例上创建&#x200B;**mc1**&#x200B;运算符(请参阅[配置执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_1.png)

1. 在&#x200B;**Control 2**&#x200B;控制实例中，为每个执行实例创建一个外部帐户，并在每个外部帐户中输入&#x200B;**mc2**&#x200B;运算符。 此后，将在所有执行实例上创建&#x200B;**mc2**&#x200B;运算符(请参阅[配置执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >有关配置控制实例的详细信息，请参阅[控制实例](#control-instance)。

### 配置执行实例{#configuring-execution-instances}

要使用多个控制实例，必须对所有执行实例执行此配置。

1. 在&#x200B;**[!UICONTROL Administration > Production > Message Center]**&#x200B;节点中，为每个运算符创建一个文件夹：**文件夹1**&#x200B;和&#x200B;**文件夹2**。 有关创建文件夹和视图的详细信息，请参阅[此页](../../platform/using/access-management-folders.md)。

   ![](assets/messagecenter_multi_control_3.png)

1. 通过复制默认提供的消息中心运算符(**mc**)，创建&#x200B;**mc1**&#x200B;和&#x200B;**mc2**&#x200B;运算符。 有关创建运算符的详细信息，请参阅[本节](../../platform/using/access-management-operators.md)。

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 和 **mc2** 运营 **[!UICONTROL Message Center execution]** 商必须拥有权限，不能访问Adobe Campaign客户端控制台。操作员必须始终与安全区域链接。 如需详细信息，请参阅[此部分](../../installation/using/security-zones.md)。

1. 对于每个运算符，选中&#x200B;**[!UICONTROL Restrict to information found in sub-folders of]**&#x200B;框，然后选择相关文件夹（******mc1**&#x200B;运算符的文件夹1和&#x200B;******&lt;mc2**&#x200B;运算符的文件夹2）。

   ![](assets/messagecenter_multi_control_5.png)

1. 为每个操作员授予其文件夹的读写权限。 要执行此操作，请右键单击文件夹，然后选择&#x200B;**[!UICONTROL Properties]**。 然后，选择&#x200B;**[!UICONTROL Security]**&#x200B;选项卡并添加相关运算符（**mc1**&#x200B;用于&#x200B;**文件夹1**&#x200B;和&#x200B;**mc2**&#x200B;用于&#x200B;**文件夹2**）。 确保选中&#x200B;**[!UICONTROL Read/Write data]**&#x200B;框。

   ![](assets/messagecenter_multi_control_6.png)

