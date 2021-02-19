---
solution: Campaign Classic
product: campaign
title: 通过 JavaScript 集成（客户端）
description: 通过 JavaScript 集成（客户端）
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 2%

---


# 通过 JavaScript 集成（客户端）{#integration-via-javascript-client-side}

要在网页中调用交互引擎，请将对JavaScript代码的调用直接插入该页。 此调用返回目标位置中的优惠内容

元素。

Adobe建议使用JavaScript集成方法。

调用URL的脚本如下所示：

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

“**env**”参数接收专用于匿名交互的实时环境的内部名称。

要演示优惠，我们需要在Adobe Campaign中创建环境和优惠空间，然后配置HTML页。

以下用例详细介绍了通过JavaScript集成优惠的可能选项。

## HTML模式{#html-mode}

### 呈现匿名优惠{#presenting-an-anonymous-offer}

1. **准备交互引擎**

   打开Adobe Campaign界面并准备匿名环境。

   创建链接到匿名优惠空间的环境。

   创建一个优惠及其链接到该优惠空间的表示形式。

1. **HTML页面的内容**

   HTML页面必须包含

   元素(具有@id属性)，其值为已创建优惠空间的内部名称(“i_internal name space”)。 优惠将插入此
元素。

   在我们的示例中，@id属性接收“i_SPC12”值，其中“SPC12”是先前创建的优惠空间的内部名称：

   ```
   <div id="i_SPC12"></div>
   ```

   在我们的示例中，调用脚本的URL如下(“OE3”是实时环境的内部名称):

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!IMPORTANT]
   >
   >`<script>`标签不能自闭。

   此静态调用将自动生成一个动态调用，其中包含交互引擎所需的所有参数。

   此行为允许您在同一页面上使用多个优惠空间，通过对引擎的单次调用进行管理。

1. **HTML页中的结果**

   优惠呈现的内容通过交互引擎返回到HTML页：

   ```
   <div id="banner_header">
     <div id="i_SPC12">
       <table>
         <tbody>
           <tr>
             <td><h3>Fly to Japan!</h3></td>
           </tr>
           <tr>
             <td><img width="150px" src="https://instance.adobe.org/res/Track/874fdaf72ddc256b2d8260bb8ec3a104.jpg"></td>
             <td>
               <p>Discover Japan for 2 weeks at an unbelievable price!!</p>
               <p><b>2345 Dollars - All inclusive</b></p>
             </td>
           </tr>
         </tbody>
       </table>
     </div>
     <script src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" id="interactionProposalScript" type="text/javascript"></script>
   </div>
   ```

### 呈现已识别的优惠{#presenting-an-identified-offer}

