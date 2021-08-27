---
product: campaign
title: '"用例：创建概述"'
description: '"用例：创建概述"'
audience: web
content-type: reference
topic-tags: web-applications
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# 用例：创建概述页面{#use-cases-creating-overviews}

![](../../assets/common.svg)

在以下示例中，我们将创建概述类型的Web应用程序，以显示数据库中的所有Web应用程序。 配置以下元素：

* 文件夹上的过滤器（请参阅[在文件夹上添加过滤器](#adding-a-filter-on-a-folder)），
* 用于创建新Web应用程序的按钮（请参阅[添加按钮以配置新Web应用程序](#adding-a-button-to-configure-a-new-web-application)），
* 列表中每个条目的详细显示（请参阅[向列表添加详细信息](#adding-detail-to-a-list)），
* 每个链接编辑工具一个过滤器（请参阅[使用链接编辑器创建过滤器](#creating-a-filter-using-a-link-editor)），
* 刷新链接（请参阅[创建刷新链接](#creating-a-refresh-link)）。

![](assets/s_ncs_configuration_webapp_overview.png)

## 创建单页Web应用程序 {#creating-a-single-page-web-application}

1. 创建一个&#x200B;**[!UICONTROL Page]** Web应用程序，并禁用叫客过渡和过渡到下一页。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 更改页面标题。

   此标题将显示在概述标题和Web应用程序概述中。

1. 在Web应用程序属性中，通过选择&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;模板来修改应用程序的呈现。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 打开Web应用程序的&#x200B;**[!UICONTROL Page]**&#x200B;活动并打开列表(**[!UICONTROL Static element > List]**)。
1. 在列表的&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Web applications]**&#x200B;文档的类型以及&#x200B;**[!UICONTROL Label]** 、 **[!UICONTROL Creation date]**&#x200B;和&#x200B;**[!UICONTROL Type of application]**&#x200B;输出列。
1. 在&#x200B;**[!UICONTROL Filter]**&#x200B;子选项卡中，创建如下所示的以下过滤器，以便仅显示Web应用程序并从视图中排除模板。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 关闭页面的配置窗口，然后单击&#x200B;**[!UICONTROL Preview]**。

   将显示数据库中可用的Web应用程序列表。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在文件夹中添加过滤器 {#adding-a-filter-on-a-folder}

在概述中，您可以根据数据在Adobe Campaign树中的位置来选择访问数据。 这是文件夹上的过滤器。 应用以下流程将其添加到概述中。

1. 将光标放在Web应用程序的&#x200B;**[!UICONTROL Page]**&#x200B;节点上，并添加&#x200B;**[!UICONTROL Select folder]**&#x200B;元素(**[!UICONTROL Advanced controls > Select folder]**)。
1. 在出现的&#x200B;**[!UICONTROL Storage]**&#x200B;窗口中，单击&#x200B;**[!UICONTROL Edit variables]**&#x200B;链接。
1. 根据需要更改变量标签。
1. 使用&#x200B;**folder**&#x200B;值更改变量名称。

   >[!NOTE]
   >
   >变量的名称必须与链接到文件夹（在架构中定义）的元素的名称匹配，即在此例中，为&#x200B;**folder**。 引用表时必须重新使用此名称。

1. 将&#x200B;**[!UICONTROL XML]**&#x200B;类型应用到变量。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 选择&#x200B;**[!UICONTROL Refresh page]**&#x200B;交互。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 将光标放在列表上，并在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中，引用之前在列表的&#x200B;**[!UICONTROL Folder filter XPath]**&#x200B;选项卡中创建的变量。 您必须使用文件夹链接所关联元素的名称，即&#x200B;**文件夹**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >此时，Web应用程序不在其应用程序上下文中，因此无法在文件夹上测试过滤器。

## 添加按钮以配置新的Web应用程序 {#adding-a-button-to-configure-a-new-web-application}

1. 将光标放在&#x200B;**[!UICONTROL Page]**&#x200B;元素上并添加链接(**[!UICONTROL Static elements > Link]**)。
1. 修改链接标签，因为它将显示在概述的按钮上。

   在本例中，标签为&#x200B;**New**。

1. 在URL字段中插入以下URL:**xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms:** webApp与Web应用程序模式一致。
   >
   >**nms:** newWebApp与新的Web应用程序创建向导重合在一起。

1. 选择在同一窗口中显示URL。
1. 在图像字段中添加Web应用程序图标：**/nms/img/webApp.png**。

   此图标将显示在&#x200B;**[!UICONTROL New]**&#x200B;按钮上。

1. 在&#x200B;**[!UICONTROL Style]**&#x200B;字段中输入&#x200B;**button**。

   此样式在以前选择的&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;模板中引用。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 向列表添加详细信息 {#adding-detail-to-a-list}

在概述中配置列表时，您可以选择显示列表中每个条目的其他详细信息。

1. 将光标放在之前创建的列表元素上。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡的下拉列表中，选择&#x200B;**[!UICONTROL Columns and additional detail]**&#x200B;显示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中，添加&#x200B;**[!UICONTROL Primary key]** 、 **[!UICONTROL Internal name]**&#x200B;和&#x200B;**[!UICONTROL Description]**&#x200B;列，并为每个列选择&#x200B;**[!UICONTROL Hidden field]**&#x200B;选项。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   这样，此信息将只显示在每个条目的详细信息中。

1. 在&#x200B;**[!UICONTROL Additional detail]**&#x200B;选项卡中，添加以下代码：

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

在此部分中，您将创建一个过滤器，用于显示由特定运算符创建的Web应用程序的概述。 此过滤器使用链接编辑器创建。 选择运算符后，刷新列表以应用过滤器；这需要创建刷新链接。

这两个元素将分组到同一个容器中，以便以图形方式在概述中分组。

1. 将光标放在&#x200B;**[!UICONTROL Page]**&#x200B;元素上，然后选择&#x200B;**[!UICONTROL Container > Standard]**。
1. 将列数设置为&#x200B;**2**，以便链接编辑器和链接彼此相邻。

   ![](assets/s_ncs_configuration_webapp_container.png)

   有关元素布局的信息，请参阅[此部分](about-web-forms.md)。

1. 应用&#x200B;**dottedFilter**。

   此样式在以前选择的&#x200B;**[!UICONTROL Single-page Web applicatio]** n模板中引用。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用链接编辑器创建过滤器 {#creating-a-filter-using-a-link-editor}

1. 将光标放在上一阶段创建的容器上，并通过&#x200B;**[!UICONTROL Advanced controls]**&#x200B;菜单插入链接编辑器。
1. 在自动打开的存储窗口中，选择&#x200B;**[!UICONTROL Variables]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Edit variables]**&#x200B;链接并创建用于筛选数据的XML变量。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改标签。

   它将显示在概述的&#x200B;**[!UICONTROL Filter]**&#x200B;字段旁边。

1. 选择运算符表作为应用程序架构。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 将光标放在列表元素上，并通过&#x200B;**[!UICONTROL Data > Filter]**&#x200B;选项卡创建过滤器：

   * **表达式：** “创建者”链接的外键
   * **运算符：** 等于
   * **值：** 变量（变量）
   * **考虑if:** &#39;$(var2/@id)&#39;!=&quot;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web应用程序用户必须是具有相应Adobe Campaign权限的已识别操作员，才能访问信息。 此类配置不适用于匿名Web应用程序。

### 创建刷新链接 {#creating-a-refresh-link}

1. 将光标放在容器上，并通过&#x200B;**[!UICONTROL Static elements]**&#x200B;菜单插入&#x200B;**[!UICONTROL Link]**。
1. 修改标签。
1. 选择 **[!UICONTROL Refresh data in a list]**。
1. 添加之前创建的列表。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在&#x200B;**[!UICONTROL Image]**&#x200B;字段中添加刷新图标：**/xtk/img/refresh.png**。
1. 使用排序箭头重新组织Web应用程序的各个元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

Web应用程序现已配置完成。 您可以单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡进行预览。

![](assets/s_ncs_configuration_webapp_result.png)
