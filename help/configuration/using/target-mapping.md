---
title: 目标映射
seo-title: 目标映射
description: 目标映射
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 1%

---


# 目标映射{#target-mapping}

目标映射创建在以下两种情况下是必需的：

* 如果您使用的收件人表不是Adobe Campaign提供的表，
* 如果配置的过滤维度与目标映射屏幕上的标准定位维度不同。

目标映射创建向导将帮助您创建使用自定义表所需的所有模式。

## 创建和配置链接到自定义表的模式 {#creating-and-configuring-schemas-linked-to-the-custom-table}

在创建目标映射之前，需要进行多种配置，Adobe Campaign才能使用新的收件人模式。

为此，请应用以下步骤：

1. 新建一个模式，它集成要使用的自定义表的字段。

   有关详细信息，请参 [阅模式参考(xtk:srcSchema)](../../configuration/using/about-schema-reference.md)。

   在我们的示例中，我们将创建一个客户模式，一个非常简单的表，其中包含以下字段：ID，名字，姓氏，电子邮件地址，手机号码。 其目的是能够向存储在此表中的个人发送电子邮件或短信警报。

   示例模式(cus:individual)

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

1. 使用=&quot;true&quot;属性将模式声明为外部视图。 请参阅 [视图属性](../../configuration/using/schema-characteristics.md#the-view-attribute)。

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. 如果您需要添加直邮地址，请使用以下类型的结构：

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

1. 单击节 **[!UICONTROL Administration > Campaign management > Target mappings]** 点。
1. 单击“ **新建** ”按钮以打开目标映射创建向导。
1. 输入 **标签** 字段，并选择您刚在模式字段中创建 **的定位维度** 。

   ![](assets/mapping_diffusion_wizard_1.png)

1. 在“编 **辑地址表单** ”窗口中，选择与各种模式地址匹配的投放字段。 在此，我们能够映射 **@email****和@mobile** 字段。

   ![](assets/mapping_diffusion_wizard_2.png)

1. 在以下 **存储** 窗口中，输入“ **扩展模式的后缀** ”字段，将新模式与Adobe Campaign提供的现成模式区分开来。

   单 **[!UICONTROL Define new additional fields]** 击以选择要在投放中目标的维。

   默认情况下，排除管理与消息存储在同一个表中。 如果要 **为链接到存储的跟踪配置模式** ，请选中“生成要跟踪的存储”复选框。

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign不支持链接到相同广播和／或跟踪日志模式的多个收件人模式(称为定位模式)。 否则，这可能导致之后的数据协调出现异常。 有关此方面的详细信息，请参 [阅建议和限制](../../configuration/using/about-custom-recipient-table.md) 页。

1. 在“ **扩展** ”窗口中，选择要生成的可选模式(可用模式的列表取决于Adobe Campaign平台上安装的模块)。

   ![](assets/mapping_diffusion_wizard_4.png)

1. 单击“ **保存** ”按钮以关闭向导。

   该向导使用开始模式创建使新目标映射工作所需的所有其他模式。

   ![](assets/mapping_schema_list.png)

## 使用目标映射 {#using-target-mapping}

有两种方法可以将新模式用作投放的目标:

* 根据映射创建一个或多个投放模板
* 创建目标时，在投放选择过程中直接选择映射，如下所示：

![](assets/mapping_selection_ciblage.png)

**相关主题**

* [快速响应客户访问其数据的请求](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)