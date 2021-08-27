---
product: campaign
title: 目标映射
description: 了解如何创建目标映射
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 2%

---

# 目标映射{#target-mapping}

![](../../assets/v7-only.svg)

在以下两种情况下，需要创建目标映射：

* 如果您使用的收件人表不是Adobe Campaign提供的表，
* 如果您配置的过滤维度与目标映射屏幕上的标准定向维度不同，则会将其设置为。

目标映射创建向导将帮助您创建使用自定义表所需的所有架构。

## 创建和配置链接到自定义表的架构 {#creating-and-configuring-schemas-linked-to-the-custom-table}

在创建目标映射之前，需要进行多种配置，以便Adobe Campaign能够使用新的收件人数据架构进行操作。

要执行此操作，请应用以下步骤：

1. 创建新的数据架构，该架构集成了您要使用的自定义表的字段。

   有关更多信息，请参阅[架构引用(xtk:srcSchema)](../../configuration/using/about-schema-reference.md)。

   在我们的示例中，我们将创建一个客户架构，一个包含以下字段的非常简单的表：ID、名字、姓氏、电子邮件地址、手机号码。 其目的是能够向存储在此表中的个人发送电子邮件或短信警报。

   示例架构(cus:indivial)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. 使用=&quot;true&quot;属性将架构声明为外部视图。 请参阅[视图属性](../../configuration/using/schema-characteristics.md#the-view-attribute)。

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. 如果需要添加直邮地址，请使用以下类型的结构：

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. 单击&#x200B;**[!UICONTROL Administration > Campaign management > Target mappings]**&#x200B;节点。
1. 单击&#x200B;**New**&#x200B;按钮以打开目标映射创建向导。
1. 输入&#x200B;**Label**&#x200B;字段，然后选择您刚在&#x200B;**定向维度**&#x200B;字段中创建的架构。

   ![](assets/mapping_diffusion_wizard_1.png)

1. 在&#x200B;**编辑地址表单**&#x200B;窗口中，选择与各种投放地址匹配的架构字段。 在此，我们能够映射&#x200B;**@email**&#x200B;和&#x200B;**@mobile**&#x200B;字段。

   ![](assets/mapping_diffusion_wizard_2.png)

1. 在以下&#x200B;**Storage**&#x200B;窗口中，输入扩展架构的&#x200B;**后缀字段**&#x200B;以区分新架构与Adobe Campaign提供的现成架构。

   单击&#x200B;**[!UICONTROL Define new additional fields]**&#x200B;以选择要在投放中定向的维度。

   默认情况下，排除管理会存储在与消息相同的表中。 如果要为链接到目标映射的跟踪配置存储，请选中&#x200B;**生成用于跟踪的存储架构**&#x200B;框。

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign不支持多个收件人模式（称为定位模式），这些模式链接到相同的broadlog和/或跟踪日志模式。 否则，这可能会导致以后的数据协调出现异常。 有关此内容的更多信息，请参阅[推荐和限制](../../configuration/using/about-custom-recipient-table.md)页面。

1. 在&#x200B;**扩展**&#x200B;窗口中，选择要生成的可选架构(可用架构列表取决于在Adobe Campaign平台上安装的模块)。

   ![](assets/mapping_diffusion_wizard_4.png)

1. 单击&#x200B;**Save**&#x200B;按钮以关闭向导。

   该向导使用启动架构创建新目标映射工作所需的所有其他架构。

   ![](assets/mapping_schema_list.png)

## 使用目标映射 {#using-target-mapping}

可使用新架构作为投放目标的两种方式：

* 基于映射创建一个或多个投放模板
* 创建投放时，在目标选择期间直接选择映射，如下所示：

![](assets/mapping_selection_ciblage.png)

**相关主题**

* [快速响应客户访问其数据的请求](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)
