---
product: campaign
title: 配置实例
description: 了解如何在Adobe Campaign Classic中配置事务性消息传递控制和执行实例
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 1%

---


# 配置实例 {#creating-a-shared-connection}



要使用事务性消息传递功能，您需要配置控制实例和执行实例。 您可以使用以下任一方法：
* [与一个或多个执行实例关联的一个控件实例](#control-instance)
* [多个与多个执行实例关联的控制实例](#using-several-control-instances)

>[!IMPORTANT]
>
>架构扩展影响了[消息中心技术工作流](../../message-center/using/additional-configurations.md#technical-workflows)在事务性消息传递模块使用的其他实例上需要复制控制实例或执行实例上使用的资源。

您还需要指定执行实例并将其连接到控制实例。

本节介绍了配置和连接控制实例和执行实例所需的所有步骤。

>[!IMPORTANT]
>
>控制实例和执行实例必须安装在不同的计算机上。 他们不能共享同一个Campaign实例。

## 配置控制实例 {#control-instance}

若要连接控制实例和执行实例，您首先需要在控制实例&#x200B;**上创建和配置&#x200B;**&#x200B;[!UICONTROL Execution instance]&#x200B;**类型的外部帐户**。 因此，一旦[发布](../../message-center/using/publishing-message-templates.md#template-publication)，事务性消息模板就可以部署到执行实例。

如果您使用多个执行实例，则必须创建与执行实例相同数量的外部帐户。

>[!NOTE]
>
>当多个控制实例使用执行实例时，数据可以按文件夹和运算符划分。 有关详细信息，请参阅[使用多个控件实例](#using-several-control-instances)。

### 创建外部帐户

>[!NOTE]
>
>必须在控制实例&#x200B;**上**&#x200B;执行以下步骤。

要创建&#x200B;**[!UICONTROL Execution instance]**&#x200B;类型的外部帐户，请应用以下内容：

1. 转到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;文件夹。
1. 选择随Adobe Campaign一起提供的现成执行实例类型外部帐户之一，右键单击并选择&#x200B;**[!UICONTROL Duplicate]** 。

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根据需要更改标签。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 选择&#x200B;**[!UICONTROL Enabled]**&#x200B;选项以使外部帐户可运行。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安装执行实例的服务器地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帐户必须与操作员文件夹中定义的消息中心代理匹配。 默认情况下，Adobe Campaign提供的现成帐户为&#x200B;**[!UICONTROL mc]** 。

   ![](assets/messagecenter_create_extaccount_005.png)

1. 输入在operator文件夹中定义的帐户密码。

   >[!NOTE]
   >
   >要避免每次登录实例时都输入密码，可以在执行实例中指定控制实例的IP地址。 有关详细信息，请参阅[配置执行实例](#execution-instance)。

1. 指定执行实例要使用的恢复方法。 要恢复的数据由执行实例转发到控制实例，以添加到事务性消息和事件归档中。

   ![](assets/messagecenter_create_extaccount_007.png)

   数据收集通过使用HTTP/HTTPS访问的Web服务或通过联合数据访问(FDA)模块进行。

   >[!NOTE]
   >
   >请注意，在使用FDA over HTTP时，仅支持使用PostgreSQL数据库的执行实例。 不支持MSSQL或Oracle数据库。

   如果控制实例可以直接访问执行实例的数据库，则建议使用第二种方法(FDA)。 如果没有，请选择Web服务访问。 要指定的FDA帐户与连接到在控制实例上创建的各种执行实例的数据库的时间一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   有关联合数据访问(FDA)的详细信息，请参阅[此部分](../../installation/using/about-fda.md)。

1. 单击&#x200B;**[!UICONTROL Test the connection]**&#x200B;以确保控制实例和执行实例已链接。

   ![](assets/messagecenter_create_extaccount_006.png)

使用多个执行实例时，重复这些步骤以创建与执行实例相同数量的外部帐户。

### 确定执行实例 {#identifying-execution-instances}

每个执行实例必须关联一个唯一标识符，以区分在控制实例上查看每个执行实例时的历史记录。

此标识符可在每个执行实例&#x200B;**上手动归因**。 在这种情况下，必须在每个执行实例&#x200B;**上执行**&#x200B;此步骤。 要实现此目的，请使用部署向导，如下所述：

1. 在执行实例上打开部署向导。
1. 转到&#x200B;**[!UICONTROL Message Center]**&#x200B;窗口。
1. 将所选的标识符分配给实例。

   ![](assets/messagecenter_id_execinstance_001.png)

1. 对每个执行实例重复上述步骤。

标识符也可以是&#x200B;**自动**&#x200B;属性。 为此，请转到&#x200B;**控件实例**，然后单击&#x200B;**[!UICONTROL Initialize connection]**&#x200B;按钮。

![](assets/messagecenter_create_extaccount_006bis.png)

## 配置执行实例 {#execution-instance}

>[!NOTE]
>
>必须在执行实例&#x200B;**上执行以下步骤**。

要将执行实例连接到控制实例，请执行以下步骤。

为了使控制实例能够连接到执行实例而无需提供密码，只需在&#x200B;**消息中心**&#x200B;访问权限部分中输入控制实例的IP地址。 但是，默认情况下禁止空密码。

要使用空密码，请转至执行实例并定义一个安全区域，该区域限制为发送事件的信息系统的IP地址。 此安全区域必须允许空密码并接受`<identifier> / <password>`类型连接。 如需详细信息，请参阅[此小节](../../installation/using/security-zones.md)。

>[!NOTE]
>
>当多个控制实例使用执行实例时，数据可以按文件夹和运算符划分。 有关详细信息，请参阅[使用多个控件实例](#using-several-control-instances)。

1. 在执行实例上，转到operator文件夹( **[!UICONTROL Administration > Access management > Operators]** )。
1. 选择&#x200B;**消息中心**&#x200B;代理。

   ![](assets/messagecenter_operator_001.png)

1. 选择&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡，单击&#x200B;**[!UICONTROL Access rights]**，然后单击&#x200B;**[!UICONTROL Edit the access parameters...]**&#x200B;链接。

   ![](assets/messagecenter_operator_002.png)

1. 在&#x200B;**[!UICONTROL Access settings]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Add a trusted IP mask]**&#x200B;链接并添加控制实例的IP地址。

   ![](assets/messagecenter_operator_003.png)

使用多个执行实例时，对每个执行实例重复这些步骤。

## 使用多个控制实例 {#using-several-control-instances}

您可以与各种控制实例共享执行集群。 此类型的体系结构需要以下配置。

例如，假设您的公司管理两个品牌，每个品牌都有自己的控制实例：**控制1**&#x200B;和&#x200B;**控制2**。 还使用了两个执行实例。 您需要为每个控制实例输入不同的消息中心运算符：**Control 1**&#x200B;实例的&#x200B;**mc1**&#x200B;运算符和&#x200B;**Control 2**&#x200B;实例的&#x200B;**mc2**&#x200B;运算符。

在所有执行实例的树中，为每个操作员（**文件夹1**&#x200B;和&#x200B;**文件夹2**）创建一个文件夹，并限制每个操作员对其文件夹的数据访问。

### 配置控制实例 {#configuring-control-instances}

>[!NOTE]
>
>必须在控制实例&#x200B;**上**&#x200B;执行以下步骤。

1. 在&#x200B;**Control 1**&#x200B;控件实例上，为每个执行实例创建一个外部帐户，并在每个外部帐户中输入&#x200B;**mc1**&#x200B;运算符。 此后将在所有执行实例上创建&#x200B;**mc1**&#x200B;运算符（请参阅[配置执行实例](#configuring-execution-instances)）。

   ![](assets/messagecenter_multi_control_1.png)

1. 在&#x200B;**Control 2**&#x200B;控件实例上，为每个执行实例创建一个外部帐户，并在每个外部帐户中输入&#x200B;**mc2**&#x200B;运算符。 此后将在所有执行实例上创建&#x200B;**mc2**&#x200B;运算符（请参阅[配置执行实例](#configuring-execution-instances)）。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >有关配置控件实例的更多信息，请参阅[此部分](#control-instance)。

### 配置执行实例 {#configuring-execution-instances}

>[!NOTE]
>
>必须在执行实例&#x200B;**上**&#x200B;执行以下步骤。

要使用多个控制实例，必须在所有执行实例上执行此配置。

1. 在&#x200B;**[!UICONTROL Administration > Production > Message Center]**&#x200B;节点中为每个运算符创建一个文件夹： **文件夹1**&#x200B;和&#x200B;**文件夹2**。 有关创建文件夹和视图的详细信息，请参阅[此页面](../../platform/using/access-management-folders.md)。

   ![](assets/messagecenter_multi_control_3.png)

1. 通过复制默认提供的Message Center运算符(**mc**)来创建&#x200B;**mc1**&#x200B;和&#x200B;**mc2**&#x200B;运算符。 有关创建运算符的详细信息，请参阅[此章节](../../platform/using/access-management-operators.md)。

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1**&#x200B;和&#x200B;**mc2**&#x200B;操作员必须具有&#x200B;**[!UICONTROL Message Center execution]**&#x200B;权限，并且他们不能访问Adobe Campaign客户端控制台。 运算符必须始终与安全区域链接。 如需详细信息，请参阅[此小节](../../installation/using/security-zones.md)。

1. 对于每个运算符，选中&#x200B;**[!UICONTROL Restrict to information found in sub-folders of]**&#x200B;框，然后选择相关的文件夹（**mc1**&#x200B;运算符为&#x200B;**文件夹1**，**mc2**&#x200B;运算符为&#x200B;**文件夹2**）。

   ![](assets/messagecenter_multi_control_5.png)

1. 向每个操作员授予对其文件夹的读写权限。 为此，请右键单击该文件夹并选择&#x200B;**[!UICONTROL Properties]** 。 然后选择&#x200B;**[!UICONTROL Security]**&#x200B;选项卡并添加相关运算符（**文件夹1**&#x200B;的&#x200B;**mc1**&#x200B;和&#x200B;**文件夹2**&#x200B;的&#x200B;**mc2**）。 确保选中&#x200B;**[!UICONTROL Read/Write data]**&#x200B;框。

   ![](assets/messagecenter_multi_control_6.png)
