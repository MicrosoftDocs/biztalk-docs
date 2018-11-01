---
title: Batch Schedule Page
TOCTitle: Batch Schedule Page
ms:assetid: 370b8792-3578-4df6-9f63-6d9defc3f850
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dd224416(v=BTS.80)
ms:contentKeyID: 51527347
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.ediagreement.batchschedule
- bts10.edir2.EDI.party.batches.scheduler
---

# Batch Schedule Page

 

This topic describes the fields in the **Batch Schedule** page of the **EDI Properties** dialog box. This page is displayed by right-clicking a party in the **Parties** node of the BizTalk Server Administration Console, clicking **EDI Properties**, clicking **Batches**, and then clicking **Scheduler** in the **Batches** page.


> [!NOTE]
> <P>A batch schedule may be affected by special events. An example is the onset of daylight savings time. If a batch were scheduled on an hourly basis less than an hour after the onset of daylight savings time, the batch would not be created and sent after clocks were reset by incrementing the hour. You can compensate for a special event that results in a skipped batch by clicking the <STRONG>Start</STRONG> button on the <STRONG>Batches</STRONG> page to start the batching orchestration manually. You may also have to stop a duplicated batch.</P>



## Batch Schedule

**Hourly**  
Select to send a batch on an hourly basis, with the exact interval (the hours or minutes after the time of the first release) established by the time entered in the **First release at** field.

For the **Subsequent release every** field, select **Hour(s)** or **Minute(s)** from the drop-down list.

**Daily**  
Select to send a batch on a daily basis, at the time listed in the **First release at** field, with the exact day established by the number of days entered in the **Subsequent release every** field.

**Weekly**  
Select to send a batch on a weekly basis, at the time listed in the **First release at** field, with the interval of weeks established by the value in the **Subsequent release every** field, and the days of the week established by which days are selected beneath the **Subsequent release every** field.

The first release will be made at the date and set in the **First release at** field, even if that day of the week was not selected in the dialog box.

If you have selected one or more days of the week in the dialog box, a release will be made on any selected day of that first week that comes after the first release. For example, if Monday and Friday have been selected, and the first release was on a Wednesday, a release will be made on Friday of the first week.

Subsequent releases will occur *n* weeks after the first week, with *n* determined by the value in the **Subsequent release every** field. Release will occur on each day of the week selected in the dialog box.

**First release at**  
Select a date and time for the first release of the batch. Select a date from the calendar, and enter the time.

**Subsequent release every**  
Enter a number establishing the period of time after the first release of the batch.

If you selected **Hourly**, select either Hour(s) or Minute(s) for the units, and then enter the number of hours or minutes between the first release and each subsequent release.

If you selected **Daily**, enter the number of days between the first release and each subsequent release.

If you selected **Weekly**, enter the number of weekly between the week of the first release and the week of each subsequent release. Then select the days of the week that the batch will be released on.

**Send empty batch signal**  
Select to send an empty batch signal if no messages have been received by the batching orchestration when the batch is scheduled to be sent.