要向已识别的联系人展示优惠，该过程与此处详述的过程类似：[呈现匿名优惠](#presenting-an-anonymous-offer)。 在网页的内容中，您需要添加以下脚本，以在调用引擎时识别联系人：

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. 转到将由网页调用的优惠空间，单击&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;并添加一个或多个标识键。

   ![](assets/interaction_htmlmode_001.png)

   在此示例中，标识键是复合的，因为它既基于电子邮件，也基于收件人名。

1. 在网页显示过程中，脚本评估允许您将收件人ID传递给优惠引擎。 如果ID是复合的，则按与高级设置中相同的顺序显示键，并由 |.

   在以下示例中，该联系人已登录到该网站，在调用交互引擎时，由于其电子邮件和姓名被识别。

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### 使用HTML呈现函数{#using-an-html-rendering-function}

要自动生成HTML优惠呈现，可以使用渲染函数。

1. 转到优惠空间并单击&#x200B;**[!UICONTROL Edit functions]**&#x200B;链接。
1. 选择 **[!UICONTROL Overload the HTML rendering function]**。
1. 转到&#x200B;**[!UICONTROL HTML rendering]**&#x200B;选项卡，并插入与优惠空间中为优惠内容定义的字段相匹配的变量。

   ![](assets/interaction_htmlmode_002.png)

   在此示例中，优惠以网页横幅的形式显示，由可单击图像和与优惠内容中定义的字段相匹配的标题组成。

## XML模式{#xml-mode}

### 呈现优惠{#presenting-an-offer}

通过交互，可将XML节点返回到调用优惠引擎的HTML页。 该XML节点可以由客户端开发的函数进行处理。

对交互引擎的调用如下所示：

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

“**env**”参数接收实时环境的内部名称。

“**cb**”参数接收将读取由包含（回调）命题的引擎返回的XML节点的函数的名称。 此参数是可选的。

“**t**”参数仅用于标识的交互，才接收目标的值。 此参数也可以与&#x200B;**interactionTarget**&#x200B;变量一起传递。 此参数是可选的。

“**c**”参数接收列表的内部名称。 此参数是可选的。

“**th**”参数接收主题列表。 此参数是可选的。

“**gctx**”参数接收整个页面的全局调用数据（上下文）。 此参数是可选的。

返回的XML节点如下所示：

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

以下用例详细说明了在Adobe Campaign中执行的配置以启用XML模式，然后在HTML页中显示对引擎的调用结果。

1. **创建环境和优惠空间**

   有关创建环境的详细信息，请参阅[实时/设计环境](../../interaction/using/live-design-environments.md)。

   有关创建优惠空间的详细信息，请参阅[创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

1. **扩展优惠模式以添加新字段**

   此模式将定义以下字段：标题2和价格。

   示例中模式的名称为&#x200B;**cus:优惠**

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2013-01-18 17:14:20.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="2013-01-18 15:20:18.373Z"
              mappingType="sql" md5="F14A7AA009AE1FCE31B0611E72866AC3" modifiedBy-id="0"
              name="offer" namespace="cus" xtkschema="xtk:srcSchema">
     <createdBy _cs="Administrator (admin)"/>
     <modifiedBy _cs="Administrator (admin)"/>
     <element img="nms:offer.png" label="Marketing offers" labelSingular="Marketing offer"
              name="offer">
       <element label="Content" name="view">
         <element label="Price" name="price" type="long" xml="true"/>
         <element label="Title 2" name="title2" type="string" xml="true"/>
   
         <element advanced="true" desc="Price calculation script." label="Script price"
                  name="price_jst" type="CDATA" xml="true"/>
         <element advanced="true" desc="Title calculation script." label="Script title"
                  name="title2_jst" type="CDATA" xml="true"/>
       </element>
     </element>
   </srcSchema>
   ```

   >[!IMPORTANT]
   >
   >每个元素需定义两次。 CDATA(&quot;_jst&quot;)类型元素可以包含个性化字段。
   >
   >不要忘记更新数据库结构。 如需详细信息，请参阅[此部分](../../configuration/using/updating-the-database-structure.md)。

   >[!NOTE]
   >
   >您可以扩展优惠模式，以批处理和统一模式以及任何格式（文本、HTML和XML）添加新字段。

1. **扩展优惠公式以编辑新字段和修改现有字段**

   编辑&#x200B;**优惠(nsm)**&#x200B;输入表单。

   在“视图”部分，插入包含以下内容的两个新字段：

   ```
   <input label="Title 2" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="title2_jst">
                   <form label="Edit title 2" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizeTitle2">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizeTitle2"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input nolabel="true" type="edit" xpath="title2_jst"/>
   
                 <input label="Price" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="price_jst">
                   <form label="Edit price" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizePrice">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizePrice"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input colspan="2" label="Prix" nolabel="true" type="number" xpath="price_jst"/>
   ```

   注释掉目标URL字段：

   ![](assets/interaction_xmlmode_form_001.png)

   >[!IMPORTANT]
   >
   >(`<input>`)表单的字段必须指向在创建的模式中定义的CDATA类型元素。

   “优惠呈现”表单中的渲染如下所示：

   ![](assets/interaction_xmlmode_form.png)

   已添加&#x200B;**[!UICONTROL Title 2]**&#x200B;和&#x200B;**[!UICONTROL Price]**&#x200B;字段，不再显示&#x200B;**[!UICONTROL Destination URL]**&#x200B;字段。

1. **创建优惠**

   有关创建优惠的详细信息，请参阅[创建优惠](../../interaction/using/creating-an-offer.md)。

   在以下用例中，按如下方式输入优惠:

   ![](assets/interaction_xmlmode_offer.png)

1. 批准优惠或让其他人批准它，然后在上一步创建的优惠空间上激活它，以便在链接的实时环境中提供它。
1. **HTML页上的引擎调用和结果**

   在HTML页面中对交互引擎的调用如下所示：

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   “**env**”参数的值是实时环境的内部名称。

   “**cb**”参数的值是需要解释引擎返回的XML节点的函数名。 在我们的示例中，调用的函数打开一个模态窗口(alert()函数)。

   交互引擎返回的XML节点如下所示：

   ```
   <propositions>
    <proposition id="a28002" offer-id="10322005" weight="1" rank="1" space="SPC14" div="i_SPC14">
     <xmlOfferView>
      <title>Travel to Russia</title>
      <price>3456</price>
      <description>Discover this vacation package!INCLUDES 10 nights. FEATURES buffet breakfast daily. BONUS 5th night free.</description>
      <image>
       <path>https://myinstance.com/res/Track/ae1d2113ed732d58a3beb441084e5960.jpg</path>
       <alt>Travel to Russia</alt>
      </image>
     </xmlOfferView>
    </proposition>
   </propositions>
   ```

### 使用呈现函数{#using-a-rendering-function-}

可以使用XML渲染功能创建优惠演示文稿。 此函数将修改在调用引擎期间返回到HTML页的XML节点。

1. 转到优惠空间并单击&#x200B;**[!UICONTROL Edit functions]**&#x200B;链接。
1. 选择 **[!UICONTROL Overload the XML rendering function]**。
1. 转到&#x200B;**[!UICONTROL XML rendering]**&#x200B;选项卡并插入所需的函数。

   该函数可以如下所示：

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)

