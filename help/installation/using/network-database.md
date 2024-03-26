---
product: campaign
title: 网络、数据库和 SSL/TLS
description: 了解有关网络、数据库和SSL/TLS配置最佳实践的更多信息
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 14%

---

# 网络、数据库和 SSL/TLS {#network-database}



## 网络配置

在部署内部部署类型的体系结构时，需要检查的一件非常重要的事情是 [网络配置](../../installation/using/network-configuration.md). 确保Tomcat服务器无法在服务器外部直接访问：

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

您也可以使用 [slyze](https://github.com/nabla-c0d3/sslyze/releases) python脚本，两者都有。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
