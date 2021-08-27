---
product: campaign
title: JSP 行为
description: JSP 行为
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP 行为{#jsp-behavior}

![](../../assets/v7-only.svg)

如果某些&#x200B;**jsp**&#x200B;作业未成功执行，则必须强制它们重新编译。

为此，请输入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

下次连接时，将重新生成&#x200B;**jsp**&#x200B;作业。
