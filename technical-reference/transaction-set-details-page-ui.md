---
description: "Learn more about: Transaction Set Details Page UI"
title: Transaction Set Details Page UI
TOCTitle: Transaction Set Details Page UI
ms:assetid: 1123586a-ecd8-439c-96f0-43c8965b9340
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743355(v=BTS.80)
ms:contentKeyID: 51526296
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- bts10.edir2.status.transaction.set.details
---

# Transaction Set Details Page UI

 

If you right-click an interchange in the query results on the EDI Interchange and Correlated ACK Status Page, and click the **Transaction set details** command, details about each transaction set in the interchange will be displayed. The results pane will include the following data (if all columns are included):

  - Transaction Set ID

  - Document Type

  - Sender party alias

  - Application Sender

  - Receiver party alias

  - Application Receiver

  - Direction

  - Interchange Control Number

  - Group Control Number

  - Transaction Set Control Number

  - Transaction Set Status

  - Interchange Date Time (not displayed by default)
    

    > [!NOTE]
    > <P>For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, BizTalk Server will display the year as 19YY. If the date is less than 75, it will be displayed as 20YY.</P>
    > <P>For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date Time will be listed in the report as 11/13/1999.</P>



  - Processing Date/Time (not displayed by default)

  - Group Date/Time (not displayed by default)

## Transaction Set Details Query Fields

**Interchange Date Time**  
Specify that only transaction sets in interchanges that were sent before or after (or equal to) the selected date and time will be displayed in the status report.

For **Value**, enter the date and time that the interchange was sent by clicking **Choose Date** and moving to the date. The default value is 12:00 AM of the previous date. You can also select **\[Today\]** to select the current date or **\[Today-1\]** to select one day before the current date.

For **Operator**, select an operator of **Greater Than or Equals** to display only interchanges sent on or after the date and time (and their correlated acknowledgments), or select **Less Than or Equals** to display only interchanges sent on or before the date and time (and their correlated acknowledgments). The default operator is **Greater Than or Equals**.

This field is part of the default query.


> [!NOTE]
> <P>You can enter two instances of this Field in the query, one with an <STRONG>Operator</STRONG> of <STRONG>Greater Than or Equals</STRONG>, and the other with an <STRONG>Operator</STRONG> of <STRONG>Less Than or Equals</STRONG>.</P>



**Receiver party**  
Specify that only transaction sets in interchanges being sent to the specified receiver party will be displayed in the status report.

For **Value**, you can either enter a value for the receiver partner name, or select **All** from the drop-down list. The default is **All**.

This field is part of the default query.

**Sender party**  
Specify that only transaction sets in interchanges being received from the specified sender party will be displayed in the status report.

For **Value**, you can either enter a value for the sender partner name, or select **All** from the drop-down list. The default is **All**.

This field is part of the default query.

**Direction**  
Specify that only transaction sets in interchanges with the selected direction will be displayed in the status report.

The Value field can be **All**, **Receive**, or **Send**. The default is **All**.

This field is part of the default query.

**Control ID**  
Specify that only transaction sets in interchanges with the selected interchange control ID will be displayed in the status report.

For **Value**, you can either enter a value for the control ID, or select **All** from the drop-down list. The default is **All**.

This field is part of the default query.

**Transaction Set Correlation Id**  
Specify that only transaction sets with the selected transaction set correlation ID will be displayed in the status report.

For **Value**, you can either enter a value for the control ID, or select **All** from the drop-down list. The default is **All**.

This field is part of the default query.

**Maximum Matches**  
Specify how many matches, and no more, will be displayed in the status report.

The **Value** field can be from **1** to **50000**. The default value is **50**.

This field is part of the default query.

**Status**  
Specify that only transaction sets in interchanges with the selected status will be displayed in the status report.

The **Value** field can be **Accepted**, **Accepted with Errors**, **Sent**, **All**, **Ack Expected**, **Ack Not Expected**, or **Rejected**. The default value is **Accepted**.

The **Operator** field can be **Equals** or **Not Equals**. The default value is **Not Equals**.

This field is not part of the default query.

**Transaction Set ID**  
Specify that only transaction sets with the selected transaction set ID will be displayed in the status report.

For **Value**, you can either enter a value for the control ID, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Run Query**  
Click to run the query defined in the fields above, and to display the results. After validations have been done, the query is executed against the BAM reporting data store and the results are displayed as a single data grid with each row representing an interchange.

**Save As**  
Click to save a query to a BTQ file.

**Open Query**  
Click to open a query in a BTQ file.

## See Also

[Transaction Set Details Status Report](https://msdn.microsoft.com/library/bb743711\(v=bts.80\))

