---
product: campaign
title: 其他配置
description: 配置
feature: Monitoring, Configuration
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 1%

---

# 配置{#configuration}



## 更改syslogd侦听端口 {#changing-the-syslogd-listening-port}

默认情况下，**syslogd**&#x200B;侦听端口为666 (udp)。 您可以根据需要使用环境变量对其进行更改。

配置此变量后，所有Adobe Campaign模块都会考虑该变量。

### 在Linux中 {#in-linux}

编辑&#x200B;**customer.sh**&#x200B;文件并添加以下行：

```sql
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您需要创建具有&#x200B;**localhost**&#x200B;值&#x200B;**`<listening port="" />`**&#x200B;的&#x200B;**TRACE_ADDR**&#x200B;环境变量。

>[!IMPORTANT]
>
>我们建议您在创建此环境变量后，运行一些测试以确保您的平台可以正常工作。

## 配置安全区域 {#configuring-security-zones}

每个运算符都需要链接到区域才能登录到实例，并且运算符IP必须包含在安全区域中定义的地址或地址集中。 技术区域配置在Adobe Campaign服务器的配置文件中执行。 必须在控制台（**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点）中定义运算符到安全区域的链接。

>[!NOTE]
>
>有关配置安全区域的详细信息，请参阅[本节](../../installation/using/security-zones.md)。
