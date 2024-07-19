---
product: campaign
title: JSP 行为
description: JSP 行为
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 14%

---

# JSP 行为{#jsp-behavior}



如果某些&#x200B;**jsp**&#x200B;作业未成功执行，则必须强制重新编译这些作业。

为此，请输入以下命令：

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

下次连接时将重新生成&#x200B;**jsp**&#x200B;作业。
