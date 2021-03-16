---
solution: Campaign Classic
product: campaign
title: 网络、数据库和SSL/TLS
description: 了解有关网络、数据库和SSL/TLS配置最佳实践的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 63b2e6b95812f1649e636580984a1f0dcc9c5c53
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---


# 网络、数据库和SSL/TLS {#network-database}

## 网络配置

部署内部部署类型的架构时需要检查的一件非常重要的事情是[网络配置](../../installation/using/network-configuration.md)。 确保Tomcat服务器不能直接在服务器外部访问：

* 在外部IP上关闭Tomcat端口(8080)（必须在localhost上工作）
* 不要将标准HTTP端口(80)映射到Tomcat 1(8080)

如果可能，请使用安全渠道:POP3S改为POP3（或POP3 over TLS）。

## 数据库

您必须应用数据库引擎安全最佳实践。

## SSL/TLS配置

要检查证书，可使用openssl。 要检查活动密码，您可以使用nmap:

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

您还可以使用[sslyze](https://github.com/nabla-c0d3/sslyze/releases) python脚本，该脚本兼有这两个功能。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
