---
solution: Campaign Classic
product: campaign
title: 部署实例
description: 了解有关活动部署向导的更多信息
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3058'
ht-degree: 1%

---


# 部署实例{#deploying-an-instance}

>[!NOTE]
>
>服务器端配置只能由Adobe执行，由Adobe托管。 要进一步了解不同的部署，请参阅[托管模型](../../installation/using/hosting-models.md)部分或[本页](../../installation/using/capability-matrix.md)。

## 部署向导{#deployment-wizard}

图形向导在Adobe Campaign客户端控制台中可用，它允许您定义要连接到的实例的参数。

要开始部署向导，请选择&#x200B;**工具>高级>部署向导**。

![](assets/s_ncs_install_deployment_wiz_01.png)

配置步骤如下：

1. [常规参数](#general-parameters)
1. [电子邮件渠道参数](#email-channel-parameters)
1. [管理退回电子邮件](#managing-bounced-emails)
1. [跟踪配置](#tracking-configuration)
1. [移动渠道参数](#mobile-channel-parameters)
1. [区域设置](#regional-settings)
1. [从Internet访问](#access-from-the-internet)
1. [管理公共资源](#managing-public-resources)
1. [清除数据](#purging-data)

## 常规参数{#general-parameters}

在部署向导的第一步中，您可以输入有关实例的一般信息。

![](assets/s_ncs_install_deployment_wiz_02.png)

### 一般信息{#general-information}

窗口的下半部分允许您选择要激活的选项。

* **[!UICONTROL Customer identifier used in billing]** :这可以是实例的名称和版本号。
* **[!UICONTROL Common name of the customer]** :输入一个带公司名称的字符串。此信息可用于退订链接。
* **[!UICONTROL Namespace]** :输入小写形式的短标识符。目的是在升级时区分您的特定配置和出厂配置。 默认命名空间为&#x200B;**cus** - for customer。

### 技术选项{#technical-options}

窗口的下半部分允许您选择要激活的选项。

可以使用以下选项：

* **[!UICONTROL Email channel]** :以激活电子邮件投放。请参阅[电子邮件渠道参数](#email-channel-parameters)。
* **[!UICONTROL Tracking]** :启用目标填充跟踪（打开和单击）。请参阅[跟踪配置](#tracking-configuration)。
* **[!UICONTROL Managing bounced emails]** :定义用于接收传入电子邮件的POP帐户。请参阅[管理退回电子邮件](#managing-bounced-emails)。
* **[!UICONTROL LDAP integration]** :通过LDAP目录配置用户身份验证。请参阅[通过LDAP](../../installation/using/connecting-through-ldap.md)连接。

## 电子邮件渠道参数{#email-channel-parameters}

通过以下步骤，您可以定义要在消息标题中显示的信息。

这些参数可能会以投放模板重载，并且对于每个投放（如果用户具有所需权限）可单独重载。

### 已传送电子邮件的参数{#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

指示以下参数：

* **[!UICONTROL Sender name]** :发件人的姓名、
* **[!UICONTROL Sender address]** :发件人地址，
* **[!UICONTROL Reply address text]** :该名称可自定义，当收件人单击其电子邮件客户 **[!UICONTROL Reply]** 端软件中的按钮时使用。
* **[!UICONTROL Reply address]** :收件人单击其电子邮件客户端软 **[!UICONTROL Reply]** 件中的按钮时要使用的电子邮件地址，
* **[!UICONTROL Error address]** :有错误的邮件的电子邮件地址。这是用于处理弹回邮件的技术地址，包括由Adobe Campaign服务器收到的由不存在的目标地址引起的电子邮件。

除此之外，您还可以指定发件人地址和错误地址的授权&#x200B;**掩码**。 如有必要，这些蒙版可以使用逗号分隔。 此配置是可选的。 输入字段后，Adobe Campaign会在投放时(在分析期间，如果地址不包含任何变量)检查地址是否有效。 此操作模式确保没有使用可能触发投放问题的地址。 投放地址必须在投放服务器上配置。

### 地址{#characters-authorized-in-addresses}中授权的字符

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

在Adobe Campaign库中，必须按如下方式创建所有电子邮件地址：`x@y.z`。 **x**、**y**&#x200B;和&#x200B;**z**&#x200B;字符不得为空，并且不得包括非授权字符。

您可以在此处在数据库的电子邮件字段中定义授权字符（“数据策略”）。 列表中未包含的字符将被禁止，因此，当通过接口、Web表单以及导入数据在数据库中输入信息时，将拒绝这些字符。

提供两个列表:**仅限欧洲**&#x200B;或&#x200B;**仅限美国**。 如有必要，可添加其他字符。

### 投放参数 {#delivery-parameters}

**高级参数……**&#x200B;链接允许您访问投放选项、链接到重试的参数和隔离。

![](assets/s_ncs_install_deployment_wiz_05.png)

通过此窗口，您可以为所有电子邮件活动定义投放和地址质量管理选项。

可以使用以下选项：

* **[!UICONTROL Delivery duration of messages]** :此时后，投放将停止（默认为5天）,
* **[!UICONTROL Online resources validity duration]** :收件人用户档案的信息被保存以生成镜像页面的时间，
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** :选择此选项后，将不阻止列表会联系收件人,
* **[!UICONTROL Automatically ignore doubles]** :选择此选项后，不会对投放地址进行重复。

### 重试参数{#retry-parameters}

有关恢复的信息在&#x200B;**恢复周期**&#x200B;和&#x200B;**恢复数**&#x200B;字段中提供：当收件人不可到达时(例如，如果项目的收件箱已满)，默认情况下，将尝试联系他们5次，每次尝试间隔1小时(在最大投放时间内)。 这些值可以更改以满足您的需求。

### 隔离参数{#quarantine-parameters}

隔离的配置选项如下：

* **[!UICONTROL Duration between two significant errors]** :默认情况下输入值(“1d”):1天)定义在出现故障时应用程序在增加错误计数器之前等待的时间，
* **[!UICONTROL Maximum number of errors before quarantine]** :到达此值后，将隔离电子邮件地址（默认为“5”）:地址将在第六个错误时被隔离)。这意味着后续投放中将自动排除改联系人。

## 管理退回电子邮件{#managing-bounced-emails}

弹回邮件对于确认投放错误非常重要。 一旦规则确定其原因，这些错误便会在NP@I中分类。

仅当在部署向导的第一阶段选择了&#x200B;**电子邮件渠道**&#x200B;和&#x200B;**弹回邮件**&#x200B;管理选项时，此步骤才可用。 请参阅[常规参数](#general-parameters)。

此阶段允许您定义用于管理弹回邮件的设置。

![](assets/s_ncs_install_deployment_wiz_06.png)

### 用于检索传入邮件的POP帐户{#pop-account-used-to-retrieve-incoming-mails}

指示要连接到用于检索传入电子邮件的帐户的参数。

* **[!UICONTROL Label]** :名称，其中包括下面给出的所有参数，
* **[!UICONTROL Server]** :用于检索弹回邮件（传入邮件）的服务器，
* **[!UICONTROL Security]** :如有必要， **[!UICONTROL SSL]** 请从下拉列表中选择，
* **[!UICONTROL Port]** :服务器端口（通常为110）,
* **[!UICONTROL Account]** :用于弹回邮件的帐户名称，
* **[!UICONTROL Password]** :与帐户关联的密码。

指定POP设置后，单击&#x200B;**测试**&#x200B;以确保它们正确。

### 未处理的退回邮件{#unprocessed-bounce-mails}

弹回由Adobe Campaign自动处理，并应用&#x200B;**管理>活动管理>非交付项管理>投放日志资格**&#x200B;节点中列出的规则。 有关详细信息，请参阅[弹回邮件管理](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)。

未处理的弹回不会显示在Adobe Campaign界面中。 除非使用以下字段将其传输到第三方邮箱，否则这些邮件会自动删除：

* **[!UICONTROL Forwarding address]** :填写此字段以将Adobe Campaign平台收集的所有错误消息（已处理或未处理）传输到第三方地址。
* **[!UICONTROL Address for errors]** :填写此字段以仅将inMail进程无法确认的错误消息传输到第三方地址。
* **[!UICONTROL SMTP server]** :服务器用于发送未处理的弹回电子邮件。

>[!IMPORTANT]
>
>要转发未处理的弹回电子邮件，Adobe建议仅填写&#x200B;**[!UICONTROL Address for errors]**&#x200B;字段。 但是，请确保定期检查所使用的地址，因为这可能会给邮件服务器带来沉重负载。 有关详细信息，请与客户经理联系。

## 跟踪配置{#tracking-configuration}

通过下一步，您可以配置实例的跟踪。 必须向跟踪服务器声明并注册实例。

仅当在部署向导的第一页中选择了&#x200B;**电子邮件渠道**&#x200B;和&#x200B;**跟踪**&#x200B;选项时，才提供此步骤。 请参阅[常规参数](#general-parameters)。

有关Web跟踪（跟踪模式、创建和插入标记……）的详细信息，请参阅[此文档](../../configuration/using/about-web-tracking.md)。

### 工作原理 {#operating-principle}

在实例上激活跟踪时，在发送过程中会更改投放中的URL以启用跟踪。

* 在部署向导的此页上输入的有关外部URL（无论是否安全）的信息用于构建新URL。 除了此信息之外，修改后的链接还包含：投放、收件人和URL的标识符。

   跟踪信息由跟踪服务器上的Adobe Campaign收集，以丰富收件人用户档案和链接到投放的数据（**[!UICONTROL Tracking]**&#x200B;选项卡）。

   有关内部URL的信息仅由Adobe Campaign应用程序服务器用来联系跟踪服务器。

   有关详细信息，请参阅[跟踪服务器](#tracking-server)。

* 配置URL后，您需要启用跟踪。 为此，必须在跟踪服务器上注册实例。

   有关详细信息，请参阅[保存跟踪](#saving-tracking)。

### 跟踪服务器{#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

要确保跟踪此实例的效率，必须显示以下信息：
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** 和／或 **[!UICONTROL Secure external URL]** :输入要在要发送的电子邮件中使用的重定向URL。
* **[!UICONTROL Internal URL(s)]** :仅由Adobe Campaign服务器用来联系跟踪服务器以收集日志和上传URL的URL。不必将其与实例关联。

   如果未指定URL，则默认情况下将使用跟踪URL。

借助中间源体系结构，您可以将跟踪管理外部化。 操作步骤：

1. 选择选项&#x200B;**[!UICONTROL Externalize tracking management]** :这允许您将中间源服务器用作跟踪服务器。
1. 填充&#x200B;**[!UICONTROL External account]**&#x200B;和&#x200B;**[!UICONTROL Instance name]**&#x200B;字段，以便能够连接到中间源服务器。

   有关详细信息，请参阅[中间源服务器](../../installation/using/mid-sourcing-server.md)。

1. 单击&#x200B;**[!UICONTROL Enable the tracking instance]**&#x200B;按钮以批准与服务器的连接。

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### 保存跟踪{#saving-tracking}

填充URL后，必须注册跟踪服务器。

单击跟踪服务器&#x200B;**上的链接**&#x200B;注册，然后选择一个可用选项。

![](assets/s_ncs_install_deployment_wiz_09.png)

实现跟踪有三种可能的体系结构：

1. **在现有实例中添加跟踪支持**

   如果实例已经为其他需求（MTA服务器等）创建，则此选项适用。 将用作跟踪服务器的服务器上。

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   在重定向服务器上输入&#x200B;**internal**&#x200B;帐户的口令，以配置跟踪实例。

   >[!NOTE]
   >
   >如果使用多个跟踪服务器，则它们必须使用相同的名称和密码。

   指定实例的名称和口令。

1. **创建专用于跟踪的新实例**

   当跟踪实例被保留用于跟踪并且没有任何其他应用程序模块时，此选项很有用。

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   在重定向服务器上输入&#x200B;**internal**&#x200B;帐户的口令，以配置跟踪实例。

   >[!NOTE]
   >
   >如果配置了多个跟踪服务器，则它们必须使用相同的口令。

   指定实例的名称、口令和任何关联的DNS掩码，如&#x200B;**[!UICONTROL Campaign*]**。

1. **验证已为您预配置的跟踪实例**

   当您没有&#x200B;**internal**&#x200B;帐户的口令时，会使用此选项；在这种情况下，跟踪帐户是在跟踪服务器上为您预配置的。 输入重定向服务器的跟踪帐户的口令以验证跟踪实例。

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   指定要验证的实例的名称。

单击&#x200B;**批准**&#x200B;以将录制过程与跟踪服务器开始。

返回到上一窗口，将显示一条消息，确认在跟踪服务器级别的注册：

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

对于标准安装，不得修改链接到URL搜索&#x200B;**的参数**。 有关所有其他参数，请与Adobe联系。

## 移动渠道参数{#mobile-channel-parameters}

下一步允许您为手机投放（SMS和WAP Push）定义默认设置。

>[!NOTE]
>
>移动渠道是可选的：此阶段仅在已购买时显示。 请核实您的许可协议。

![](assets/s_ncs_install_deployment_wiz_12.png)

### SMS投放{#default-account-for-sms-delivery}的默认帐户

输入以下信息：

* **[!UICONTROL Label]** :输入此SMS/Wap推送帐户的名称。例如，您可能希望使用路由器的名称。
* 对于&#x200B;**[!UICONTROL Server]**、**[!UICONTROL Port]**、**[!UICONTROL Account]**、**[!UICONTROL Password]**、**[!UICONTROL Connector]**、**[!UICONTROL Send Endpoint]**、**[!UICONTROL Reception Endpoint]**、**[!UICONTROL Notification Endpoint]**&#x200B;字段：有关所需的设置，请与服务提供商联系。

### 发送的SMS参数{#parameters-of-sms-sent}

在&#x200B;**优先级**&#x200B;下拉列表中：选择“正常”、“高”或“紧急”，将其应用于要发送的邮件。

### 高级参数 {#advanced-parameters}

**高级参数……**&#x200B;链接允许您访问重试选项和隔离选项。

![](assets/s_ncs_install_deployment_wiz_13.png)

有关重试的信息，请参见&#x200B;**重试周期**&#x200B;和&#x200B;**重试数**&#x200B;字段：当移动设备不可到达时，默认情况下，项目将重试5次，间隔至少为15分钟(对于最大投放期)。 这些值可以调整以满足您的需求。

隔离的配置选项如下：

* **[!UICONTROL Time between two significant errors]** :输入默认值(默认为“1d”:（天）定义应用程序在增加错误计数器以等待失败之前等待的时间。
* **[!UICONTROL Maximum number of errors before quarantine]** :到达此值后，将隔离手机号码（默认为“5”）:该号码将在第6个错误时被隔离)。这意味着联系人将自动从将来的投放中排除。

## 区域设置{#regional-settings}

此阶段允许您包含数据策略首选项。

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** :选择此选项后，应用程序会将国际格式应用于电话号码（国家／地区前缀是必填的，因为在应用格式之前不会检查数字数）。如果未选择此选项，您必须在国际电话号码前加上“+”或“00”前缀。
* **[!UICONTROL Store all phone numbers using the international format]** :此选项仅涉及 **** 导入或编辑的国内电话号码。定义您是要使用国内格式（如425 555 0150）还是国际格式(如+1 425 555 0150)

## 从Internet访问{#access-from-the-internet}

>[!IMPORTANT]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

通过此步骤，可以为Internet上公开的Adobe Campaign页面定义访问URL。

您还必须在此处指明链接到Web 窗体的发布选项。

![](assets/s_ncs_install_deployment_wiz_15.png)

### Web上公开的服务器{#servers-exposed-on-the-web}

使用此页可以填充服务器URL以：

1. 访问Internet上公开的应用程序服务器：订阅/退订表单、外部网等。
1. 访问应用程序服务器以获取Web上未公开的资源：表单、内部网、确认页。
1. 访问镜像页面投放。

   镜像页面是显示电子邮件内容的动态页面。 它通过插入到发送给收件人的消息中的链接来访问，并且可以包含个性化元素。 该镜像页面使收件人能够在因特网浏览器中而不是电子邮件软件中阅读消息，而不管投放格式（文本或HTML）如何。 但是，只有在定义了所需的HTML内容后，才会为给定投放生成镜像页面。

Adobe Campaign允许您区分这三个URL，将负载分散到多个平台。

## 管理公共资源{#managing-public-resources}

>[!IMPORTANT]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

要从外部查看，链接到活动的电子邮件和公共资源中使用的图像必须存在于可从外部访问的服务器上。 然后，外部收件人或操作员可使用它们。

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

对于此步骤，您需要输入：

1. 新的公共资源URL。 有关详细信息，请参阅[公共资源URL](#public-resources-url)部分。
1. 投放中的图像检测模式。 有关详细信息，请参阅[投放图像检测](#delivery-image-detection)部分。
1. 发布选项。 有关详细信息，请参阅[发布模式](#publication-modes)部分。

公共资源可通过Adobe Campaign树的&#x200B;**“管理”>“资源”>“联机”>“公共资源”**&#x200B;节点访问。 它们收集在图书馆中，并可以包含在电子邮件中，但也可以用于活动或任务，以及内容管理。

![](assets/install_pub_resources_view.png)

### 公共资源URL {#public-resources-url}

第一个字段允许您指定上传后用于资源的URL的开始。 上传后，可通过此新URL访问资源。

在投放中，可以使用存储在公共资源库中的图像或存储在服务器上的任何其他本地图像或图像。

* 对于电子邮件图像，**https://** server **/res/img** URL。

   可以覆盖每个投放的此值。

* 对于公共资源,URL **https://** server **/res/** instance ****，其中&#x200B;**instance**是跟踪实例的名称。

### 投放图像检测{#delivery-image-detection}

在投放中，可以使用存储在公共资源库中的图像或存储在服务器上的任何其他本地图像或图像。

通过字段&#x200B;**URL掩码**，可以指定自动上传图像时要跳过的URL掩码的列表。 例如，如果您使用存储在可从外部访问的站点（特别是Internet站点）上的图像，则可以在此字段中输入站点URL。

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

可以使用逗号分隔多个URL蒙版。

* 有关在电子邮件中使用和管理图像的信息，请参阅[本节](../../delivery/using/defining-the-email-content.md#adding-images)。
* 在投放向导中，从这些URL调用的图像将显示“已忽略”状态。

### 发布模式{#publication-modes}

在向导的下半部分，您可以选择公共资源和图像的发布选项。 Web 窗体和调查也可以使用这些选项。

提供以下发布模式：

* 跟踪服务器

   资源将自动复制到不同的跟踪服务器。 它们是在步骤[跟踪配置](#tracking-configuration)中配置的。

* 其他Adobe Campaign服务器

   您可以使用另一个Adobe Campaign服务器复制资源。

   服务器端，要使用专用Adobe Campaign服务器，必须使用以下命令创建新实例：

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   然后输入密码。

   专用服务器的参数在&#x200B;**[!UICONTROL Media URL(s)]**、**[!UICONTROL Password]**&#x200B;和&#x200B;**[!UICONTROL Instance name]**&#x200B;字段中指定。

   ![](assets/s_ncs_install_images_upload_b.png)

* 手动发布脚本(仅限公共资源)

   ![](assets/s_ncs_install_images_upload_c.png)

   您可以使用脚本发布图像：

   * 必须创建此脚本：其内容取决于您的配置。
   * 脚本将由以下命令调用：

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      其中`[INSTALL]`是Adobe Campaign安装文件夹的访问路径。

   * 在Unix中，确保脚本是可执行的。

对于图像，它必须将它们从通过&#x200B;**NmsDelivery_ImageSubDirectory**&#x200B;选项指定的“images”文件夹复制到一个或多个前端服务器。 这些服务器将存储图像，以便通过新配置的URL访问它们。

在没有手动发布脚本的Adobe Campaign服务器上发布的事件中，默认情况下，投放的图像存储在`$(XTK_INSTALL_DIR)/var/res/img/ directory`中。 相应的URL如下：**`https://server/res/img`**。

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`.相应的URL如下：**`https://server/res/instance`**&#x200B;其中instance是跟踪实例的名称。

>[!NOTE]
>
>可以更改公共资源存储目录。 有关详细信息，请参阅[管理公共资源](#managing-public-resources)。

### 同步公共资源{#synchronizing-public-resources}

此功能允许您&#x200B;**同步多台备用服务器上的公共资源**。

如果跟踪服务器上不存在公共资源，或者如果资源返回404错误，则跟踪服务器将尝试在其中一个备用服务器上查找该资源。

必须在营销服务器的&#x200B;**serverConf.xml**&#x200B;文件中声明和配置备用服务器。 **serverConf.xml**&#x200B;中的所有可用参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

**声明**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**配置**

对于每个必须同步的公共资源，您必须向`<relay>`部分的`<url>`元素添加状态属性：

状态属性可以是以下三个值之一：

* 备用：公共资源已同步

* 正常：现有行为（无同步）

* 黑名单：如果返回404错误，阻止列表则该URL将添加到。 中URL的持续时间（以秒为单位）阻止列表由默认值为60s的&#x200B;**timeout**&#x200B;属性定义。

现成的同步配置是：

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## 清除数据{#purging-data}

在部署向导的最后一个阶段，您可以配置自动清除过时数据。 这些值以天数表示。

![](assets/s_ncs_install_deployment_wiz_16.png)

数据会通过数据库清理工作流自动删除。 有关如何配置和操作此工作流以及已删除项的详细信息，请参阅此[文档](../../production/using/database-cleanup-workflow.md)。
