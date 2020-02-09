---
title: 在Adobe Campaign Classic中安装中间采购服务器
description: 本节详细介绍了Adobe Campaign Classic中中间采购服务器的安装和配置。
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# 中间采购服务器{#mid-sourcing-server}

本节详细介绍了中间采购服务器的安装和配置，以及允许第三方在中间采购模式下发送消息的实 **例的部署** 。

“中间采购”架构在中间采购部 [署中呈现](../../installation/using/mid-sourcing-deployment.md)。

安装中间采购服务器与以常规方式安装服务器的过程相同（请参阅标准配置）。 它是一个独立实例，其自己的数据库可用于运行提交。 简而言之，它包含额外的配置，允许远程实例在中间采购模式下通过它执行交付。

## 安装和配置实例的步骤 {#steps-for-installing-and-configuring-an-instance}

### 安装和配置实例的先决条件 {#prerequisites-for-installing-and-configuring-an-instance}

* 应用程序服务器上的JDK。
* 访问应用程序服务器上的数据库服务器。
* 防火墙配置为打开HTTP(80)或HTTPS(443)端口至中间来源服务器。

以下过程详细描述了使用单一中间采购服务器的配置。 还可以使用多台服务器。 同样，也可以从内部配置发送某些消息（例如，工作流通知）。

### 安装和配置应用程序服务器以进行中间资源部署 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安装过程与独立实例的安装过程相同。 请参阅 [安装和配置（单台计算机）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

但是，您必须应用以下内容：

* 在第 **5步**，必须禁用mta **（传送）和** inMail **** （弹回邮件）模块。 但 **wfserver** （工作流）模块必须保持激活状态。

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

* 步 **骤6**、 **9****和** 10不是必需的。
* 在步骤 **12** 和 **13中**，您需要在连接URL中指示8080端口（因为控制台直接与Tomcat通信，而不是通过Web服务器通信）。 该URL变为 [http://console.campaign.net:8080](http://console.campaign.net)。 在第13 **步中**，选择包 **[!UICONTROL Issue towards Mid-sourcing]** 以及要安装的包。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >技术交付的默认传送方式会自动替换为通过中间采购的电子邮件传送方式。

### 安装和配置中间包服务器 {#installing-and-configuring-the-mid-sourcing-server}

在客户端控制台中，找到使 **用中间来源补充中间来源补充帐户** (在 **/Administration/External accounts/** folder中)的电子邮件传送方式。 使用托管中间 **服务器的服务器提供商提供的信息，填充** Server **、** account **、** password **和** Mirror page URL Sourcing服务器的URL。 测试连接。

>[!NOTE]
>
>中间 **来源补充发射器** ，可创建两 **个中间来源补充工作流** 。 该过程默认每1小时20分钟运行一次，并在中间采购服务器上收集交付信息。

## 部署中间采购服务器 {#deploying-a-mid-sourcing-server}

1. 安装应用程序服务器：

   >[!CAUTION]
   >
   >如果您安装了中间采购服务器并要安装额外的Adobe Campaign模块，我们建议使用“交付”模块，而不要使用“营销活动”模块。

   按照与标准部署相同的步骤操作，只选择选 **[!UICONTROL Mid-sourcing platform]** 项。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 用于在中部采购模式下接收的配置

   设置提交帐户密码：在 **/Mid-sourcing/Access Management/Operators/** /文件夹中，远程实例将 **mid** 运算符用于在中间采购模式下提交。 您必须为此操作符设置口令，并将其交给提交实例的管理员。

   “中 **部采购平台** ”选项创建用于存储已提交的交付的默认文件夹以及执行提交的默认操作员。

## 多路传输中间源服务器 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>仅本地环境支持多路复用。

中间采购实例可由多个提交实例共享。 每个实例都需要与中间采购数据库中的运算符相关联。 要在中间采购服务器上创建第二个帐户，请执行以下操作：

1. 在节点中创建一 **[!UICONTROL Mid-sourcing > Deliveries]** 个将与默认中间采购帐户关联的文件夹(例如：prod)。
1. 在节点中创建 **[!UICONTROL Mid-sourcing > Deliveries]** 与帐户同名的文件夹(例如：acception_test)。

   ![](assets/mid_recette_account.png)

1. 在 **[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;中，创建新帐户。

   ![](assets/mid_recette_user_create.png)

1. 在选项卡 **[!UICONTROL Access rights]** 中，为此运营商授予中间采 **购提交组的权限** 。 此访问权限在中可用 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**。

   ![](assets/mid_recette_user_rights.png)

1. 选择选 **[!UICONTROL Restrict to data in the sub-folders of]** 项并选择交货文件夹，以将此运算符限制到中部来源补充交货文件夹。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用以下命令重新启动Web模块：无 **服务器重新启动Web**。

必须更改serverConf.xml文件中的中间采购服务器设置。 必须在现有行的“IP地址相关性管理”部分中添加以下行：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

“@name”属性必须遵守以下规则：

**&#39;marketing_account_operator_name&#39;。&#39;affinity_name&#39;.&#39;affinity_group&#39;**

“marketing_account_operator_name”与在中间采购实例中声明的中间采购帐户的内部名称相关。

“affinity_name”与赋予关联的任意名称相关。 此名称必须唯一。 授权字符 `[a-z]``[A-Z]``[0-9]`为。 其目的是声明一组公共IP地址。

“affinity_group”与在每个分发中使用的目标映射中声明的子关联相关。 最后一部分包括“.” 如果没有子关联，则忽略该属性。 授权字符 `[a-z]``[A-Z]``[0-9]`为。

您必须停止并重新启动服务器，才能将修改考虑在内。

## 在中间采购服务器上配置跟踪 {#configuring-tracking-on-a-mid-sourcing-server}

**配置中间采购服务器**

1. 转到“运算符”并选择该运算符 **[!UICONTROL mid]**。
1. 在选项卡 **[!UICONTROL Frontal servers]** 中，输入跟踪服务器连接参数。

   要创建跟踪实例，请输入跟踪服务器的URL、跟踪服务器内部帐户密码以及该实例的名称、其密码以及与其关联的DNS掩码。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 输入连接参数后，单击 **[!UICONTROL Confirm the configuration]**。
1. 如果需要，请指定要存储传送中包含的图像的位置。 为此，请从下拉列表中选择一种发布模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果选择该选 **[!UICONTROL Tracking server(s)]** 项，则图像将复制到中间采购服务器上。

**配置客户平台**

1. 转至外部中间采购工艺路线帐户。
1. 在选项卡 **[!UICONTROL Mid-Sourcing]** 中，指定中间采购服务器连接参数。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 单击以确认配置 **[!UICONTROL Test the connection]**。
1. 声明在中间采购服务器上引用的跟踪实例：

   单击链接 **[!UICONTROL Use this platform as a platform to access the tracking servers]**,

   指定跟踪实例的名称，然后确认与跟踪服务器的连接。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果消息传送将由多个中部采购服务器管理，请选择相应选项并指 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 定不同的服务器。

![](assets/s_ncs_install_midsourcing_tracking04.png)

