---
title: JSP 行为
seo-title: JSP 行为
description: JSP 行为
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '38'
ht-degree: 21%

---


# JSP 行为{#jsp-behavior}

如果某 **些jsp** 作业未成功执行，则必须强制它们重新编译。

对于此，输入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

下次 **连接** 时，将重新生成jsp作业。
