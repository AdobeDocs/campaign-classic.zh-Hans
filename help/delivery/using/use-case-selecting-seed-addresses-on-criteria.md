---
product: campaign
title: “用例：根据条件选择种子地址”
description: “用例：根据条件选择种子地址”
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# 用例：根据条件选择种子地址{#use-case-selecting-seed-addresses-on-criteria}


在投放或营销策划的框架内， **[!UICONTROL Edit the dynamic condition...]** 链接允许您根据特定的选择条件选择种子地址。

在此用例中，站点 **我的联机库** 想要根据客户的文学品味打造个性化的电子报。

负责递送的用户与购买部门合作，为购买警察小说的订阅者制作了一本通讯。

为了共享他们与交付人员协作的最终结果，交付经理决定将其采购部门的同事作为种子地址添加到交付中。 使用动态条件可以节省配置和更新地址的时间。

要使用动态条件，您必须具有：

* 准备发送的投放，
* 具有公共值的种子地址。 此值可以是Adobe Campaign中已存在的字段。 在本例中，种子地址共享“Department”字段中的“Purchasing”值，默认情况下，该值不在应用程序中。

## 步骤1 — 创建投放 {#step-1---creating-a-delivery}

有关创建投放的详细步骤，请参见 [创建电子邮件投放](creating-an-email-delivery.md) 部分。

在本例中，投放经理已创建新闻稿并选择收件人。

![](assets/dlv_seeds_usecase_01.png)

## 第2步 — 创建公共值 {#step-2---creating-a-common-value}

要创建与我们示例（采购部门）中相同的公用值，您必须先扩展 **数据架构** 并编辑关联的输入表单。

### 扩展数据架构 {#extending-the-data-schema}

有关架构扩展的详细信息，请参阅 [本节](../../configuration/using/data-schemas.md).

1. 在 **[!UICONTROL Administration > Configuration > Data schemas]** 节点，单击 **[!UICONTROL New]** 图标。
1. 在 **[!UICONTROL Creation of a data schema]** 窗口中，选择 **[!UICONTROL Extension of a schema]** 选项并单击 **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. 选择 **[!UICONTROL Seed addresses]** 源架构，输入 **文档** 作为 **[!UICONTROL Namespace]** 并单击 **[!UICONTROL Ok]**.

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

   然后，复制以下行并将其粘贴到 **[!UICONTROL Seed to insert in the export files]** 元素。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在这种情况下，您将指定名为 **[!UICONTROL Department]** 已在种子地址表中创建，并且它基于标准 **[!UICONTROL @company]** 枚举模板（在名称下标记） **公司** （在种子地址表单中）。

1. 单击 **[!UICONTROL Save]**。
1. 在 **[!UICONTROL Tools > Advanced]** 菜单，选择 **[!UICONTROL Update database structure]** 选项。

   ![](assets/dlv_seeds_usecase_12.png)

1. 显示更新向导时，单击 **[!UICONTROL Next]** 按钮访问“编辑表”窗口：在种子地址数据模式中执行的更改需要结构更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 按照向导操作，直到您进入页面运行更新。 单击 **[!UICONTROL Start]** 按钮。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成后，可以关闭向导。

1. 断开连接，然后重新连接到Adobe Campaign。 现在，在种子地址数据架构中所做的更改生效。 为了使其在种子地址屏幕中可见，您必须更新关联的 **[!UICONTROL Input form]**. 请参阅 [更新输入表单](#updating-the-input-form) 部分。

#### 从链接表扩展数据模式 {#extending-the-data-schema-from-a-linked-table}

种子地址数据模式可以使用链接到收件人数据模式 — 收件人(nms)的表中的值。

例如，用户希望将 **[!UICONTROL Internet Extension]** 可在 **[!UICONTROL Country]** 链接到收件人模式的表。

![](assets/dlv_seeds_usecase_06.png)

因此，他们必须扩展种子地址数据模式，如部分所述。 但是，要集成到的代码行位于 **步骤4** 如下所示：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它们表示：

* 用户希望创建一个名为的新元素 **[!UICONTROL Internet Extension]**，
* 此元素来自 **[!UICONTROL Country]** 表格。

>[!CAUTION]
>
>在链接表名称中，必须指定 **xpath-dst** 的链接。
>
>这可以在 **[!UICONTROL Country]** 元素。

![](assets/dlv_seeds_usecase_07.png)

然后，用户可以从以下位置关注 **步骤5** 部分，并更新 **[!UICONTROL Input form]** 种子地址的。

请参阅 [更新输入表单](#updating-the-input-form) 部分。

#### 更新输入表单 {#updating-the-input-form}

1. 在 **[!UICONTROL Administration > Configuration > Input forms]** 节点，查找种子地址输入表单。

   ![](assets/dlv_seeds_usecase_19.png)

1. 编辑表单并将以下行插入到 **[!UICONTROL Recipient]** 容器。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 保存您的更改。
1. 打开种子地址。 此 **[!UICONTROL Department]** 字段，请参见 **[!UICONTROL Recipient]** 表格。

   ![](assets/dlv_seeds_usecase_22.png)

1. 编辑要用于投放的种子地址并输入 **采购** 作为 **[!UICONTROL Department]** 字段。

## 步骤3 — 定义条件 {#step-3---defining-the-condition}

您现在可以为投放指定种子地址的动态条件。 操作步骤：

1. 打开投放。

   ![](assets/dlv_seeds_usecase_01.png)

1. 单击 **[!UICONTROL To]** 链接然后 **[!UICONTROL Seed addresses]** 选项卡访问 **[!UICONTROL Edit the dynamic condition...]** 链接。

   ![](assets/dlv_seeds_usecase_02.png)

1. 选择用于选择所需种子地址的表达式。 在此处，用户选择 **[!UICONTROL Department (@workField)]** 表达式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 选择所需的值。 在此示例中，用户选择 **采购** 的值下拉列表中的部门。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >之前创建的架构扩展来自 **收件人** 架构。 上述屏幕上显示的值来自 **收件人** 架构。

1. 单击 **[!UICONTROL Ok]**。

   查询显示在 **[!UICONTROL Select target]** 窗口。

   ![](assets/dlv_seeds_usecase_04.png)

1. 单击 **[!UICONTROL Ok]** 以批准查询。
1. 分析您的投放，然后单击 **[!UICONTROL Delivery]** 选项卡访问投放日志。

   采购部门的种子地址将显示为待定投放，与收件人或其他种子地址类似。

   ![](assets/dlv_seeds_usecase_05.png)

1. 单击 **[!UICONTROL Send]** 按钮开始投放。

   购买部门的成员构成了您的种子地址的一部分，您将在其电子邮件收件箱中接收投放。

   ![](assets/dlv_seeds_usecase_18.png)
