---
title: 通过 JavaScript 集成（客户端）
seo-title: 通过 JavaScript 集成（客户端）
description: 通过 JavaScript 集成（客户端）
seo-description: null
page-status-flag: never-activated
uuid: 19cafecd-cf13-458a-857e-0a45c346f4ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 7453d768-31eb-4372-aae3-27527cd5c79b
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 2%

---


# 通过 JavaScript 集成（客户端）{#integration-via-javascript-client-side}

要在网页中调用交互引擎，请将对JavaScript代码的调用直接插入该页面。 此调用返回目标位置中的优惠内容

元素。

Adobe建议使用JavaScript集成方法。

调用URL的脚本如下所示：

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

“env ****”参数接收专用于匿名交互的实时环境的内部名称。

要演示优惠，我们需要创建Adobe Campaign和优惠空间，然后配置HTML页。

以下用例详细说明了通过JavaScript集成优惠的可能选项。

## HTML模式 {#html-mode}

### 呈现匿名优惠 {#presenting-an-anonymous-offer}

1. **准备交互引擎**

   打开Adobe Campaign界面并准备匿名环境。

   创建链接到匿名优惠空间的环境。

   创建优惠及其与优惠空间链接的表示形式。

1. **HTML页面的内容**

   HTML页面必须包含

   具有@id属性的元素，其值为已创建优惠空间的内部名称(“i_internal name space”)。 优惠将通过“交互”插入到此元素中。

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
   >标 `<script>` 签不能自行关闭。

   此静态调用将自动生成包含交互引擎所需的所有参数的动态调用。

   此行为允许您在同一页面上使用多个优惠空间，通过对引擎的一次调用进行管理。

1. **HTML页中的结果**

   优惠呈现的内容由交互引擎返回到HTML页面：

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

### 呈现已识别的优惠 {#presenting-an-identified-offer}

要向已识别的联系人提供优惠，该过程与此处详述的过程类似： [呈现匿名优惠](#presenting-an-anonymous-offer)。 在网页内容中，您需要添加以下脚本，以在调用引擎时识别联系人：

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. 转至网页将调用的优惠空间，单击并添 **[!UICONTROL Advanced parameters]** 加一个或多个标识键。

   ![](assets/interaction_htmlmode_001.png)

   在此示例中，标识密钥是组合的，因为它既基于电子邮件，也基于收件人名。

1. 在网页显示过程中，脚本评估允许您将收件人ID传递给优惠引擎。 如果ID是复合的，则按与高级设置中相同的顺序显示键，并由 |。

   在以下示例中，联系人已登录到网站，在调用交互引擎时，由于其电子邮件和姓名而被识别。

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### 使用HTML渲染功能 {#using-an-html-rendering-function}

要自动生成HTML优惠呈现，您可以使用渲染函数。

1. 转到优惠空间并单击链 **[!UICONTROL Edit functions]** 接。
1. 选择 **[!UICONTROL Overload the HTML rendering function]**。
1. 转到选项 **[!UICONTROL HTML rendering]** 卡，并插入与为优惠内容定义的字段相匹配的变量。

   ![](assets/interaction_htmlmode_002.png)

   在此示例中，优惠以网页中横幅的形式显示，由可单击的图像和与优惠内容中定义的字段相匹配的标题组成。

## XML模式 {#xml-mode}

### 展示优惠 {#presenting-an-offer}

交互允许您将XML节点返回到调用优惠引擎的HTML页。 此XML节点可由客户端开发的函数进行处理。

对交互引擎的调用如下所示：

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

“env ****”参数接收实时环境的内部名称。

“cb ****”参数接收将读取引擎返回的包含（回调）命题的XML节点的函数名称。 此参数是可选的。

“t ****”参数接收目标值，仅用于标识的交互。 此参数也可以与interactionTarget变 **量一起** 传递。 此参数是可选的。

“**c**”参数接收类别的内部名称的列表。 此参数是可选的。

“th ****”参数接收主题。 此参数是可选的。

“gctx ****”参数接收整个页面的全局调用数据（上下文）。 此参数是可选的。

返回的XML节点如下所示：

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

以下用例详细介绍了在Adobe Campaign下进行的配置以启用XML模式，然后在HTML页中显示对引擎的调用结果。

1. **创建环境和优惠空间**

   有关创建环境的详细信息，请参 [阅实时／设计环境](../../interaction/using/live-design-environments.md)。

   有关创建优惠空间的详细信息，请参阅 [创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

1. **扩展优惠模式以添加新字段**

   此模式将定义以下字段：标题2和价格。

   示例中模式的名称为 **cus:优惠**

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
   >每个元素需要定义两次。 CDATA(&quot;_jst&quot;)类型元素可包含个性化字段。
   >
   >不要忘记更新数据库结构。 如需详细信息，请参阅[此部分](../../configuration/using/updating-the-database-structure.md)。

   >[!NOTE]
   >
   >您可以扩展优惠模式，以批处理和统一模式以及任何格式（文本、HTML和XML）添加新字段。

1. **扩展优惠公式以编辑新字段和修改现有字段**

   编辑 **优惠(nsm)** 输入表单。

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
   >()表单的字 `<input>`段必须指向在创建的模式中定义的CDATA类型元素。

   优惠呈现表单中的呈现如下所示：

   ![](assets/interaction_xmlmode_form.png)

   已 **[!UICONTROL Title 2]** 添加 **[!UICONTROL Price]** 和字段，且不再 **[!UICONTROL Destination URL]** 显示该字段。

1. **创建优惠**

   有关创建优惠的详细信息，请 [参阅创建优惠](../../interaction/using/creating-an-offer.md)。

   在以下用例中，优惠按如下方式输入：

   ![](assets/interaction_xmlmode_offer.png)

1. 批准优惠或让其他人批准，然后在上一步创建的优惠空间上激活它，以便在链接的实时环境中提供它。
1. **HTML页上的引擎调用和结果**

   在HTML页面中调用交互引擎的情况如下：

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   “env ****”参数的值是实时环境的内部名称。

   “cb ****”参数的值是需要解释引擎返回的XML节点的函数名称。 在我们的示例中，调用的函数打开一个模态窗口(alert()函数)。

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

### 使用渲染函数 {#using-a-rendering-function-}

可以使用XML渲染功能创建优惠演示文稿。 此函数将修改在调用引擎期间返回到HTML页面的XML节点。

1. 转到优惠空间并单击链 **[!UICONTROL Edit functions]** 接。
1. 选择 **[!UICONTROL Overload the XML rendering function]**。
1. 转到选项卡 **[!UICONTROL XML rendering]** 并插入所需的函数。

   该函数可以如下所示：

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)

