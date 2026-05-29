---
product: campaign
title: 其他配置
description: 配置
feature: Monitoring, Configuration
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: efa38731-2723-4334-8d8b-a778af834835id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 11%

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
