---
title: Batch Status Page UI
TOCTitle: Batch Status Page UI
ms:assetid: d0019eb4-15c5-439b-bb7a-4a1ef3a42428
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226538(v=BTS.80)
ms:contentKeyID: 51531368
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.edir2.status.batch
---

# Batch Status Page UI

 

The properties included in this page define which batches will be included in the batch status report. The batch status report wil show all interchanges that are processed by the batching subsystem and meet the criteria defined on this page.

The Batch Status page displayed by clicking the BizTalk Group node in the console tree of the BizTalk Server Administration Console, and then clicking **Batch Status** in the right pane.

In this status report, the results pane will include the following data (if all columns are included):

  - Batch Status

  - Batch Name

  - Destination party

  - Activation Time

  - Batch Occurrence Count

  - EDI encoding type

  - Batch Type

  - Batch Target

  - Batch Element Count: how many batch elements have been accumulated by the batching orchestration instance

  - Rejected Elements Count

  - Latest action: Can be Batch defined, Batch activated, Element added, Batch released, Batch override release, Batch terminate release, Batch sent, and Batch about to release.

  - Interchange Control No

  - Interchange Date Time

  - Batch Size (in chars) (not displayed by default)

You can views details about the batched interchanges by right-clicking a batched interchange in the query results, and then clicking **Interchange/ACK Status**.

If you right-click anywhere in the Results pane, you will see an **Add/Remove Columns** command that you can use to make changes to the columns in the result.


> [!NOTE]
> <P>There is no wild-card support in any of the query fields, operators, or values.</P>



## Batch Status Query Fields

**Batch Status**  
Specify that only batches with the selected status will be displayed in the status report.

The **Value** field can be **Defined**, **Active**, **Released**, **Completed**, or **All**. The default value is **Active**.

The **Operator** field can be **Equals** or **Not Equals**. The default value is **Equals**.

The **Defined** status indicates that batch settings have been created, but the batching orchestration is not active and is not collecting messages for the batch because the batch start date time is in the future.

The **Active** status indicates that the batching orchestration is active and collecting messages for the batch, because the batch start date time has been reached.

The **Released** status indicates that the batching orchestration has released the batch XML file to the MessageBox because the batch release criteria has been satisfied, but that the batch has not been sent by the send pipeline. It can also indicate that the batching orchestration was stopped before any messages were processed.

The **Completed** status indicates that the batch has been sent by the send pipeline.

This field is part of the default query.

**Maximum Matches**  
Specify how many matches, and no more, will be displayed in the status report.

The **Value** field can be from **1** to **50000**. The default value is **50**.

This field is part of the default query.

**Activation Date Time**  
Specify that only batches activated before or after (or equal to) the selected date and time will be displayed in the status report.

For **Value**, enter the date and time that the interchange was sent by clicking **Choose Date** and moving to the date. The default value is 12:00 AM of the previous date. You can also select **\[Today\]** to select the current date or **\[Today-1\]** to select one day before the current date.

For **Operator**, select an operator of **Greater Than or Equals** to display only batches activated on or after the date and time, or select **Less Than or Equals** to display only batches activated on or before the date and time.

This field is not part of the default query.


> [!NOTE]
> <P>You can enter two instances of this Field in the query, one with an <STRONG>Operator</STRONG> of <STRONG>Greater Than or Equals</STRONG>, and the other with an <STRONG>Operator</STRONG> of <STRONG>Less Than or Equals</STRONG>.</P>



**Batch Name**  
Specify that only batches with the specified name will be displayed in the status report.

For **Value**, you can enter a value for the batch name, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Destination Party**  
Specify that only batches being sent to the specified receiver partner will be displayed in the status report.

For **Value**, you can either enter a value for the receiver partner name, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**EDI encoding type**  
Specify the type of EDI encoding type that messages displayed in the status report will have.

For **Value**, you can select **X12**, **EDIFACT**, or **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Run Query**  
Click to run the query defined in the fields above, and to display the results. After validations have been done, the query is executed against the BAM reporting data store and the results are displayed as a single data grid with each row representing a batch.

**Save As**  
Click to save a query to a BTQ file.

**Open Query**  
Click to open a query in a BTQ file.

