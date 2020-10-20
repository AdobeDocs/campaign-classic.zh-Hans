---
title: 在活动中安装中间源服务器
description: 本节详细介绍了中间源服务器在活动中的安装和配置
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
translation-type: tm+mt
source-git-commit: 270c86a8a15ebe38907be258aed9d245d2a49b6d
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 0%

---


# 中间源服务器{#mid-sourcing-server}

本节详细介绍中间源服务器的安装和配置以及允许第三方以中间源模式发送消息的实例的 **部署** 。

“中间源”体系结构在中间源部署 [中呈现](../../installation/using/mid-sourcing-deployment.md)。

安装中间源服务器与正常安装服务器的过程相同（请参阅标准配置）。 它是一个独立实例，具有自己的投放库，可用于运行数据。 简而言之，它包含一个额外的配置，允许远程实例在投放模式下通过它执行中间源。

## 安装和配置实例的步骤 {#steps-for-installing-and-configuring-an-instance}

### 安装和配置实例的先决条件 {#prerequisites-for-installing-and-configuring-an-instance}

* 应用程序服务器上的JDK。
* 访问应用程序服务器上的数据库服务器。
* 防火墙配置为打开HTTP(80)或HTTPS(443)端口至中间源服务器。

以下过程使用单个中间源服务器详细描述配置。 也可以使用多台服务器。 同样，也可以从内部配置发送某些消息（例如，工作流通知）。

### 安装和配置应用程序服务器以进行中间源部署 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安装过程与独立实例的安装过程相同。 请参阅 [安装和配置（单台计算机）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

但是，您必须应用以下各项：

* 在第 **5步**，必须禁用mta **(投放** )和 **inMail** （弹回邮件）模块。 但 **wfserver** （工作流）模块必须保持激活状态。

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

* 步 **骤** 6 **、****9** 和10不是必需的。
* 在步骤 **12** 和 **13期间**，您需要在连接URL中指示8080端口（因为控制台直接与Tomcat通信，而不是通过Web服务器通信）。 URL变为 [http://console.campaign.net:8080](http://console.campaign.net)。 在第13 **步**，选择包 **[!UICONTROL Issue towards Mid-sourcing]** 以及要安装的包。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >技术投放的默认路由会通过中间源自动替换为电子邮件路由。

### 安装和配置中间源服务器 {#installing-and-configuring-the-mid-sourcing-server}

在客户端控制台中，找到使 **用中间源路由帐** 户的电子邮件中间源 **(在** /Administration/外部帐户/文件夹中)。 使用承载 **中间源服**&#x200B;务器的服 **务器**&#x200B;提供商提 **供的信息填充服** 务器、帐户、 **密码和** 镜像页面URL设置的URL。 测试连接。

>[!NOTE]
>
>中 **间源补充发射器** 选项创建两 **个中间源** 工作流。 该进程默认每1小时20分钟运行一次，并在投放服务器上收集中间源信息。

## 部署中间源服务器 {#deploying-a-mid-sourcing-server}

1. 安装应用程序服务器：

   >[!CAUTION]
   >
   >如果您安装中间源服务器并要安装额外的Adobe Campaign模块，我们建议使用投放模块，而不是活动模块。

   按照与标准部署相同的过程操作，只选择选 **[!UICONTROL Mid-sourcing platform]** 项。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 在中间源模式下接收的配置

   设置提交帐户密码：在/ **中间源/访问管理/Operators** /文件夹 **中，远程实例使** 用mid运算符进行中间源模式的提交。 您必须为此运算符设置口令，并将其授予提交实例的管理员。

   中间源 **平台选项** ，创建用于存储已提交投放的默认文件夹以及执行提交的默认运算符。

## 多路复用中间源服务器 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>仅本地环境支持多路复用。

中间源实例可由多个提交实例共享。 这些实例中的每个实例都需要与中间源库中的运算符相关联。 要在中间源服务器上创建第二个帐户：

1. 在节点中创建 **[!UICONTROL Mid-sourcing > Deliveries]** 与默认中间源帐户关联的文件夹(例如：prod)。
1. 在节点中创建 **[!UICONTROL Mid-sourcing > Deliveries]** 与帐户同名的文件夹(例如：acception_test)。

   ![](assets/mid_recette_account.png)

1. 在 **[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;中，创建新帐户。

   ![](assets/mid_recette_user_create.png)

1. 在选项 **[!UICONTROL Access rights]** 卡中，为此操作员授予中间源提 **交组的权** 限。 此访问权限在中可用 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**。

   ![](assets/mid_recette_user_rights.png)

1. 选择选 **[!UICONTROL Restrict to data in the sub-folders of]** 项并选择投放文件夹，以将此运算符限制为中间源投放文件夹。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用以下命令重新启动Web模块： **nlserver重新启动web**。

必须更改serverConf.xml文件中的中间源服务器设置。 必须在现有行的“具有IP地址的关联管理”部分中添加以下行：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

“@name”属性必须遵守以下规则：

**&#39;marketing_account_operator_name&#39;。&#39;关联名称。&#39;关联组**

“marketing_account_operator_name”与在中间源实例中声明的中间源帐户的内部名称相关。

“关联名”与给予关联的任意名称相关。 此名称必须唯一。 授权字符 `[a-z]``[A-Z]``[0-9]`为。 目的是声明一组公共IP地址。

“关联组”关联在每个投放中使用的目标映射中声明的子关联。 最后一部分包括“.” 如果没有子关联，则忽略。 授权字符 `[a-z]``[A-Z]``[0-9]`为。

您必须停止并重新启动服务器，才能将修改考虑在内。

## 在中间源服务器上配置跟踪 {#configuring-tracking-on-a-mid-sourcing-server}

**配置中间源服务器**

1. 转到“运算符”并选择运算符 **[!UICONTROL mid]**。
1. 在选项卡 **[!UICONTROL Frontal servers]** 中，输入跟踪服务器连接参数。

   要创建跟踪实例，请输入跟踪服务器的URL、跟踪服务器内部帐户密码以及该实例的名称、其密码以及与其关联的DNS掩码。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 输入连接参数后，单击 **[!UICONTROL Confirm the configuration]**。
1. 如有必要，请指定投放中包含的图像的存储位置。 为此，请从下拉列表中选择一种发布模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果选择该选 **[!UICONTROL Tracking server(s)]** 项，图像将复制到中间源服务器上。

**配置客户平台**

1. 转到外部中间源路由帐户。
1. 在选项卡 **[!UICONTROL Mid-Sourcing]** 中，指定中间源服务器连接参数。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 单击以确认配置 **[!UICONTROL Test the connection]**。
1. 声明在中间源服务器上引用的跟踪实例：

   单击链接 **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   指定跟踪实例的名称，然后确认与跟踪服务器的连接。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果消息投放由多个中间源服务器管理，请选择选项并指 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 定不同的服务器。

![](assets/s_ncs_install_midsourcing_tracking04.png)

