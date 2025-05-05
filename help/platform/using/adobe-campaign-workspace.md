---
product: campaign
title: Adobe Campaign 工作区
description: 了解如何使用及自定义Campaign工作区
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 31%

---

# Adobe Campaign 工作区{#adobe-campaign-workspace}



## 探索Adobe Campaign界面 {#about-adobe-campaign-interface}

连接到数据库后，即可访问 Adobe Campaign 主页，这是一个仪表板：其中包含允许您访问各种功能的链接和快捷方式，具体显示哪些取决于您的安装以及常规平台配置。

在主页的中央部分，可以使用链接访问 Campaign 在线文档门户网站、论坛及支持网站。

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)在[视频](#video)中发现Campaign工作区

>[!NOTE]
>
>实例上可用的Adobe Campaign功能取决于安装的模块和加载项。 根据您的权限及具体配置，部分功能可能无法使用。
>
>在安装任何模块或插件之前，您需要查看许可协议或与Adobe客户经理联系。

### 控制台和 Web 访问 {#console-and-web-access}

可通过控制台或互联网浏览器访问Adobe Campaign平台。 请参阅[兼容性矩阵](../../rn/using/compatibility-matrix.md#Browsers)中的兼容浏览器。

Web访问界面与控制台界面类似。 在浏览器中，您可以使用与控制台中相同的导航和显示功能，但您只能对营销策划执行一组缩减的操作。 例如，您可以查看和取消营销活动，但无法修改营销活动。 对于给定的运算符，营销活动将在控制台中显示以下选项：

![在营销活动的仪表板中，操作员可以查看和取消营销活动，还可以对其进行修改，并向其添加投放、文档和任务。](assets/operation_from_console.png)

而使用Web访问时，选项将主要支持查看：

![在浏览器中，同一操作员只能查看和取消营销活动。](assets/operation_from_web.png)

了解有关[使用Web界面](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-)的详细信息。

### 语言 {#languages}

在安装Adobe Campaign Classic实例时，将选择语言。

![](assets/language.png)

您可以在五种不同的语言之间进行选择：

* 英语（英国）
* 英语（美国）
* 法语
* 德语
* 日语

您为Adobe Campaign Classic实例选择的语言可能会影响日期和时间格式。 有关更多信息，请参阅此[&#128279;](../../platform/using/adobe-campaign-workspace.md#date-and-time)章节。

有关如何创建实例的详细信息，请参阅此[页面](../../installation/using/creating-an-instance-and-logging-on.md)。

>[!CAUTION]
>
>创建实例后，无法更改语言。

## 导览基本功能 {#navigation-basics}

### 浏览页面 {#browsing-pages}

该平台的各种功能可分为几大核心功能：可使用界面上方的链接来访问这些功能。

![](assets/overview_home.png)

可以访问的核心功能列表将取决于您所安装的软件包和附加组件以及访问权。

每个功能包括一组基于任务相关需求和使用上下文的功能。 例如，通过&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;链接，您可以访问收件人列表、订阅服务、现有的定位工作流以及创建这些元素的快捷方式。

这些列表可通过&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;界面左侧部分的&#x200B;**[!UICONTROL Lists]**&#x200B;链接获得。

![](assets/recipient_list_overview.png)

### 使用选项卡 {#using-tabs}

* 单击核心功能或链接时，相关页面将替换当前页面。 要返回上一页，请单击工具栏上的&#x200B;**[!UICONTROL Back]**&#x200B;按钮。 要返回主页，请单击&#x200B;**[!UICONTROL Home]**&#x200B;按钮。

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 在菜单或显示屏幕快捷方式（如Web应用程序、程序、投放、报告等）的情况下，匹配页面会显示在另一个选项卡中。 这样您可以使用选项卡从一个页面浏览至另一页面。

  ![](assets/d_ncs_user_interface_tabs.png)

### 创建元素 {#creating-an-element}

通过每个核心功能部分，可在可用元素之间浏览。 为此，请使用&#x200B;**[!UICONTROL Browsing]**&#x200B;部分中的快捷方式。 **[!UICONTROL Other choices]**&#x200B;链接允许您访问所有其他页面，无论环境如何。

您可以使用屏幕左侧&#x200B;**[!UICONTROL Create]**&#x200B;部分中的快捷方式创建新元素（投放、Web应用程序、工作流等）。 使用列表上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮向列表添加新元素。

例如，在投放页面上，使用&#x200B;**[!UICONTROL Create]**&#x200B;按钮创建新投放。

![](assets/d_ncs_user_interface_tab_add_del.png)


## 格式和单位 {#formats-and-units}

### 日期和时间 {#date-and-time}

Adobe Campaign Classic 实例的语言将会影响日期和时间格式。

安装Campaign时会选择语言，此后无法更改。 您可以选择：英语（美国）、英语（英语）、法语、德语或日语。 有关详细信息，请参见[此页面](../../installation/using/creating-an-instance-and-logging-on.md)。

美式英语和英式英语的主要差别如下：

<table> 
 <thead> 
  <tr> 
   <th> 格式<br /> </th> 
   <th> 英语（美国）<br /> </th> 
   <th> 英语(EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 星期从星期日开始<br /> </td> 
   <td> 星期从星期一<br />开始 </td> 
  </tr> 
  <tr> 
   <td> 简短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>示例：09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>示例：25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> 具有时间的简短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>例如：2018年9月25日10:47:25下午</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>例如： 2018年9月25日22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 在枚举中添加值 {#add-values-in-an-enumeration}

通过使用下拉列表的输入字段，您可以输入枚举值，该值可以存储下来，然后作为下拉列表中的选项提供。 例如，在收件人用户档案的&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL City]**&#x200B;字段中，您可以输入London。 当您按Enter键确认此值时，会出现一条消息，询问您是否要为与该字段关联的枚举保存此值。

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

如果单击&#x200B;**[!UICONTROL Yes]**，此值将在相关字段的组合框中可用（在本例中为： **[!UICONTROL London]**）。

>[!NOTE]
>
>枚举（也称为“明细列表”）由管理员通过&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;部分管理。 有关详细信息，请参阅[管理枚举](../../platform/using/managing-enumerations.md)。

### 默认单位 {#default-units}

在表示一段时间的字段中（例如，某次投放的资源的有效期、已批准的任务期限等），可采用以下&#x200B;**单位**&#x200B;表示该值：

* **[!UICONTROL s]**&#x200B;表示秒，
* **[!UICONTROL mn]**&#x200B;分钟，
* **[!UICONTROL h]**&#x200B;表示小时，
* **[!UICONTROL d]**&#x200B;天。

![](assets/enter_unit_sample.png)

## 教程视频 {#video}

本视频介绍Campaign Classic工作区。

>[!VIDEO](https://video.tv.adobe.com/v/39534?quality=12&captions=chi_hans)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他 Campaign Classic 操作方法视频。
