---
product: campaign
title: 创建实例并登录
description: 创建实例并登录
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 9%

---

# 创建实例并登录{#creating-an-instance-and-logging-on}



要创建新实例和Adobe Campaign数据库，请应用以下流程：

1. 创建连接。
1. 登录以创建相关实例。
1. 创建和配置数据库。

>[!NOTE]
>
>只有&#x200B;**内部**&#x200B;标识符才能执行这些操作。 如需详细信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#internal-identifier)。

启动Adobe Campaign控制台后，您将访问登录页面。

要创建新实例，请执行以下步骤：

1. 单击凭据字段右上角的链接可访问连接配置窗口。 此链接可以是&#x200B;**[!UICONTROL New...]**&#x200B;或现有的实例名称。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击 **[!UICONTROL Add > Connection]** 并输入 Adobe Campaign 应用程序服务器的标签和 URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过 URL 指定与 Adobe Campaign 应用程序服务器的连接。使用计算机的 DNS 或别名，或您的 IP 地址。

   例如，您可以使用 `https://<machine>.<domain>.com` 类型 URL。

   >[!CAUTION]
   >
   >对于连接URL，仅使用以下字符： `[a-z]`、`[A-Z]`、`[0-9]`和破折号(-)或句点。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;以确认设置：您现在可以从实例创建过程开始。
1. 在&#x200B;**[!UICONTROL Connection settings]**&#x200B;窗口中，输入&#x200B;**内部**&#x200B;登录名及其密码以连接到Adobe Campaign应用程序服务器。 连接后，可以访问实例创建助手来声明新实例
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;字段中，输入&#x200B;**实例名称**。 由于此名称用于生成配置文件&#x200B;**config-`<instance>`.xml**&#x200B;并在命令行参数中用于标识实例，因此请确保选择不带特殊字符的短名称。 例如：**eMarketing**。

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的实例名称不能超过40个字符。 这样，您就可以限制“Message-ID”标头的大小，并防止将邮件视为垃圾邮件，尤其是SpamAssassin等工具。

1. 在&#x200B;**[!UICONTROL DNS masks]**&#x200B;字段中，输入应附加实例的&#x200B;**DNS掩码列表**。 Adobe Campaign服务器使用HTTP请求中显示的主机名来确定要访问的实例。

   主机名包含在字符串&#x200B;**https://**&#x200B;和服务器地址的第一个斜杠字符&#x200B;**/**&#x200B;之间。

   您可以定义以逗号分隔的值列表。

   是？ 和&#42;个字符可用作通配符，以替换一个或多个字符（DNS、端口等）。 例如，**demo&#42;**&#x200B;值将与“https://demo”配合使用，就像与“https://demo:8080”甚至“https://demo2”配合使用一样。

   使用的名称必须在DNS中定义。 您还可以通知Windows中&#x200B;**c：/windows/system32/drivers/etc/hosts**&#x200B;文件和Linux中&#x200B;**/etc/hosts**&#x200B;文件中的DNS名称和IP地址之间的通信。 因此，您必须修改连接设置以使用此DNS名称，才能连接到您选择的实例。

   服务器必须由此名称标识，尤其是在电子邮件中上传图像时。

   此外，服务器必须能够使用此名称以及环回地址（如果可能）与其自身连接，尤其是允许以PDF格式导出报告。127.0.0.1

1. 在&#x200B;**[!UICONTROL Language]**&#x200B;下拉列表中，选择&#x200B;**实例语言**：英语（美国）、英语（英国）、法语或日语。

   美式英语和英国英语之间的差异在[Campaign v8 （控制台）文档] (.https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui)中进行了说明。

   >[!CAUTION]
   >
   >在此步骤之后无法修改实例语言。 Adobe Campaign实例不是多语言的：您无法将界面从一种语言切换到另一种语言。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;确认实例声明。 注销并重新登录以声明数据库。

   >[!NOTE]
   >
   >可以从命令行创建实例。 有关详细信息，请参阅[命令行](../../installation/using/command-lines.md)。
