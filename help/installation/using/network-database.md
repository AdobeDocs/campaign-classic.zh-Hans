---
product: campaign
title: 网络、数据库和 SSL/TLS
description: 进一步了解网络、数据库和SSL/TLS配置最佳实践。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 9%

---

# 网络、数据库和 SSL/TLS {#network-database}

![](../../assets/v7-only.svg)

## 网络配置

部署内部部署类型的架构时，需要检查的一个非常重要的事项是 [网络配置](../../installation/using/network-configuration.md). 确保Tomcat服务器不能直接在服务器外部访问：

* 在外部IP上关闭Tomcat端口(8080)（必须在本地主机上工作）
* 请勿将标准HTTP端口(80)映射到Tomcat端口(8080)

如果可能，请使用安全渠道：POP3改为POP3（或POP3而不是TLS）。

## 数据库

必须应用数据库引擎安全最佳实践。

## SSL/TLS配置

要检查证书，您可以使用openssl。 要检查活动密码，您可以使用nmap:

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

您还可以使用 [sslyze](https://github.com/nabla-c0d3/sslyze/releases) python脚本，可同时执行这两项操作。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
