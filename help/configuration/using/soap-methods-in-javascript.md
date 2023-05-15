---
product: campaign
title: JavaScript 中的 SOAP 方法
description: JavaScript 中的 SOAP 方法
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# JavaScript 中的 SOAP 方法{#soap-methods-in-javascript}

这是在Adobe Campaign服务器上执行的JavaScript。

## 静态方法 {#static-methods}

通过在表示架构的对象上调用方法来访问静态SOAP方法。 架构是“namespace”对象的属性。 这些命名空间是全局变量，因此，例如xtk或nms变量表示相应的命名空间

以下示例调用xtk：工作流架构的静态PostEvent方法：

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## 非静态方法 {#non-static-methods}

要使用非静态SOAP方法，必须首先在相应的架构中使用“get”或“create”方法检索实体。

以下示例调用“xtk:queryDef”架构的ExecuteQuery方法：

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## 示例 {#examples}

* 使用“get”操作查询收件人表：

   ```
   var query = xtk.queryDef.create(  
     <queryDef schema="nms:recipient" operation="get">    
       <select>      
         <node expr="@firstName"/>      
         <node expr="@lastName"/>      
         <node expr="@email"/>    
       </select>    
       <where>      
         <condition expr="@email = 'peter.martinez@adobe.com'"/>    
       </where>  
     </queryDef>)
   
   var recipient = query.ExecuteQuery()
   
   logInfo(recipient.@firstName)
   logInfo(recipient.@lastName)
   ```

* 使用“select”操作查询收件人表：

   ```
   var query = xtk.queryDef.create(  
     <queryDef schema="nms:recipient" operation="select">    
       <select>      
         <node expr="@email"/>      
         <node expr="@lastName"/>      
         <node expr="@firstName"/>    
       </select>    
       <where>      
         <condition expr="@age > 25"/>    
       </where>    
     </queryDef>)
   
   var res = query.ExecuteQuery()
   
   for each (var recipient in res.recipient) 
   {  
     logInfo(recipient.@email)  
     logInfo(recipient.@firstName)  
     logInfo(recipient.@lastName)
   }
   ```

* 将数据写入收件人表：

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```
