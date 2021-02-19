---
solution: Campaign Classic
product: campaign
title: JSP 行为
description: JSP 行为
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# JSP 行为{#jsp-behavior}

如果某些&#x200B;**jsp**&#x200B;作业未成功执行，则必须强制它们重新编译。

对于此，输入以下命令：

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

下次连接时将重新生成&#x200B;**jsp**&#x200B;作业。
