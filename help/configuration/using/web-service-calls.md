---
title: Web服务调用
seo-title: Web服务调用
description: Web服务调用
seo-description: null
page-status-flag: never-activated
uuid: 7defe0e4-bb4a-4f6a-b6e8-e2ffac73b4c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 6934c165-6d27-4ce5-8607-170f299b4702
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c51a51f175e9f3fe5a55f2b5f57872057f70909d
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Web服务调用{#web-service-calls}

## 一般信息 {#general-information}

所有API方法都以Web服务的形式呈现。 这使您能够通过SOAP调用管理所有Adobe Campaign函数，SOAP调用是Adobe Campaign应用服务器的本机入口点。 Adobe Campaign控制台本身仅使用SOAP调用。

Web服务允许您从第三方系统创建许多应用程序：

* 从后台或交易系统同步警报、通知和实时投放模板执行，
* 开发具有简化功能的特殊界面（Web界面等）,
* 在遵守贸易规则并与基础物理模型保持隔离的同时，在数据库中供给和查找数据。

## Web服务的定义 {#definition-of-web-services}

在Adobe Campaign应用服务器上实现的Web服务的定义可从数据模式获得。

在数据模式的语法中描述Web服务，并从元素中可 **`<methods>`** 用。

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

这里我们有一个名为GenerateForm的方法定义 **的示例**。

服务开始与元素的说 `<method>` 明。 该方法的参数列表从元素中完 `<parameters>` 成。 每个参数都由名称、类型（布尔、字符串、DOMElement等）指定 和描述。 带有“out”值的“inout”属性允许您指定“result”参数在SOAP调用输出处。

存在“static”属性（值为“true”）将此方法描述为静态，这意味着必须声明该方法的所有参数。

“const”方法隐式地将XML文档格式的相关模式作为其输入。

有关Adobe Campaign模式 `<method>` 模式元素的完整说明，请参阅  <a href="../../configuration/using/elements-and-attributes.md#method--element" target="_blank">  `<method>`    元素。

“xtk:queryDef”模式中“const”类型的“ExecuteQuery”方法的示例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的输入参数是格式为“xtk:queryDef”文档的XML模式。

## Web服务描述： WSDL {#web-service-description--wsdl}

每个服务都有一个WSDL（Web服务描述库）文件。 此XML文件使用元语言描述服务，并指定可用的方法、参数和与服务器联系以执行服务。

### WSDL文件生成 {#wsdl-file-generation}

要生成WSDL文件，必须从Web浏览器输入以下URL:

[https://`<server>`/nl/jsp/schemawsdl.jsp?模式=`<schema>`

具有：

* **`<server>`**: Adobe Campaign应用程序服务器(nlserver web)
* **`<schema>`**: 模式标识密钥(命名空间:模式名)

### 模式“xtk:queryDef”的“ExecuteQuery”方法示例 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL文件是从URL生成的：

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

WSDL描述开始，通过定义用于形成消息的类型（与“端口”关联），通过“绑定”与协议连接，形成Web服务。

#### 类型 {#types}

类型定义基于XML模式。 在我们的示例中，“ExecuteQuery”方法采用“s:string”字符串和XML文档(`<s:complextype>`)作为参数。 方法的返回值(“ExecuteQueryResponse”)是XML文档( `<s:complextype>`)。

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### 消息 {#messages}

介 `<message>` 绍要发送的一组字段的名称和类型。 该方法使用两条消息作为参数(“ExecuteQueryIn”)和返回值(“ExecuteQueryOut”)传递。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### 端口类型 {#porttype}

将 `<porttype>` 消息关联到由生成响应的查询（“输入”）触发的“ExecuteQuery”操作。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 绑定 {#binding}

该 `<binding>` 部分指定SOAP通信协议( `<soap:binding>` )、HTTP中的数据传输（“transport”属性的值）和“ExecuteQuery”操作的数据格式。 SOAP封套的正文直接包含消息段，无需转换。

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### 服务 {#service}

本 `<service>` 部分描述“XtkQueryDef”服务，其URI位于Adobe Campaign应用程序服务器的URL上。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 连接性 {#connectivity}

Adobe Campaign通过引入安全区(请参阅本节的“定 **义安全区** ”一章) [和会话管理设置](../../installation/using/configuring-campaign-server.md#defining-security-zones)，提高了身份验证机制的安全性。

有两种可用的身份验证模式：

* **通过调用登录方法()**。 此模式生成会话令牌和安全令牌。 它是最安全的模式，因此也是最推荐的模式。

或

* **通过Adobe Campaign登录名** +密码创建会话令牌。 会话令牌会在设置的时间段后自动过期。 不建议使用此模式，并要求为某些区域设置（allowUserPassword=&quot;true&quot;和sessionTokenOnly=&quot;true&quot;）减少应用程序安全设置。

### 会话令牌特性 {#session-token-characteristics}

会话令牌具有以下特性：

* a X小时生命周期（生命周期可在“serverConf.xml”文件中配置，默认周期为24小时）
* 随机构造（不再包含用户登录名和口令）
* 当通过Web访问时：

   * 会话令牌成为永久令牌，一旦浏览器关闭，它不会被销毁
   * 它位于仅HTTP的Cookie中（必须为操作符激活Cookie）

### 安全令牌特性 {#security-token-characteristics}

安全令牌具有以下特征：

* 它是从会话令牌生成的
* 它有一个24小时的生命周期（可在“serverConf.xml”文件中配置，默认周期为24小时）
* 它存储在Adobe Campaign控制台中
* 当通过Web访问时：

   * 它存储在文档中。__securityToken属性
   * 页面URL将更新安全令牌
   * 表单也通过包含令牌的隐藏字段进行更新

#### 安全令牌移动 {#security-token-movement}

通过控制台访问时，它为：

* 在登录响应中传输（在HTTP头中）
* 用于每个查询（在HTTP头中）

从POST和GET HTTP:

* 服务器用令牌完成链接
* 服务器向表单添加隐藏字段

从SOAP调用：

* 添加到呼叫头

### 调用示例 {#call-examples}

* 使用 **HttpSoapConnection/SoapService**:

   ```
     var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
   var session = new SoapService(cnx, 'urn:xtk:session');
   session.addMethod("Logon", "xtk:session#Logon",
                       ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                       ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
   
   var res = session.Logon("", "admin", "pwd", <param/>);
   var sessionToken = res[0];
   var securityToken = res[2];
   
   cnx.addTokens(sessionToken, securityToken);
   var query = new SoapService(cnx, 'urn:xtk:queryDef');
   query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                       ["sessiontoken", "string", "entity", "NLElement"],
                       ["res", "NLElement"]);
   
   var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@email = 'joe.doe@aol.com'"/>
             </where>
           </queryDef>);
   logInfo(queryRes[0].toXMLString())
   ```

* 使用 **HttpServletRequest**:

>[!NOTE]
>
>以下HttpServletRequest调 **用中使用的** URL必须位于serverConf.xml文件的url权限部分的 **允许列表中** 。 服务器本身的URL也是如此。

登录执行():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
  '<soapenv:Header/>' +
  '<soapenv:Body>' +
      '<urn:Logon>' +
          '<urn:sessiontoken></urn:sessiontoken>' +
          '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
          '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
          '<urn:elemParameters></urn:elemParameters>' +
      '</urn:Logon>' +
  '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
         
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

查询执行：

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
           '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
              '<queryDef operation="select" schema="nms:recipient">' +
                '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
              '</queryDef>' +
         '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```

