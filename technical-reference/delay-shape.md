---
description: "Learn more about: Delay Shape"
title: Delay Shape
TOCTitle: Delay Shape
ms:assetid: b29c5dbf-2f8b-4e26-bc1a-4f93a139846d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578173(v=BTS.80)
ms:contentKeyID: 51530583
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.delay
---

# Delay Shape

 

The **Delay** shape enables you to control the timing of the progress of your orchestration. You can set a time-out on the **Delay** shape so that your orchestration pauses before resuming execution. You specify the time-out by using **System.DateTime**, which causes your orchestration to pause until the specified date or time is reached, or by using **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.

For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in Microsoft Visual Studio Help.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Delay</strong> property</td>
<td>Specify a time-out using <strong>System.DateTime</strong> or <strong>System.TimeSpan</strong> in order to create a corresponding delay in your orchestration. For example, if you specify <strong>System.DateTime.UtcNow.AddSeconds (60)</strong>, your orchestration will be idle for sixty seconds before proceeding.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Delay Shape](https://msdn.microsoft.com/library/aa560800\(v=bts.80\))

