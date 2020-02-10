---
title: “使用案例：创建概述”
seo-title: “使用案例：创建概述”
description: “使用案例：创建概述”
seo-description: null
page-status-flag: never-activated
uuid: 404ae82b-2766-4802-8673-aaaa26868f46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: a3834828-4d39-4699-b648-d399797b8ea7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 用例：创建概述{#use-cases-creating-overviews}

在以下示例中，我们将创建概述类型的Web应用程序，以显示数据库中的所有Web应用程序。 配置以下元素：

* 文件夹上的过滤器(请参阅 [在文件夹上添加过滤器](#adding-a-filter-on-a-folder)),
* 用于创建新Web应用程序的按钮(请参阅 [添加按钮以配置新Web应用程序](#adding-a-button-to-configure-a-new-web-application)),
* 列表中每个条目的详细信息显示(请参 [阅将详细信息添加到列表](#adding-detail-to-a-list)),
* 每个链接编辑工具一个过滤器(请参 [阅使用链接编辑器创建过滤器](#creating-a-filter-using-a-link-editor)),
* 刷新链接(请参阅 [创建刷新链接](#creating-a-refresh-link))。

![](assets/s_ncs_configuration_webapp_overview.png)

## 创建单页Web应用程序 {#creating-a-single-page-web-application}

1. 创建单个 **[!UICONTROL Page]** Web应用程序并禁用向下一页的出站过渡和过渡。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 更改页面标题。

   此标题将显示在概述标题和Web应用程序概述中。

1. 在Web应用程序属性中，通过选择模板来修改应用程序的呈 **[!UICONTROL Single-page Web application]** 现。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 打开Web **[!UICONTROL Page]** 应用程序的活动并打开列表(**[!UICONTROL Static element > List]**)。
1. 在列 **[!UICONTROL Data]** 表的选项卡中，选择文档的类 **[!UICONTROL Web applications]** 型以及 **[!UICONTROL Label]** 、 **[!UICONTROL Creation date]** 和 **[!UICONTROL Type of application]** 输出列。
1. 在子选 **[!UICONTROL Filter]** 项卡中，如下所示创建以下筛选器，以便仅显示Web应用程序并从视图中排除模板。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 关闭页面的配置窗口，然后单击 **[!UICONTROL Preview]**。

   将显示数据库中可用的Web应用程序列表。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在文件夹中添加过滤器 {#adding-a-filter-on-a-folder}

在概述中，您可以根据数据在Adobe Campaign树中的位置选择访问数据。 这是文件夹上的过滤器。 应用以下过程，将其添加到概述中。

1. 将光标放在Web应 **[!UICONTROL Page]** 用程序的节点上，并添加一 **[!UICONTROL Select folder]** 个元素(**[!UICONTROL Advanced controls > Select folder]**)。
1. 在出现 **[!UICONTROL Storage]** 的窗口中，单击该链 **[!UICONTROL Edit variables]** 接。
1. 更改变量标签以满足您的需求。
1. 使用文件夹值更改变 **量名** 。

   >[!NOTE]
   >
   >变量的名称必须与链接到该文件夹（在架构中定义）的元素的名称匹配，即，在本 **例中** ，文件夹。 引用表时，必须重新使用此名称。

1. 将类 **[!UICONTROL XML]** 型应用于变量。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 选择交 **[!UICONTROL Refresh page]** 互。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 将光标放在列表上，在选项卡 **[!UICONTROL Advanced]** 中，引用之前在列表选项卡中创 **[!UICONTROL Folder filter XPath]** 建的变量。 必须使用文件夹链接所关注元素的名称，即文件夹 **名称**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >在此阶段，Web应用程序不在其应用程序上下文中，因此无法在文件夹上测试过滤器。

## 添加按钮以配置新的Web应用程序 {#adding-a-button-to-configure-a-new-web-application}

1. 将光标放在元 **[!UICONTROL Page]** 素上并添加链接(**[!UICONTROL Static elements > Link]**)。
1. 修改链接标签，因为链接标签将显示在概述的按钮上。

   在我们的示例中，标签为 **New**。

1. 在URL字段中插入以下URL: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms:webApp与Web应用程序架构** “一致”。
   >
   >**nms:newWebApp与新的Web应用程序创建向导一致。**

1. 选择在同一窗口中显示URL。
1. 在图像字段中添加Web应用程序图标： **/nms/img/webApp.png**。

   此图标将显示在按钮 **[!UICONTROL New]** 上。

1. 在字 **段中** ，输入 **[!UICONTROL Style]** 按钮。

   此样式在以前选择的模 **[!UICONTROL Single-page Web application]** 板中引用。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 向列表添加详细信息 {#adding-detail-to-a-list}

在概述中配置列表时，您可以选择显示列表中每个条目的其他详细信息。

1. 将光标放在先前创建的列表元素上。
1. 在选 **[!UICONTROL General]** 项卡中，从下拉 **[!UICONTROL Columns and additional detail]** 列表中选择显示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在选 **[!UICONTROL Data]** 项卡中，添加、和 **[!UICONTROL Primary key]** 列， **[!UICONTROL Internal name]** 然后为每 **[!UICONTROL Description]****[!UICONTROL Hidden field]** 个选项选择选项。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   这样，此信息将仅显示在每个条目的详细信息中。

1. 在选项卡 **[!UICONTROL Additional detail]** 中，添加以下代码：

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>在服务器上刷新JavaScript库需要五分钟。 您可以重新启动服务器以避免等待此延迟。

## 筛选和更新列表 {#filtering-and-updating-the-list}

在本节中，您将创建一个过滤器，用于显示由特定操作符创建的Web应用程序的概述。 此过滤器是使用链接编辑器创建的。 选择操作符后，请刷新列表以应用过滤器；这需要创建刷新链接。

这两个元素将分组在同一容器中，以便在概述中以图形方式分组。

1. 将光标放在元素 **[!UICONTROL Page]** 上并选择 **[!UICONTROL Container > Standard]**。
1. 将列数设置为 **2**，以便链接编辑器和链接彼此相邻。

   ![](assets/s_ncs_configuration_webapp_container.png)

   有关元素布局的信息，请参阅 [此部分](../../web/using/about-web-forms.md)。

1. 应用 **dottedFilter**。

   此样式在之前选择的 **[!UICONTROL Single-page Web applicatio]** n个模板中引用。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用链接编辑器创建过滤器 {#creating-a-filter-using-a-link-editor}

1. 将光标放在在上一阶段创建的容器上，并通过菜单插入链接编 **[!UICONTROL Advanced controls]** 辑器。
1. 在自动打开的存储窗口中，选择选 **[!UICONTROL Variables]** 项，然后单击链 **[!UICONTROL Edit variables]** 接并创建用于筛选数据的XML变量。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改标签。

   它将显示在概述中 **[!UICONTROL Filter]** 的字段旁边。

1. 选择“运算符”表作为应用程序架构。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 将光标放在列表元素上，并通过选项卡创建过 **[!UICONTROL Data > Filter]** 滤器：

   * **** 表达式：“创建者”链接的外键
   * **** 运营商：等于
   * **** 值：变量（变量）
   * **** 在以下情况下，请考虑：&#39;$(var2/@id)&#39;!=&quot;
   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web应用程序用户必须是具有相应Adobe Campaign权限的已识别运营商才能访问信息。 此类配置对匿名Web应用程序无效。

### 创建刷新链接 {#creating-a-refresh-link}

1. 将光标放在容器上，并通过菜 **[!UICONTROL Link]** 单插入 **[!UICONTROL Static elements]** 光标。
1. 修改标签。
1. Select **[!UICONTROL Refresh data in a list]**.
1. 添加以前创建的列表。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在字段上添加刷新 **[!UICONTROL Image]** 图标：**/xtk/img/refresh.png **。
1. 使用排序箭头重新组织Web应用程序的各个元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

现在已配置Web应用程序。 您可以单击选 **[!UICONTROL Preview]** 项卡进行预览。

![](assets/s_ncs_configuration_webapp_result.png)

