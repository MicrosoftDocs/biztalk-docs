---
description: "Learn more about: Transaction Set Aggregation Report Page UI"
title: Transaction Set Aggregation Report Page UI
TOCTitle: Transaction Set Aggregation Report Page UI
ms:assetid: 7e9a693b-17af-4f57-92d9-ab8278eed2ae
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743496(v=BTS.80)
ms:contentKeyID: 51529225
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.edir2.status.transaction.set.aggregation
---

# Transaction Set Aggregation Report Page UI

 

The properties included in this page define which transaction sets will be included in the Transaction Set Aggregation status report. The transaction set report will show all transaction sets that are processed by the EDI send and receive pipelines and that meet the criteria defined on this page.

The Transaction Set Aggregation Report page is displayed by clicking the BizTalk Group node in the console tree of the BizTalk Server Administration Console, and then clicking **Transaction Set Aggregation Report** in the right pane.

In this status report, you can get the status for transaction sets. The results pane will include the following data (if all columns are included):

  - Transaction Set ID

  - Transaction Set Count

  - Sender party

  - Receiver party

  - Direction

  - Earliest Started Date/Time
    

    > [!NOTE]
    > <P>For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, BizTalk Server will display the year as 19YY. If the date is less than 75, it will be displayed as 20YY.</P>
    > <P>For example, if you receive an interchange that contains the value 991113 in ISA09, the Earliest Started Date/Time will be listed in the report as 11/13/1999.</P>



  - Latest Ended Date/Time

If you right-click anywhere in the Results pane, you will see an **Add/Remove Columns** command that you can use to make changes to the columns in the result.

## Interchange Aggregation Report Query Fields

**Interchange Date Time**  
Specify that only interchanges (including acknowledgments) that were sent before or after (or equal to) the selected date and time will be displayed in the status report.

For **Value**, enter the date and time that the interchange was sent by clicking **Choose Date** and moving to the date. The default value is 12:00 AM of the previous date. You can also select **\[Today\]** to select the current date or **\[Today-1\]** to select one day before the current date.

For **Operator**, select an operator of **Greater Than or Equals** to display only interchanges sent on or after the date and time (and their correlated acknowledgments), or select **Less Than or Equals** to display only interchanges sent on or before the date and time (and their correlated acknowledgments). The default operator is **Greater Than or Equals**.

This field is part of the default query.


> [!NOTE]
> <P>You can enter two instances of this Field in the query, one with an <STRONG>Operator</STRONG> of <STRONG>Greater Than or Equals</STRONG>, and the other with an <STRONG>Operator</STRONG> of <STRONG>Less Than or Equals</STRONG>.</P>



**Maximum Matches**  
Specify how many matches, and no more, will be displayed in the status report.

The **Value** field can be from **1** to **50000**. The default value is **50**.

This field is part of the default query.

**Direction**  
Specify that only interchanges with the selected direction will be displayed in the status report.

The Value field can be **All**, **Receive**, or **Send**. The default is **All**.

This field is not part of the default query.

**Receiver party**  
Specify that only interchanges being sent to the specified receiver party will be displayed in the status report.

For **Value**, you can either enter a value for the receiver partner name, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Sender party**  
Specify that only interchanges being received from the specified sender party will be displayed in the status report.

For **Value**, you can either enter a value for the sender partner name, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Status**  
Specify that only interchanges with the selected status will be displayed in the status report.

The **Value** field can be **Accepted**, **Accepted with Errors**, **Sent**, **All**, **Ack Expected**, **Ack Not Expected**, or **Rejected**. The default value is **Accepted**.

The **Operator** field can be **Equals** or **Not Equals**. The default value is **Not Equals**.

This field is part of the default query.

**Transaction Set ID**  
Specify that only interchanges with the selected transaction set ID will be displayed in the status report.

This field is not part of the default query.

**Run Query**  
Click to run the query defined in the fields above, and to display the results. After validations have been done, the query is executed against the BAM reporting data store and the results are displayed as a single data grid with each row representing an interchange.

**Save As**  
Click to save a query to a BTQ file.

**Open Query**  
Click to open a query in a BTQ file.

## See Also

[Transaction Set Aggregation Report](https://msdn.microsoft.com/library/bb727941\(v=bts.80\))

