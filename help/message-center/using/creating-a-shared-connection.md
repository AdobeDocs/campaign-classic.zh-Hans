---
solution: Campaign Classic
product: campaign
title: 创建共享连接
description: 创建共享连接
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 2%

---


# 创建共享连接{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* 对消息中心模式在控件或模式 [上使用的技术工作流](../../message-center/using/technical-workflows.md) ，进行的执行实例扩展需要在Adobe Campaign事务消息模块使用的其他实例上进行复制。
>* 控制实例和执行实例必须安装在不同的计算机上。 他们不能共享同一活动实例。

>



## 控制实例 {#control-instance}

如果您有分解的架构，则需要指定链接到执行实例的控制实例并连接它们。 事务性消息模板部署到执行实例。 控制实例与执行实例之间的连接是通过配置类型外部帐户 **[!UICONTROL Execution instance]** 来创建的。 您需要创建任意数量的外部帐户，以便创建任意数量的执行实例。

>[!NOTE]
>
>当执行实例被多个控制实例使用时，数据可以按文件夹和运算符进行划分。 有关此内容的详细信息，请参 [阅使用多个控制实例](#using-several-control-instances)。

要创建执行实例类型外部帐户，请应用以下步骤：

1. Go to the **[!UICONTROL Administration > Platform > External accounts]** folder.
1. 选择附带执行实例的现成外部帐户类型之一，右键单击并选择 **[!UICONTROL Duplicate]** 。

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根据您的需求更改标签。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 选择选 **[!UICONTROL Enabled]** 项以使外部帐户可操作。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安装执行实例的服务器的地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帐户必须与操作符文件夹中定义的消息中心代理匹配。 默认情况下，Adobe Campaign提供的现成帐户为 **[!UICONTROL mc]** 。

   ![](assets/messagecenter_create_extaccount_005.png)

1. 输入操作符文件夹中定义的帐户密码。

   >[!NOTE]
   >
   >要避免每次登录实例时输入口令，可在执行实例中指定控制实例的IP地址。 For more on this, refer to [Execution instance](#execution-instance).

1. 指定执行实例要使用的恢复方法。

   要恢复的控制实例由执行实例转发到事务性消息，以添加到和事件存档。

   ![](assets/messagecenter_create_extaccount_007.png)

   通过使用HTTP/HTTPS访问的Web服务或通过联合数据访问(联合数据访问)模块进行数据收集。

   >[!NOTE]
   >
   >请注意，在使用HTTP联合数据访问时，仅支持使用PostgreSQL执行实例库的。 不支持MSSQL或Oracle数据库。

   如果控制实例可以直接访问执行实例的数据库，则建议使用第二种方法。 否则，选择Web服务访问。 要指定的联合数据访问帐户与在控制实例上创建的各种执行实例的数据库连接一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   有关联合数据访问(联合数据访问)的详细信息，请参阅 [访问外部数据库](../../installation/using/about-fda.md)。

1. 单 **[!UICONTROL Test the connection]** 击以确保控制实例和执行实例已关联。

   ![](assets/messagecenter_create_extaccount_006.png)

1. 每个执行实例必须与标识符相关联。 此标识符可以通过使用部署向导(请参阅标识执行实例 [)手动分配给每个执行实例，也可以通过单击该中的“](../../message-center/using/identifying-execution-instances.md)初始化连接 **** ”按钮自动分配给每个控制实例。

   ![](assets/messagecenter_create_extaccount_006bis.png)

## 执行实例 {#execution-instance}

为了控制实例能够连接到执行实例而无需提供密码，只需在“消息中心”访问权限部分输入控制实例 **的IP** 地址。 但是，默认情况下禁止使用空密码。

要使用空密码，请转到执行实例，并定义一个限制为提供事件的信息系统的IP地址的安全区。 此安全区域必须允许空密码并接受类 `<identifier> / <password>` 型连接。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

>[!NOTE]
>
>当执行实例被多个控制实例使用时，数据可以按文件夹和运算符进行划分。 有关此内容的详细信息，请参 [阅使用多个控制实例](#using-several-control-instances)。

1. 转到执行实例()中的运算符文 **[!UICONTROL Administration > Access management > Operators]** 件夹。
1. 选择“消 **息中心** ”代理。

   ![](assets/messagecenter_operator_001.png)

1. 选择选 **[!UICONTROL Edit]** 项卡， **[!UICONTROL Access rights]** 单击，然后单击链 **[!UICONTROL Edit the access parameters...]** 接。

   ![](assets/messagecenter_operator_002.png)

1. 在窗 **[!UICONTROL Access settings]** 口中，单 **[!UICONTROL Add a trusted IP mask]** 击链接并添加控制实例的IP地址。

   ![](assets/messagecenter_operator_003.png)

## 使用多个控制实例 {#using-several-control-instances}

您可以与各种控制实例共享执行群集。 此类型的架构需要以下配置。

例如，如果公司管理两个品牌，每个品牌都有其自己的控制实例: **控制1** 和 **控制2**。 还使用了两个执行实例。 您需要为每个控制实例输入不同的消息中心运算符：Control **1实例** 的mc1运 **算符和Control** 2实例的 **mc2** 运 **算符** 的mc2运算符。

在所有执行实例的树中，为每个运算符创建一个文件&#x200B;**夹(文件夹** 1 **和文件夹2**)，并限制每个运算符对其文件夹的数据访问。

### 配置控制实例 {#configuring-control-instances}

1. 在“控 **制1** ”控制实例中 **，为每个执行实例创建一个外部帐户，并在每个** 外部帐户中输入mc1运算符。 之 **后** ，将在所有执行实例上创建mc1运算符(请参 [阅配置执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_1.png)

1. 在“控 **制2** ”控制实例中 **，为每个执行实例创建一个外部帐户，并在每个** 外部帐户中输入mc2运算符。 之 **后** ，将在所有执行实例上创建mc2运算符(请参 [阅配置执行实例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >有关配置控制实例的详细信息，请参阅 [控制实例](#control-instance)。

### 配置执行实例 {#configuring-execution-instances}

要使用多个控制实例，必须对所有执行实例执行此配置。

1. 在节点中，为每个运算符创建一个 **[!UICONTROL Administration > Production > Message Center]** 文件夹： **文件夹** 1和 **文件夹2**。 有关创建文件夹和视图的详细信息，请参 [阅平台](../../platform/using/access-management.md#folders-and-views)。

   ![](assets/messagecenter_multi_control_3.png)

1. 复制默 **认提供的** Message Center **运算符(mc** )，创建mc1 **和mc2**&#x200B;运算符。 For more on creating operators, refer to [this section](../../platform/using/access-management.md#operators).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1和** mc2 **运营商必****[!UICONTROL Message Center execution]** 须拥有权限，并且无法访问Adobe Campaign客户端控制台。 操作员必须始终与安全区域链接。 如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

1. 对于每个运算符，选 **[!UICONTROL Restrict to information found in sub-folders of]** 中相应的文件夹(**mc1运算符的文件夹1** , **mc1运算符的文件夹2** , mc2运算符的文件夹2 ******** )。

   ![](assets/messagecenter_multi_control_5.png)

1. 为每个操作员授予其文件夹的读写权限。 为此，请右键单击文件夹并选择 **[!UICONTROL Properties]** 。 然后，选择 **[!UICONTROL Security]** 选项卡并添加相关运算符(**Mc1** 表示Folder **1,mc2** 表示Folder **2******)。 确保选中 **[!UICONTROL Read/Write data]** 这些框。

   ![](assets/messagecenter_multi_control_6.png)

