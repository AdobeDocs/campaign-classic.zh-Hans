---
product: campaign
title: 在Campaign中安装中间源服务器
description: 本节详细介绍Campaign中中间源服务器的安装和配置
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# 中间源服务器{#mid-sourcing-server}



本节详细介绍中间源服务器的安装和配置，以及允许第三方在 **中间源** 模式。

“中间源”架构在 [中间源部署](../../installation/using/mid-sourcing-deployment.md).

安装中间源服务器的过程与以正常方式安装服务器的过程相同（请参阅标准配置）。 它是一个独立实例，其自己的数据库可用于运行投放。 简而言之，它包含额外的配置，以允许远程实例在中间源模式下通过它执行投放。

>[!CAUTION]
>
>设置中间源服务器后， [同步工作流](../../workflow/using/about-technical-workflows.md) 首次运行时，请确保未更新中间源外部帐户的内部名称。

## 安装和配置实例的步骤 {#steps-for-installing-and-configuring-an-instance}

### 安装和配置实例的先决条件 {#prerequisites-for-installing-and-configuring-an-instance}

* 应用程序服务器上的JDK。
* 访问应用程序服务器上的数据库服务器。
* 防火墙配置为打开HTTP(80)或HTTPS(443)端口到中间源服务器。

以下步骤使用单个中间源服务器详细描述配置。 也可以使用多个服务器。 同样，也可以从内部配置发送某些消息（例如，工作流通知）。

### 安装和配置应用程序服务器以进行中间源部署 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安装过程与独立实例的安装过程相同。 请参阅 [安装和配置（单台计算机）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

但是，您必须应用以下内容：

* 步骤 **5**，则必须禁用 **mta** （投放）及 **inMail** （退回邮件）模块。 的 **wfserver** （工作流）模块必须保持激活状态。

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

   如需详细信息，请参阅[此部分](../../installation/using/configuring-campaign-server.md#enabling-processes)。

* 步骤 **6**, **9** 和 **10** 没必要。
* 步骤期间 **12** 和 **13**，则需要在连接URL中指示8080端口（因为控制台直接与Tomcat通信，而不是通过Web服务器）。 URL将变为 `http://console.campaign.net:8080`. 步骤期间 **13**，选择 **[!UICONTROL Issue towards Mid-sourcing]** 包以及要安装的包。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >技术投放的默认路由会自动替换为通过中间源的电子邮件路由。

### 安装和配置中间源服务器 {#installing-and-configuring-the-mid-sourcing-server}

在客户端控制台中，找到 **使用中间源的电子邮件路由** 中间源帐户(在 **/管理/外部帐户/** 文件夹)。 填充 **服务器的URL**, **帐户**, **密码** 和 **镜像页面URL** 设置，其中包含托管中间源服务器的服务器提供商提供的信息。 测试连接。

>[!NOTE]
>
>的 **mid-sourcingEmitter** 选项创建2 **中间源** 工作流。 默认情况下，每1小时20分钟运行一次该进程，并在中间源服务器上收集投放信息。

## 部署中间源服务器 {#deploying-a-mid-sourcing-server}

1. 安装应用程序服务器：

   >[!CAUTION]
   >
   >如果您安装中间源服务器并想要安装额外的Adobe Campaign模块，我们建议您使用“投放”模块，而不是Campaign模块。

   按照与标准部署相同的步骤操作，仅选择 **[!UICONTROL Mid-sourcing platform]** 选项。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 用于在中间源模式下接收的配置

   设置提交帐户密码：在 **/中间源/访问管理/运算符/** 文件夹， **mid** 运算符由远程实例用于在中间源模式下提交。 您必须为此运算符设置一个密码，并将其提供给提交实例的管理员。

   的 **中间源平台** 选项会创建用于存储已提交投放的默认文件夹，以及执行提交的默认运算符。

## 多路复用中间源服务器 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>仅内部部署环境支持多路复用。

中间源实例可能由多个提交实例共享。 每个实例都需要与中间源数据库中的运算符关联。 要在中间源服务器上创建第二个帐户，请执行以下操作：

1. 在中创建文件夹 **[!UICONTROL Mid-sourcing > Deliveries]** 与默认中间源帐户关联的节点(例如：prod)。
1. 在中创建文件夹 **[!UICONTROL Mid-sourcing > Deliveries]** 与帐户同名的节点(例如：acception_test)。

   ![](assets/mid_recette_account.png)

1. 在 **[!UICONTROL Mid-sourcing > Access Management > Operators]**，请创建新帐户。

   ![](assets/mid_recette_user_create.png)

1. 在 **[!UICONTROL Access rights]** 选项卡，为此运算符授予 **中间源提交** 群组。 此访问权限位于 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. 选择 **[!UICONTROL Restrict to data in the sub-folders of]** 选项，然后选择投放文件夹，以将此运算符限制为中间源投放文件夹。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用以下命令重新启动Web模块： **nlserver重新启动web**.

必须更改serverConf.xml文件中的中间源服务器设置。 必须在现有行的“使用IP地址管理任务共用性”部分中添加以下行：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

“@name”属性必须遵循以下规则：

**&#39;marketing_account_operator_name&#39;。&#39;affinity_name&#39;.&#39;affinity_group&#39;**

“marketing_account_operator_name”与在中间源实例中声明的中间源帐户的内部名称相关。

“affinity_name”与给定给该亲和度的任意名称相关。 此名称必须唯一。 授权字符为 `[a-z]``[A-Z]``[0-9]`. 目的是声明一组公共IP地址。

“affinity_group”与在每个投放中使用的目标映射中声明的子亲和度相关联。 最后一部分，包括“。” 如果没有子亲和度，则忽略。 授权字符为 `[a-z]``[A-Z]``[0-9]`.

您必须停止并重新启动服务器才能考虑修改。

## 在中间源服务器上配置跟踪 {#configuring-tracking-on-a-mid-sourcing-server}

**配置中间源服务器**

1. 转到“运算符”并选择运算符 **[!UICONTROL mid]**.
1. 在 **[!UICONTROL Frontal servers]** 选项卡，输入跟踪服务器连接参数。

   要创建跟踪实例，请输入跟踪服务器的URL、跟踪服务器内部帐户密码、实例名称、其密码以及与其关联的DNS掩码。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 输入连接参数后，单击 **[!UICONTROL Confirm the configuration]**.
1. 如有必要，请指定存储投放中包含的图像的位置。 为此，请从下拉列表中选择一种发布模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果您选择 **[!UICONTROL Tracking server(s)]** 选项，则图像将复制在中间源服务器上。

**配置客户平台**

1. 转到外部中间源路由帐户。
1. 在 **[!UICONTROL Mid-Sourcing]** 选项卡，指定中间源服务器连接参数。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 通过单击 **[!UICONTROL Test the connection]**.
1. 声明中间源服务器上引用的跟踪实例：

   单击链接 **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   指定跟踪实例的名称，然后确认与跟踪服务器的连接。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果消息传递由多个中间源服务器管理，请选择选项 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 并指定不同的服务器。

![](assets/s_ncs_install_midsourcing_tracking04.png)
