---
title: Batch Filter Page
TOCTitle: Batch Filter Page
ms:assetid: 6739943b-b5e1-412d-b8c3-a18e0f9fb586
ms:mtpsurl: https://msdn.microsoft.com/library/Dd257229(v=BTS.80)
ms:contentKeyID: 51528613
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.ediagreement.batchfilter
- bts10.edir2.EDI.party.batches.filter
---

# Batch Filter Page

 

This topic describes the fields in the **Batch Filter** page of the **EDI Properties** dialog box. This page is displayed by right-clicking a party in the **Parties** node of the BizTalk Server Administration Console, clicking **EDI Properties**, clicking **Batches**, and then clicking **Filter** in the **Batches** page.

In this page, you create a set of filter criteria for determining which messages will be picked up by the batching orchestration and included in the batch.


> [!NOTE]
> <P>When making changes to the batch filter, it will take 15 minutes for the new filter settings to take effect. This refresh time cannot be changed.</P>



## Batch Filter

**Property**  
Select a property to include in the batch filter expression. Only those messages that have this property set to the value entered in the filter expression will be included in the batch.

**Operator**  
Select the operator to be used in the line in the filter expression.

**Value**  
Enter the value to be correlated with the properly by the operator.

**Group by**  
Enter the logical relationship between the first line of the filter expression and the next line of the filter expression, either **And** or **Or**.

**Delete**  
After selecting a row by clicking in the leftmost column of that row, click **Delete** to remove the line from the filter expression.

**Move Up**  
After selecting a row by clicking in the leftmost column of that row, click **Move Up** to move the line to the position before the previous line in the filter expression.

**Move Down**  
After selecting a row by clicking in the leftmost column of that row, click **Move Down** to move the line to the position after the following line in the filter expression.

