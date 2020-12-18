---
solution: Campaign Classic
product: campaign
title: 目标映射
description: 了解如何创建目标映射
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# 目标映射{#target-mapping}

目标映射创建在以下两种情况下是必需的：

* 如果您使用的收件人表不是Adobe Campaign提供的表，
* 如果配置的过滤维度与目标映射屏幕上的标准定位维度不同。

目标映射创建向导将帮助您创建使用自定义表所需的所有模式。

## 创建和配置链接到自定义表{#creating-and-configuring-schemas-linked-to-the-custom-table}的模式

在创建目标映射之前，需要进行多种配置，Adobe Campaign才能使用新的收件人模式。

为此，请应用以下步骤：

1. 新建一个模式，它集成要使用的自定义表的字段。

   有关详细信息，请参阅[模式引用(xtk:srcSchema)](../../configuration/using/about-schema-reference.md)。

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

1. 使用=&quot;true&quot;属性将模式声明为外部视图。 请参阅[视图属性](../../configuration/using/schema-characteristics.md#the-view-attribute)。

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

1. 单击&#x200B;**[!UICONTROL Administration > Campaign management > Target mappings]**&#x200B;节点。
1. 单击&#x200B;**新建**&#x200B;按钮以打开目标映射创建向导。
1. 输入&#x200B;**标签**&#x200B;字段，并选择刚在&#x200B;**定位维度**&#x200B;字段中创建的模式。

   ![](assets/mapping_diffusion_wizard_1.png)

1. 在&#x200B;**编辑地址表单**&#x200B;窗口中，选择与各种模式地址匹配的投放字段。 在此，我们能够映射&#x200B;**@email**&#x200B;和&#x200B;**@mobile**&#x200B;字段。

   ![](assets/mapping_diffusion_wizard_2.png)

1. 在下面的&#x200B;**存储**&#x200B;窗口中，输入扩展模式&#x200B;**后缀字段，将新模式与Adobe Campaign提供的现成模式区分开来。**

   单击&#x200B;**[!UICONTROL Define new additional fields]**&#x200B;以选择要在投放中目标的维。

   默认情况下，排除管理与消息存储在同一个表中。 如果要为链接到您的存储的跟踪配置存储，请选中&#x200B;**生成跟踪模式**&#x200B;框。

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign不支持链接到相同广播和／或跟踪日志模式的多个收件人模式(称为定位模式)。 否则，这可能导致之后的数据协调出现异常。 有关此信息，请参阅[建议和限制](../../configuration/using/about-custom-recipient-table.md)页。

1. 在&#x200B;**扩展**&#x200B;窗口中，选择要生成的可选模式(可用模式的列表取决于Adobe Campaign平台上安装的模块)。

   ![](assets/mapping_diffusion_wizard_4.png)

1. 单击&#x200B;**保存**&#x200B;按钮以关闭向导。

   该向导使用开始模式创建使新目标映射工作所需的所有其他模式。

   ![](assets/mapping_schema_list.png)

## 使用目标映射{#using-target-mapping}

有两种方法可以将新模式用作投放的目标:

* 根据映射创建一个或多个投放模板
* 创建目标时，在投放选择过程中直接选择映射，如下所示：

![](assets/mapping_selection_ciblage.png)

**相关主题**

* [快速响应客户访问其数据的请求](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)