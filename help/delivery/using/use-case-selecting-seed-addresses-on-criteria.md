---
product: campaign
title: “用例：根据条件选择种子地址”
description: “用例：根据条件选择种子地址”
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# 用例：根据条件选择种子地址{#use-case-selecting-seed-addresses-on-criteria}


在投放或营销策划的框架内，**[!UICONTROL Edit the dynamic condition...]**&#x200B;链接允许您根据特定的选择条件选择种子地址。

在此使用案例中，网站&#x200B;**我的在线图书馆**&#x200B;希望根据客户的文学品味，将其新闻稿个性化。

负责递送的用户与购买部门合作，为购买警察小说的订阅者制作了一本通讯。

为了共享他们与交付人员协作的最终结果，交付经理决定将其采购部门的同事作为种子地址添加到交付中。 使用动态条件可以节省配置和更新地址的时间。

要使用动态条件，您必须具有：

* 准备发送的投放，
* 具有公共值的种子地址。 此值可以是Adobe Campaign中已存在的字段。 在本例中，种子地址共享“Department”字段中的“Purchasing”值，默认情况下，该值不在应用程序中。

## 步骤1 — 创建投放 {#step-1---creating-a-delivery}

有关创建投放的详细步骤，请参见[创建电子邮件投放](creating-an-email-delivery.md)一节。

在本例中，投放经理已创建新闻稿并选择收件人。

![](assets/dlv_seeds_usecase_01.png)

## 第2步 — 创建公共值 {#step-2---creating-a-common-value}

若要创建类似于示例（采购部门）中的通用值，您必须首先扩展种子地址的&#x200B;**数据架构**，并编辑关联的输入表单。

### 扩展数据架构 {#extending-the-data-schema}

有关架构扩展的详细信息，请参阅[此部分](../../configuration/using/data-schemas.md)。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;节点中，单击&#x200B;**[!UICONTROL New]**&#x200B;图标。
1. 在&#x200B;**[!UICONTROL Creation of a data schema]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Extension of a schema]**&#x200B;选项并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 选择&#x200B;**[!UICONTROL Seed addresses]**&#x200B;源架构，输入&#x200B;**doc**&#x200B;作为&#x200B;**[!UICONTROL Namespace]**，然后单击&#x200B;**[!UICONTROL Ok]**。

   ![](assets/dlv_seeds_usecase_10.png)

1. 单击 **[!UICONTROL Save]**。
1. 在架构编辑窗口中，复制以下行并将其粘贴到屏幕快照中指示的区域中。

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   然后，复制以下行并将其粘贴到&#x200B;**[!UICONTROL Seed to insert in the export files]**&#x200B;元素下。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在这种情况下，您正在指定已在种子地址表中创建了名为&#x200B;**[!UICONTROL Department]**&#x200B;的新枚举，该枚举基于标准&#x200B;**[!UICONTROL @company]**&#x200B;枚举模板（在种子地址表单中的名称&#x200B;**Company**&#x200B;下标记）。

1. 单击 **[!UICONTROL Save]**。
1. 在&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;菜单中，选择&#x200B;**[!UICONTROL Update database structure]**&#x200B;选项。

   ![](assets/dlv_seeds_usecase_12.png)

1. 显示更新助手时，单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮以访问“编辑表”窗口：在种子地址数据架构中执行的更改需要结构更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 请按照该助手操作，直到您进入页面运行更新为止。 单击 **[!UICONTROL Start]** 按钮。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成后，可以关闭该助手。

1. 断开连接，然后重新连接到Adobe Campaign。 现在，在种子地址数据架构中所做的更改生效。 为了从种子地址屏幕中可见，您必须更新关联的&#x200B;**[!UICONTROL Input form]**。 请参阅[更新输入表单](#updating-the-input-form)部分。

#### 从链接表扩展数据模式 {#extending-the-data-schema-from-a-linked-table}

种子地址数据模式可以使用链接到收件人数据模式 — 收件人(nms)的表中的值。

例如，用户希望集成在链接到收件人架构的&#x200B;**[!UICONTROL Country]**&#x200B;表中找到的&#x200B;**[!UICONTROL Internet Extension]**。

![](assets/dlv_seeds_usecase_06.png)

因此，他们必须扩展种子地址数据模式，如部分所述。 但是，要在&#x200B;**步骤4**&#x200B;中集成的代码行如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它们表示：

* 用户想要创建一个名为&#x200B;**[!UICONTROL Internet Extension]**&#x200B;的新元素，
* 此元素来自&#x200B;**[!UICONTROL Country]**&#x200B;表。

>[!CAUTION]
>
>在链接表名称中，必须指定该链接表的&#x200B;**xpath-dst**。
>
>这可以在收件人表的&#x200B;**[!UICONTROL Country]**&#x200B;元素中找到。

![](assets/dlv_seeds_usecase_07.png)

然后，用户可以按照该部分的&#x200B;**步骤5**&#x200B;进行操作，并更新种子地址的&#x200B;**[!UICONTROL Input form]**。

请参阅[更新输入表单](#updating-the-input-form)部分。

#### 更新输入表单 {#updating-the-input-form}

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Input forms]**&#x200B;节点中，查找种子地址输入表单。

   ![](assets/dlv_seeds_usecase_19.png)

1. 编辑表单并在&#x200B;**[!UICONTROL Recipient]**&#x200B;容器中插入以下行。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 保存您的更改。
1. 打开种子地址。 **[!UICONTROL Department]**&#x200B;字段出现在&#x200B;**[!UICONTROL Recipient]**&#x200B;表中。

   ![](assets/dlv_seeds_usecase_22.png)

1. 编辑要用于投放的种子地址，并在&#x200B;**[!UICONTROL Department]**&#x200B;字段中输入&#x200B;**Purchasing**&#x200B;作为值。

## 步骤3 — 定义条件 {#step-3---defining-the-condition}

您现在可以为投放指定种子地址的动态条件。 操作步骤：

1. 打开投放。

   ![](assets/dlv_seeds_usecase_01.png)

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡以访问&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;链接。

   ![](assets/dlv_seeds_usecase_02.png)

1. 选择用于选择所需种子地址的表达式。 在此处，用户选择&#x200B;**[!UICONTROL Department (@workField)]**&#x200B;表达式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 选择所需的值。 在此示例中，用户从下拉值列表中选择&#x200B;**采购**&#x200B;部门。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >之前创建的架构扩展来自&#x200B;**收件人**&#x200B;架构。 上述屏幕上显示的值来自&#x200B;**收件人**&#x200B;架构的枚举。

1. 单击 **[!UICONTROL Ok]**。

   查询显示在&#x200B;**[!UICONTROL Select target]**&#x200B;窗口中。

   ![](assets/dlv_seeds_usecase_04.png)

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;批准查询。
1. 分析您的投放，然后单击&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡以访问投放日志。

   采购部门的种子地址将显示为待定投放，与收件人或其他种子地址类似。

   ![](assets/dlv_seeds_usecase_05.png)

1. 单击&#x200B;**[!UICONTROL Send]**&#x200B;按钮开始投放。

   购买部门的成员构成了您的种子地址的一部分，您将在其电子邮件收件箱中接收投放。

   ![](assets/dlv_seeds_usecase_18.png)
