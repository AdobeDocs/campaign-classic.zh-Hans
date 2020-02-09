---
title: “用例：根据条件选择种子地址
seo-title: “用例：根据条件选择种子地址
description: “用例：根据条件选择种子地址
seo-description: null
page-status-flag: never-activated
uuid: 6af39893-6ef3-4204-8b53-0c16e35bac8f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: fa8aab62-e182-4388-aa23-c255b0dbd42e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 用例：在条件上选择种子地址{#use-case-selecting-seed-addresses-on-criteria}

在分发或营销活动的框架中，通过链接， **[!UICONTROL Edit the dynamic condition...]** 您可以根据特定的选择条件选择种子地址。

在此用例中，网站 **My online library** ，希望根据客户的文学品味个性化其新闻稿。

与采购部门一起，负责交付的用户为购买了警察小说的订户创建了新闻稿。

为了与他们分享其协作的最终结果，交付经理决定将采购部门的同事添加到交付中作为种子地址。 使用动态条件可节省配置和更新地址的时间。

要使用动态条件，您必须具有：

* 即将发送的送货，
* 具有相同值的种子地址。 此值可以是Adobe Campaign中已存在的字段。 在此示例中，种子地址在“部门”字段中共享“采购”值，默认情况下，该值不在应用程序中。

## 第1步——创建分发 {#step-1---creating-a-delivery}

创建电子邮件分发部分详细介绍了创 [建分发的步骤](../../delivery/using/creating-an-email-delivery.md) 。

在此示例中，交付管理器已创建Newsletter并选择收件人。

![](assets/dlv_seeds_usecase_01.png)

## 第2步——创建公用值 {#step-2---creating-a-common-value}

要创建与示例（采购部门）中相同的公用值，您必须首先扩展种子地址的数 **据架构** ，并编辑关联的输入表单。

### 扩展数据架构 {#extending-the-data-schema}

有关架构扩展的更多详细信息，请参阅配 [置指南](../../configuration/using/data-schemas.md)。

1. 在节 **[!UICONTROL Administration > Configuration > Data schemas]** 点中，单击图 **[!UICONTROL New]** 标。
1. 在窗 **[!UICONTROL Creation of a data schema]** 口中，选择选 **[!UICONTROL Extension of a schema]** 项并单击 **[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 选择源 **[!UICONTROL Seed addresses]** 架构，输入 **doc** 作为 **[!UICONTROL Namespace]** ，然后单击 **[!UICONTROL Ok]**。

   ![](assets/dlv_seeds_usecase_10.png)

1. 单击 **[!UICONTROL Save]**.
1. 在架构编辑窗口中，复制下面的行并将其粘贴到屏幕截图中指示的区域。

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   然后，复制以下行并将其粘贴到元素 **[!UICONTROL Seed to insert in the export files]** 下。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在这种情况下，您将指定在种子地址表中已创建名为的新枚举，该枚举基于标准枚举模板(在种子地址表中的 **[!UICONTROL Department]** Company **[!UICONTROL @company]****** 名称下标记)。

1. 单击 **[!UICONTROL Save]**.
1. 在菜 **[!UICONTROL Tools > Advanced]** 单中，选择选 **[!UICONTROL Update database structure]** 项。

   ![](assets/dlv_seeds_usecase_12.png)

1. 显示更新向导时，单击按钮 **[!UICONTROL Next]** 以访问“编辑表”窗口：在种子地址数据架构中执行的更改需要结构更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 请按照向导进行操作，直到您进入页面运行更新。 Click the **[!UICONTROL Start]** button.

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成后，您可以关闭向导。

1. 断开连接，然后重新连接到Adobe Campaign。 在种子地址数据架构中所做的更改现已生效。 要使它们在种子地址屏幕中可见，您必须更新关联的 **[!UICONTROL Input form]**。 请参阅更 [新输入表单部分](#updating-the-input-form) 。

#### 从链接的表扩展数据架构 {#extending-the-data-schema-from-a-linked-table}

种子地址数据模式可以使用来自链接到接收者数据模式——接收者(nms)的表的值。

例如，用户希望集成在链接到收 **[!UICONTROL Internet Extension]** 件人架构的 **[!UICONTROL Country]** 表中找到的内容。

![](assets/dlv_seeds_usecase_06.png)

因此，它们必须扩展“种子地址”数据架构，详见章节。 但是，在步骤4中要集成的 **代码行** 如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它们表示：

* 用户想要创建一个名为 **[!UICONTROL Internet Extension]**,
* 这个元素来自表 **[!UICONTROL Country]** 格。

>[!CAUTION]
>
>在链接的表名中，必须指定所 **述链接表的xpath** -dst。
>
>这可以在收件人表 **[!UICONTROL Country]** 格的元素中找到。

![](assets/dlv_seeds_usecase_07.png)

然后，用户可以从该部 **分的步骤** 5中进行操作 **[!UICONTROL Input form]** ，并更新种子地址。

请参阅更 [新输入表单部分](#updating-the-input-form) 。

#### 更新输入表单 {#updating-the-input-form}

1. 在节点 **[!UICONTROL Administration > Configuration > Input forms]** 中，查找种子地址输入表单。

   ![](assets/dlv_seeds_usecase_19.png)

1. 编辑表单，并在容器中插入以下 **[!UICONTROL Recipient]** 行。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 保存更改。
1. 打开种子地址。 该字 **[!UICONTROL Department]** 段显示在表 **[!UICONTROL Recipient]** 中。

   ![](assets/dlv_seeds_usecase_22.png)

1. 编辑要用于交货的种子地址，并在字段中输 **入** Purchasing作为 **[!UICONTROL Department]** 值。

## 第3步——定义条件 {#step-3---defining-the-condition}

您现在可以指定传送种子地址的动态条件。 操作步骤：

1. 打开分发。

   ![](assets/dlv_seeds_usecase_01.png)

1. 单击链 **[!UICONTROL To]** 接，然后单击 **[!UICONTROL Seed addresses]** 选项卡以访问链 **[!UICONTROL Edit the dynamic condition...]** 接。

   ![](assets/dlv_seeds_usecase_02.png)

1. 选择允许您选择所需种子地址的表达式。 此处，用户选择表达 **[!UICONTROL Department (@workField)]** 式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 选择所需的值。 在此示例中，用户从值的下 **拉列表中** ，选择采购部门。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前创建的架构扩展来自收件 **人架构** 。 以上屏幕上显示的值来自收件人架构的 **枚举** 。

1. 单击 **[!UICONTROL Ok]**.

   查询显示在窗 **[!UICONTROL Select target]** 口中。

   ![](assets/dlv_seeds_usecase_04.png)

1. 单击 **[!UICONTROL Ok]** 以批准查询。
1. 分析您的交付，然后单击 **[!UICONTROL Delivery]** 选项卡以访问交付日志。

   采购部门的种子地址显示为待交付，就像收件人或其他种子地址一样。

   ![](assets/dlv_seeds_usecase_05.png)

1. 单击按 **[!UICONTROL Send]** 钮以开始传送。

   采购部门的成员构成了种子地址的一部分，这些种子地址将在其电子邮件收件箱中接收传送。

   ![](assets/dlv_seeds_usecase_18.png)
