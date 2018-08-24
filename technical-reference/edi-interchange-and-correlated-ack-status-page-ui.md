---
title: EDI Interchange and Correlated ACK Status Page UI
TOCTitle: EDI Interchange and Correlated ACK Status Page UI
ms:assetid: 9edaf8b6-80ce-414b-967d-476e1930c342
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226437(v=BTS.80)
ms:contentKeyID: 51530075
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.edir2.status.EDI
---

# EDI Interchange and Correlated ACK Status Page UI

 

The properties included in this page define which interchanges and their correlated acknowledgments will be included in the Interchange/ACK status report. The interchange status report will show all interchanges that are processed by the EDI send and receive pipelines and that meet the criteria defined on this page.

The EDI Interchange and Correlated ACK Status page is displayed by clicking the BizTalk Group node in the console tree of the BizTalk Server Administration Console, and then clicking **EDI Interchange and Correlated ACK Status** in the right pane.

In this status report, you can get the status for interchanges, technical ACKs (for each interchange), and functional ACKs (for each group in each interchange). The results pane will include the following data (if all columns are included):

  - Sender Party

  - Receiver Party

  - Control ID

  - Direction

  - Interchange Date Time

  - EDI encoding type

  - Interchange Status

  - Group Count

  - Port ID

  - Sender party alias (not displayed by default)

  - Receiver party alias (not displayed by default)

  - Transaction Set Correlation Id (not displayed by default)

If you right-click a row in the query results in the Interchange Status page, you will see an **Interchange ACK Details** command that you can use to display a page showing details of the interchange.

If you right-click anywhere in the Results pane, you will see an **Add/Remove Columns** command that you can use to make changes to the columns in the result. Initially, you can use the **Add/Remove Columns** command to add either the Sender Partner Alias column or the Receiver Partner Alias column to the default columns of the results pane.

The Sender Party Alias and the Receiver Party Alias will be displayed in the following format: \[\<*qualifier*\>\]\<*identifier*\>.


> [!NOTE]
> <P>There is no wild-card support in any of the query fields, operators, or values.</P>



## Interchange Status Report Query Fields

**Status**  
Specify that only interchanges (and their correlated acknowledgments) with the selected status will be displayed in the status report.

The **Value** field can be **Accepted**, **Accepted with Errors**, **Sent**, **All**, **Ack Expected**, **Ack Not Expected**, or **Rejected**. The default value is **Accepted**.

The **Operator** field can be **Equals** or **Not Equals**. The default value is **Not Equals**.

This field is part of the default query.

**Interchange Date Time**  
Specify that only interchanges (and their correlated acknowledgments) that were sent before or after (or equal to) the selected date and time will be displayed in the status report.

For **Value**, enter the date and time that the interchange was sent by clicking **Choose Date** and moving to the date. The default value is 12:00 AM of the previous date. You can also select **\[Today\]** to select the current date or **\[Today-1\]** to select one day before the current date.

For **Operator**, select an operator of **Greater Than or Equals** to display only interchanges sent on or after the date and time (and their correlated acknowledgments), or select **Less Than or Equals** to display only interchanges sent on or before the date and time (and their correlated acknowledgments). The default operator is **Greater Than or Equals**.

This field is part of the default query.


> [!NOTE]
> <P>You can enter two instances of this Field in the query, one with an <STRONG>Operator</STRONG> of <STRONG>Greater Than or Equals</STRONG>, and the other with an <STRONG>Operator</STRONG> of <STRONG>Less Than or Equals</STRONG>.</P>



**Maximum Matches**  
Specify how many matches, and no more, will be displayed in the status report.

The **Value** field can be from **1** to **50000**. The default value is **50**.

This field is part of the default query.

**Control ID**  
Specify that only interchanges with the selected control ID (and their correlated acknowledgments) will be displayed in the status report.

For **Value**, you can either enter a value for the control ID, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Direction**  
Specify that only interchanges with the selected direction (and their correlated acknowledgments) will be displayed in the status report.

The Value field can be **All**, **Receive**, or **Send**. The default is **All**.

This field is not part of the default query.

**Receiver Party**  
Specify that only interchanges being sent to the specified receiver party (and their correlated acknowledgments) will be displayed in the status report.

For **Value**, you can either enter a value for the receiver partner name, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Sender Party**  
Specify that only interchanges being received from the specified sender party (and their correlated acknowledgments) will be displayed in the status report.

For **Value**, you can either enter a value for the sender partner name, or select **All** from the drop-down list. The default is **All**.

This field is not part of the default query.

**Run Query**  
Click to run the query defined in the fields above, and to display the results. After validations have been done, the query is executed against the BAM reporting data store and the results are displayed as a single data grid with each row representing an interchange.

**Save As**  
Click to save a query to a BTQ file.

**Open Query**  
Click to open a query in a BTQ file.

## In This Section

[Interchange Status and ACK Details Page UI](interchange-status-and-ack-details-page-ui.md)

[Transaction Set Details Page UI](transaction-set-details-page-ui.md)

[Message Content Status Page UI](message-content-status-page-ui.md)

