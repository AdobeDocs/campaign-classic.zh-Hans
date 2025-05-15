---
product: campaign
title: 新的基于GCM的函数
description: 新的基于GCM的函数
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# 基于 GCM 的函数 {#new-functions}

为了提高安全性，我们不再将AES（高级加密标准）算法与CBC（密码块链接）模式一起用于加密操作。 引入了新的加密函数。 这些函数将AES与Galois/Counter Mode (AES-GCM)一起使用，从而提供了更安全的替代方案。 这些函数在JavaScript、JSP、SOAP API和XML架构中可用，允许客户从CBC过渡到GCM进行加密和解密。

本文档列出了新引入的AES-GCM函数以及已弃用的基于CBC的函数。

新函数：

* [EncryptString API函数](#encryptString-api-xtk)
* [EncryptStringWithServerPassword API函数](#EncryptStringWithServerPassword-api-xtk)
* [encryptString javascript函数](#encryptString-javascript)

可用于GCM的旧版函数：

* [DecryptString javascript函数](#decryptString-javascript)
* [DecryptPassword javascript函数](#decryptPassword-javascript)

[已弃用的函数](#depracated-functions)

## API函数

### 加密字符串 {#encryptString-api-xtk}

在GCM模式下使用AES算法使用实例密钥加密字符串。

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**参数**：解密的文本

**返回值**：已加密

**架构**： xtk：session

**静态**：是

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

在GCM模式下使用AES算法使用服务器密钥加密字符串。


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**参数**：已解密

**返回值**：已加密

**架构**： xtk：session

**静态**：是

## Javascript函数

### encryptString() {#encryptString-javascript}

使用实例的键或任何其他键加密字符串。

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**参数**：

* str：要加密的字符串。
* 密钥：如果密钥长度为32，则AES加密密钥以base 64:256位编码；如果密钥长度为24，则为192位；如果密钥长度为16或未指定密钥，则为128位。
* useSalt：使用数据的加密盐进行加密。 默认情况下为True。

**返回值**：返回加密的字符串。

**备注**

加密按照以下方法进行：

* unicode字符串将转换为UTF-8字符串。
* 在密码文本末尾添加一个校验字符。
* 此字符串在galois/计数器模式(GCM)下使用AES算法加密，使用salt和12字节初始化向量和16字节标记。 如果未提供键作为参数，则使用实例键。
* 密文将包含标记和初始化矢量。
* 然后将加密块转换为基数64。

使用decryptString函数执行解密。

**功能**

可用位置：

* 内容管理 
* 投放属性
* 投放消息
* 类型规则
* 导入
* JSSP
* SOAP方法
* WebApp
* 工作流

### decryptString() {#decryptString-javascript}

使用实例的键或任何其他键对字符串进行解密。 此旧版函数可与GCM一起使用。 对于使用AES-CBC模式加密的密文解密，它已被弃用。

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**参数**：

* str：要解密的字符串。
* 密钥：如果密钥长度为32，则AES加密密钥以base 64:256位编码；如果密钥长度为24，则为192位；如果密钥长度为16或未指定密钥，则为128位。
* useSalt：使用数据的盐进行解密。 默认情况下为True。

**返回值**：返回解密的字符串。

**警告**：使用此方法无法再解密数据库中存储的密码（选项/外部帐户）。 为此，请使用[decryptPassword](#decryptPassword-javascript)。

### decryptPassword() {#decryptPassword-javascript}

解密存储在外部帐户中的密码。 此旧版函数可与GCM一起使用。 对于使用AES-CBC模式加密的密文解密，它已被弃用。

```
            decryptPassword (str)
         
```

**参数**：

* str：要解密的字符串。

**返回值**：返回纯文本密码。

**备注**

无法在工作流、Web应用程序、报表或投放中调用此函数。 可以在JSSP或SOAP调用实现中调用它。 示例：

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## 已弃用的函数 {#depracated-functions}

以下函数已完全弃用：

* cryptString
* 加密
* EncryptServerPassword
