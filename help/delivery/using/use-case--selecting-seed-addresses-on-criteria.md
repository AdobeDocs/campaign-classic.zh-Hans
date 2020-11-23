---
solution: Campaign Classic
product: campaign
title: '"用例：根据条件选择种子地址"'
description: '"用例：根据条件选择种子地址"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---


# 用例：根据条件选择种子地址{#use-case-selecting-seed-addresses-on-criteria}

在投放或活动的框架中，通过链接 **[!UICONTROL Edit the dynamic condition...]** 可以根据特定选择条件选择种子地址。

在这种情况下，My在 **线图书馆** 希望根据客户的文学品味个性化其新闻稿。

与采购部门一起，负责投放的用户为购买警察小说的订户创建了新闻稿。

为了分享与他们协作的最终结果，投放经理决定将其采购部门的同事添加到投放，作为种子地址。 使用动态条件可节省配置和更新地址的时间。

要使用动态条件，您必须具有：

* 投放准备发送，
* 具有共同价值的种子地址。 此值可以是Adobe Campaign中已存在的字段。 在此示例中，种子地址在“部门”字段中共享“采购”值，默认情况下，该值不在应用程序中。

## 第1步——创建投放 {#step-1---creating-a-delivery}

创建投放的步骤详见创建 [电子邮件投放部分](../../delivery/using/creating-an-email-delivery.md) 。

在此示例中，投放管理器已创建Newsletter并选择收件人。

![](assets/dlv_seeds_usecase_01.png)

## 第2步——创建公用值 {#step-2---creating-a-common-value}

要创建与示例（采购部门）中相同的公用值，您必须先扩展模式的 **种子地址** ，并编辑关联的输入表单。

### 扩展数据模式 {#extending-the-data-schema}

有关模式扩展的更多详细信息，请参阅 [配置指南](../../configuration/using/data-schemas.md)。

1. 在节 **[!UICONTROL Administration > Configuration > Data schemas]** 点中，单击 **[!UICONTROL New]** 图标。
1. 在窗口 **[!UICONTROL Creation of a data schema]** 中，选择选 **[!UICONTROL Extension of a schema]** 项并单击 **[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 选择源 **[!UICONTROL Seed addresses]** 模式, **输入** doc作为 **[!UICONTROL Namespace]** 并单击 **[!UICONTROL Ok]**。

   ![](assets/dlv_seeds_usecase_10.png)

1. 单击 **[!UICONTROL Save]**.
1. 在模式编辑窗口中，复制下面的行并将其粘贴到屏幕截图中指示的区域。

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   然后复制以下行并将其粘贴到元素 **[!UICONTROL Seed to insert in the export files]** 下。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在这种情况下，您将指定在种子地址表中 **[!UICONTROL Department]** 已创建名为的新明细列表，并且它基于标准 **[!UICONTROL @company]** 明细列表模板(在种子地址表中 **的名称** 公司下标记)。

1. 单击 **[!UICONTROL Save]**.
1. In the **[!UICONTROL Tools > Advanced]** menu, select the **[!UICONTROL Update database structure]** option.

   ![](assets/dlv_seeds_usecase_12.png)

1. 显示更新向导时，单击按钮 **[!UICONTROL Next]** 以访问“编辑表”窗口：在种子地址数据模式中执行的更改需要结构更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 请按照向导操作，直到您转到页面运行更新。 单击 **[!UICONTROL Start]** 按钮。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成后，您可以关闭向导。

1. 断开连接，然后重新连接到Adobe Campaign。 种子地址数据模式中所做的更改现在有效。 要使种子地址屏幕显示它们，您必须更新关联的 **[!UICONTROL Input form]**。 请参阅更 [新输入表单部分](#updating-the-input-form) 。

#### 从链接的表扩展模式 {#extending-the-data-schema-from-a-linked-table}

种子地址模式可以使用来自链接到收件人模式的表的值-收件人(nms)。

例如，用户希望集成表中 **[!UICONTROL Internet Extension]** 找到的 **[!UICONTROL Country]** 链接到收件人模式。

![](assets/dlv_seeds_usecase_06.png)

因此，他们必须扩展种子地址模式，详见一节。 但是，要在步骤4中集 **成的代** 码行如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

他们表示：

* 用户想要创建一个名为 **[!UICONTROL Internet Extension]**,
* 这个元素来自 **[!UICONTROL Country]** 桌。

>[!CAUTION]
>
>在链接的表名称中，必须指定 **该链接表** 的xpath-dst。
>
>这可以在收件人表 **[!UICONTROL Country]** 的元素中找到。

![](assets/dlv_seeds_usecase_07.png)

然后，用户可以 **从该部** 分的步骤5进行操作，并 **[!UICONTROL Input form]** 更新种子地址。

请参阅更 [新输入表单部分](#updating-the-input-form) 。

#### 更新输入表单 {#updating-the-input-form}

1. 在节点 **[!UICONTROL Administration > Configuration > Input forms]** 中，找到种子地址输入表单。

   ![](assets/dlv_seeds_usecase_19.png)

1. 编辑表单，在容器中插入以 **[!UICONTROL Recipient]** 下行。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 保存更改。
1. 打开种子地址。 该字 **[!UICONTROL Department]** 段显示在表 **[!UICONTROL Recipient]** 中。

   ![](assets/dlv_seeds_usecase_22.png)

1. 编辑要用于种子地址的投放，并在字 **段** 中输入Purchasing **[!UICONTROL Department]** 值。

## 第3步——定义条件 {#step-3---defining-the-condition}

您现在可以指定种子地址的动态条件。 操作步骤：

1. 打开投放。

   ![](assets/dlv_seeds_usecase_01.png)

1. 单击链 **[!UICONTROL To]** 接，然后 **[!UICONTROL Seed addresses]** 单击选项卡以访问 **[!UICONTROL Edit the dynamic condition...]** 链接。

   ![](assets/dlv_seeds_usecase_02.png)

1. 选择表达式，以便您选择所需的种子地址。 此处，用户选择 **[!UICONTROL Department (@workField)]** 表达式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 选择所需的值。 在此示例中，用户从值 **的下拉** 列表中选择Purchasing部门。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前创建的模式扩展来自 **收件人** 模式。 上面屏幕上显示的值来自明细列表 **收件人** 。

1. 单击 **[!UICONTROL Ok]**.

   查询显示在窗 **[!UICONTROL Select target]** 口中。

   ![](assets/dlv_seeds_usecase_04.png)

1. Click **[!UICONTROL Ok]** to approve the query.
1. 分析投放，然后单击 **[!UICONTROL Delivery]** 选项卡以访问投放日志。

   采购部门的种子地址显示为待定投放，就像收件人或其他种子地址显示的一样。

   ![](assets/dlv_seeds_usecase_05.png)

1. Click the **[!UICONTROL Send]** button to start the delivery.

   采购部门的成员构成了将在其电子邮件收件箱中接收投放的部分种子地址。

   ![](assets/dlv_seeds_usecase_18.png)
