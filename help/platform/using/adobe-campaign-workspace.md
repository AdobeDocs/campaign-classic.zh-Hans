---
product: campaign
title: Adobe Campaign 工作区
description: 了解如何使用和自定义Campaign工作区
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 67%

---

# Adobe Campaign 工作区{#adobe-campaign-workspace}



## 探索Adobe Campaign界面 {#about-adobe-campaign-interface}

连接到数据库后，即可访问 Adobe Campaign 主页，这是一个仪表板：其中包含允许您访问各种功能的链接和快捷方式，具体显示哪些取决于您的安装以及常规平台配置。

在主页的中央部分，可以使用链接访问 Campaign 在线文档门户网站、论坛及支持网站。

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ 在视频中发现 Campaign 工作区](#video)

>[!NOTE]
>
>在您的实例上有哪些 Adobe Campaign 功能可用取决于已安装的模块和附加组件。根据您的权限及具体配置，部分功能可能无法使用。
>
>在安装任何模块或加载项之前，您需要查看许可协议或与Adobe客户经理联系。

### 控制台和 Web 访问 {#console-and-web-access}

可通过控制台或互联网浏览器访问 Adobe Campaign 平台。请参阅中的兼容浏览器 [兼容性矩阵](../../rn/using/compatibility-matrix.md#Browsers).

Web访问界面类似于控制台界面。 在浏览器中，您可以使用与控制台中相同的导航和显示功能，但您只能在营销策划上执行一组缩减的操作。 例如，您可以查看和取消营销活动，但无法修改营销活动。 对于给定的运算符，营销活动将在控制台中显示以下选项：

![在营销策划的仪表板中，操作员可以查看和取消营销策划，还可以修改营销策划，并向其中添加投放、文档和任务。](assets/operation_from_console.png)

而使用Web访问时，选项将主要支持查看：

![在浏览器中，同一操作员只能查看和取消营销活动。](assets/operation_from_web.png)

详细了解 [使用Web界面](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### 语言 {#languages}

安装Adobe Campaign Classic实例时选择语言。

![](assets/language.png)

您可以在五种不同的语言之间进行选择：

* 英语（英国）
* 英语（美国）
* 法语
* 德语
* 日语

您为Adobe Campaign Classic实例选择的语言可能会影响日期和时间格式。 有关更多信息，请参阅此](../../platform/using/adobe-campaign-workspace.md#date-and-time)章节[。

有关如何创建实例的详细信息，请参阅此 [页面](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>创建实例后，无法更改语言。

## 导览基本功能 {#navigation-basics}

### 浏览页面 {#browsing-pages}

该平台的各种功能可分为几大核心功能：可使用界面上方的链接来访问这些功能。

![](assets/overview_home.png)

可以访问的核心功能列表将取决于您所安装的软件包和附加组件以及访问权。

每项功能都包含一套基于工作任务相关需求及使用情境的功能。例如，**[!UICONTROL Profiles and targets]** 链接可用于访问收件人列表、订阅服务、现有的定位工作流，以及创建这些元素的快捷方式。

这些列表可通过 **[!UICONTROL Lists]** 左侧部分中的链接 **[!UICONTROL Profiles and Targets]** 界面。

![](assets/recipient_list_overview.png)

### 使用选项卡 {#using-tabs}

* 单击某个核心功能或链接时，相关页面会取代当前的页面。要回到上一页，可单击工具栏上的 **[!UICONTROL Back]** 按钮。要返回主页，可单击 **[!UICONTROL Home]** 按钮。

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 如果是某个显示屏幕（例如 Web 应用程序、计划、投放、报告等）的菜单和快捷方式，则会将匹配的页面显示在另一个选项卡中。这样您可以使用选项卡从一个页面浏览至另一页面。

   ![](assets/d_ncs_user_interface_tabs.png)

### 创建元素 {#creating-an-element}

通过每个核心功能部分可以浏览各种可用的元素。要执行此操作，可使用 **[!UICONTROL Browsing]** 部分中的快捷方式。**[!UICONTROL Other choices]** 链接可用于访问其他所有页面，无论工作环境如何。

您可以创建新元素（投放、Web应用程序、工作流等） 使用 **[!UICONTROL Create]** 部分。 使用列表上方的 **[!UICONTROL Create]** 按钮向列表中添加新元素。

例如，在投放页面上，使用 **[!UICONTROL Create]** 按钮创建新的投放。

![](assets/d_ncs_user_interface_tab_add_del.png)


## 格式和单位 {#formats-and-units}

### 日期和时间 {#date-and-time}

Adobe Campaign Classic 实例的语言将会影响日期和时间格式。

无法在安装后更改您在安装 Campaign 时所选择的语言。您可以选择：美式英语、英式英语、法语、德语或日语。有关详细信息，请参见[此页面](../../installation/using/creating-an-instance-and-logging-on.md)。

美式英语和英式英语的主要差别如下：

<table> 
 <thead> 
  <tr> 
   <th> 格式<br /> </th> 
   <th> 英语（美国）<br /> </th> 
   <th> 英式英语<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 一周从星期日开始<br /> </td> 
   <td> 一周从星期一开始<br /> </td> 
  </tr> 
  <tr> 
   <td> 短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>示例：09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>示例：25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> 带时间的短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>例如：2018年9月25日10:47:下午25</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>例如：2018年9月25日22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 在枚举中添加值 {#add-values-in-an-enumeration}

使用带有下拉式列表的输入字段，您可以输入枚举值，该值将存储起来并且作为下拉式列表中的选项提供。例如，在收件人用户档案的 **[!UICONTROL City]** 选项卡的 **[!UICONTROL General]** 字段中，您可以输入 London。按下 Enter 键确认该值时，一条消息会询问您是否要为与该字段相关联的枚举保存此值。

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

如果单击 **[!UICONTROL Yes]**，就可以在相关字段的组合框中提供该值（在本例中为 **[!UICONTROL London]**）。

>[!NOTE]
>
>管理员通过 **[!UICONTROL Administration > Platform > Enumerations]** 部分管理枚举（也称为“分项列表”）。有关更多信息，请参阅 [管理明细列表](../../platform/using/managing-enumerations.md).

### 默认单位 {#default-units}

在表示一段时间的字段中（例如，某次投放的资源的有效期、已批准的任务期限等），可采用以下&#x200B;**单位**&#x200B;表示该值：

* **[!UICONTROL s]** 几秒钟，
* **[!UICONTROL mn]** 几分钟，
* **[!UICONTROL h]** 数小时，
* **[!UICONTROL d]** 好几天了。

![](assets/enter_unit_sample.png)

## 教程视频 {#video}

本视频介绍Campaign Classic工作区。

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
