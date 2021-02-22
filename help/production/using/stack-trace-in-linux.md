---
solution: Campaign Classic
product: campaign
title: Linux 中的堆栈跟踪
description: Linux 中的堆栈跟踪
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---


# Linux 中的堆栈跟踪{#stack-trace-in-linux}

**堆栈跟踪**&#x200B;表示包含在&#x200B;**核心**&#x200B;类型文件中的跟踪。 此文件在计算机错误事件中生成。 它可以识别错误的来源。

>[!NOTE]
>
>* **core**&#x200B;文件名为&#x200B;**core.`<num>`**。
>* **gdb — 必须在** 计算机上安装GNU调试程序。
>



Adobe Campaign技术支持可以要求您提供此&#x200B;**堆栈跟踪**。 要获取它，请在Linux中输入以下命令：

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

Adobe Campaign技术支持可能会要求您使用特定的可执行文件（由我们提供）运行此命令。

在这种情况下，只需使用Adobe Campaign提供的可执行文件替换&#x200B;**nlserver**&#x200B;来运行以下命令：

```
gdb nlserver <coreFile>
```

例如：

```
gdb nlserver.1823 <coreFile>
```

