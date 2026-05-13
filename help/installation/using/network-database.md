---
product: campaign
title: 网络、数据库和 SSL/TLS
description: 了解有关网络、数据库和SSL/TLS配置最佳实践的更多信息
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
TQID: https://experienceleague.adobe.com/PLGVcm4QYeU0A1uEhlDEfweZ275xpxtxo91r4aidr1I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 138
ht-degree: 9%

---

# 网络、数据库和 SSL/TLS {#network-database}

## 网络配置

部署内部部署类型的架构时要检查的非常重要的事项是[网络配置](../../installation/using/network-configuration.md)。 确保Tomcat服务器无法在服务器外部直接访问：

* 关闭外部IP上的Tomcat端口(8080)（必须在本地主机上工作）
* 请勿将标准HTTP端口(80)映射到Tomcat端口(8080)

如果可能，请使用安全渠道：改用POP3S而不是POP3（或通过TLS的POP3）。

## 数据库

您必须应用数据库引擎安全最佳实践。

## SSL/TLS配置

要检查证书，您可以使用openssl。 要检查活动密码，您可以使用nmap：

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

您也可以使用同时执行这两项操作的[sslyze](https://github.com/nabla-c0d3/sslyze/releases) python脚本。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
