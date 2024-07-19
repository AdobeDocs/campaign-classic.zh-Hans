---
product: campaign
title: 发送生日电子邮件
description: 了解如何使用工作流发送生日电子邮件
feature: Workflows
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 2%

---

# 发送生日电子邮件{#sending-a-birthday-email}



## 简介 {#introduction}

此用例介绍了如何计划在收件人生日当天向其列表发送定期电子邮件。

为了设置此用例，我们创建了以下定位工作流：

![](assets/birthday-workflow_usecase_1.png)

此（每日运行）工作流会选择其生日为当前日期的所有收件人。

![](assets/do-not-localize/how-to-video.png)此用例也可以以视频形式找到。 有关详细信息，请参阅[创建工作流](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html)视频。

为此，请创建一个营销活动，然后单击&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡。 有关更多信息，请参阅[在工作流中生成主目标](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)部分。

然后按照以下步骤操作：

## 计划发送 {#configuring-the-scheduler}

1. 首先，添加&#x200B;**调度程序**&#x200B;以触发每天发送投放。 在下面的示例中，每天早上6:00创建投放。

   ![](assets/recur_delivery2.png)


## 识别其生日为的收件人 {#identifying-recipients-whose-birthday-it-is}

在配置&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动以便工作流每天开始后，识别其出生日期等于当前日期的所有收件人。

要执行此操作，请应用以下步骤：

1. 将&#x200B;**[!UICONTROL Query]**&#x200B;活动拖放到工作流中并双击该活动。
1. 单击&#x200B;**编辑查询**&#x200B;链接并选择&#x200B;**[!UICONTROL Filtering conditions]**。

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. 单击&#x200B;**[!UICONTROL Expression]**&#x200B;列的第一个单元格并单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;打开表达式编辑器。

   ![](assets/s_ncs_user_create_exp_exple.png)

1. 单击&#x200B;**[!UICONTROL Advanced selection]**&#x200B;以选择筛选模式。

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. 选择&#x200B;**[!UICONTROL Edit the formula using an expression]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**&#x200B;以显示表达式编辑器。
1. 在函数列表中，双击&#x200B;**[!UICONTROL Day]**，可通过&#x200B;**[!UICONTROL Date]**&#x200B;节点访问它。 此函数返回数字，该数字表示与作为参数传递的日期对应的日期。

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. 在可用字段列表中，双击&#x200B;**[!UICONTROL Birth date]**。 然后，该编辑器的上半部分会显示以下公式：

   ```
   Day(@birthDate)
   ```

   单击 **[!UICONTROL Finish]** 确认。

1. 在查询编辑器中，在&#x200B;**[!UICONTROL Operator]**&#x200B;列的第一个单元格中选择&#x200B;**[!UICONTROL equal to]**。

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. 接下来，单击第二列(**[!UICONTROL Value]**)的第一个单元格，然后单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;以打开表达式编辑器。
1. 在函数列表中，双击&#x200B;**[!UICONTROL Day]**，可通过&#x200B;**[!UICONTROL Date]**&#x200B;节点访问它。
1. 双击&#x200B;**[!UICONTROL GetDate]**&#x200B;函数以检索当前日期。

   ![](assets/s_ncs_user_create_exp_exple04.png)

   该编辑器的上半部分显示以下公式：

   ```
   Day(GetDate())
   ```

   单击 **[!UICONTROL Finish]** 确认。

1. 重复此过程以检索对应于当前月份的出生月份。 为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并重复步骤3至10，将&#x200B;**[!UICONTROL Day]**&#x200B;替换为&#x200B;**[!UICONTROL Month]**。

   完整的查询如下所示：

   ![](assets/s_ncs_user_create_exp_exple03.png)

将&#x200B;**[!UICONTROL Query]**&#x200B;活动的结果链接到&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动，以向生日当天您的所有收件人的列表发送电子邮件。

## 包括2月29日出生的收件人（可选） {#including-recipients-born-on-february-29th--optional-}

如果您希望包含所有在2月29日出生的收件人，则此用例将介绍如何计划向生日收件人的列表发送定期电子邮件 — 无论是否为闰年。

此用例的主要实施步骤包括：

* 选择收件人
* 选择是否为闰年
* 选择2月29日出生的任何收件人

为了设置此用例，我们创建了以下定位工作流：



如果当前年份&#x200B;**不是闰年**，并且工作流在3月1日运行，我们需要选择昨天（2月29日）生日的所有收件人，并将他们添加到收件人列表中。 在任何其他情况下，均无需执行其他操作。

### 步骤1：选择收件人 {#step-1--selecting-the-recipients}

在配置&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动以便工作流每天启动后，识别其周年是当天的所有收件人。

>[!NOTE]
>
>如果当前年份是闰年，则所有在2月29日出生的收件人都会自动包含在内。

![](assets/birthday-workflow_usecase_2.png)

选择其生日对应于当前日期的收件人将显示在[确定其生日是](#identifying-recipients-whose-birthday-it-is)部分的收件人中。

### 步骤2：选择是否为闰年 {#step-2--select-whether-or-not-it-is-a-leap-year}

**[!UICONTROL Test]**&#x200B;活动允许您检查是否为闰年，以及当前日期是否为3月1日。

如果测试得到验证（该年不是闰年 — 没有2月29日 — 并且当前日期确实是3月1日），则启用&#x200B;**[!UICONTROL True]**&#x200B;过渡，并将在2月29日出生的收件人添加到3月1日投放。 否则，将启用&#x200B;**[!UICONTROL False]**&#x200B;过渡，并且只有生于当前日期的收件人才会收到投放。

将下面的代码复制并粘贴到&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡的&#x200B;**[!UICONTROL Initialization script]**&#x200B;部分中。

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

在&#x200B;**[!UICONTROL Conditional forks]**&#x200B;部分中添加以下条件：

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### 步骤3：选择2月29日出生的任何收件人 {#step-3--select-any-recipients-born-on-february-29th}

创建&#x200B;**[!UICONTROL Fork]**&#x200B;活动并将其中一个叫客过渡链接到&#x200B;**[!UICONTROL Query]**&#x200B;活动。

在此查询中，选择出生日期为2月29日的所有收件人。

![](assets/birthday-workflow_usecase_5.png)

将结果与&#x200B;**[!UICONTROL Union]**&#x200B;活动合并。

将两个&#x200B;**[!UICONTROL Test]**&#x200B;活动分支的结果链接到&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动，以向生日当天的所有收件人的列表发送电子邮件，甚至向在非闰年2月29日出生的人发送电子邮件。

## 创建循环投放 {#creating-a-recurring-delivery-in-a-targeting-workflow}

基于要发送的生日电子邮件模板添加&#x200B;**定期投放**&#x200B;活动。

>[!CAUTION]
>
>对于要执行的工作流，必须启动与Campaign包相关的技术工作流。 有关详细信息，请参阅[技术工作流列表](about-technical-workflows.md)部分。
>
>如果为营销活动启用了批准步骤，则仅在确认了这些步骤后才会发送投放。 有关详细信息，请参阅[选择要批准的进程](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved)部分。

![](assets/birthday-workflow_usecase_1.png)
