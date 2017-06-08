---
title: "AS2 Message and Correlated MDN Status Page UI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edir2.status.AS2"
ms.assetid: e61c36a2-d15e-4b81-9d8d-07614f5f1c9f
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Message and Correlated MDN Status Page UI
The properties included in this page define which AS2 messages processed by the AS2 send and receive pipelines and their correlated MDNs will be included in the AS2/MDN status report.  
  
 The AS2/MDN Status page is displayed by clicking the BizTalk Group node in the console tree of the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console, and then clicking **AS2 MDN Status** in the right pane.  
  
 In this status report, the results pane will include the following data (if all columns are included):  
  
-   Sender party  
  
-   Receiver party  
  
-   AS2 From  
  
-   AS2 To  
  
-   AS2 MessageID  
  
-   AS2 Message Date Time  
  
-   Received Date Time  
  
-   Party role  
  
-   MDN Status  
  
-   Encryption Status  
  
-   Signature Status  
  
-   Edi Interchange Control No  
  
-   Is AS2 Message Duplicate  
  
-   Days to check for duplicate  
  
-   Filename  
  
-   Reliable messaging enabled  
  
 If you right-click a row in the query results in the AS2 Message and Correlated MDN Status page, you will see a **View Related Interchange** command that you can use to display a page showing the interchanges related to the batch. The fields of the query for this command will be populated with values that are specific to the row that you right-click. You will also get commands enabling you to display the message wire format, decoded message, or MDN message (in text or binary format).  
  
 If you right-click a row that display the Receiver party role, you will see a **View Reliable Messaging Status** command that you can use to display a history of resend attempts for this message. The fields displayed for this command will be populated with values that are specific to the row that you right-click.  
  
> [!NOTE]
>  The **View Reliable Messaging Status** command will only be available for parties that are configured with the **Resend AS2 message if MDN not received** property on the Party as AS2 Message Receiver page of the party AS2 Properties page.  
  
 If you right-click anywhere in the Results pane, you will see an **Add/Remove Columns** command that you can use to make changes to the columns in the result.  
  
> [!NOTE]
>  There is no wild-card support in any of the query fields, operators, or values.  
  
## AS2 Message and Correlated MDN Status Query Fields  
 **Message Status**  
 Specify that only AS2 message (and their correlated MDN messages) with the selected status will be displayed in the status report.  
  
 The **Value** field can be **All**, **Acknowledged - Processed**, **Acknowledged - Rejected**, **Processed - MDN pending**, **Processed - MDN not expected**, **Not acknowledged – Resend attempts exceeded**, or **Not acknowledged – Resend Duration exceeded**. The default value is **Acknowledged-Processed**. (with an operator of **Not Equals**).  
  
 The **Operator** field can be **Equals** or **Not Equals**. The default value is **Not Equals**.  
  
 This field is part of the default query.  
  
 **Maximum Matches**  
 Specify how many matches, and no more, will be displayed in the status report.  
  
 The **Value** field can be from **1** to **50000**. The default value is **50**.  
  
 This field is part of the default query.  
  
 **AS2 Message Date Time**  
 Select the date or dates that status reporting is enabled for AS2 messages.  
  
 For **Value**, enter the date and time that the interchange was sent by clicking **Choose Date** and moving to the date. The default value is 12:00 AM of the previous date. You can also select **[Today]** to select the current date or **[Today-1]** to select one day before the current date.  
  
 The operators that you can use with this field are **Greater than or Equals** and **Less than or Equals**. Both operators can be used.  
  
 The default is the current date.  
  
 This field is part of the default query.  
  
> [!NOTE]
>  You can enter two instances of this Field in the query, one with an **Operator** of **Greater Than or Equals**, and the other with an **Operator** of **Less Than or Equals**.  
  
 **AS2 Message ID**  
 Specify that only AS2 messages with the selected message ID (and their correlated MDN messages) will be displayed in the status report.  
  
 For **Value**, you can either enter a value for the message ID, or select **All** from the drop-down list. The default is **All**.  
  
 This field is not part of the default query.  
  
 **Direction**  
 Specify that only AS2 messages with the selected direction (and their correlated MDN messages) will be displayed in the status report.  
  
 The Value field can be **All**, **Received**, or **Sender**. The default is **All**.  
  
 This field is not part of the default query.  
  
 **Receiver party**  
 Specify that only AS2 messages being sent to the specified receiver partner (and their correlated MDN messages) will be displayed in the status report.  
  
 For **Value**, you can either enter a value for the receiver partner name, or select **All** from the drop-down list. The default is **All**.  
  
 This field is not part of the default query.  
  
 **Sender party**  
 Specify that only AS2 messages being received from the specified sender partner (and their correlated MDN messages) will be displayed in the status report.  
  
 For **Value**, you can either enter a value for the sender partner name, or select **All** from the drop-down list. The default is **All**.  
  
 This field is not part of the default query.  
  
 **Run Query**  
 Click to run the query defined in the fields above, and to display the results. After validations have been done, the query is executed against the BAM reporting data store and the results are displayed as a single data grid with each row representing an AS2 message and its correlated MDN.  
  
 **Save As**  
 Click to save a query to a BTQ file.  
  
 **Open Query**  
 Click to open a query in a BTQ file.  
  
## In This Section  
 [Message Wire Format Page UI](../core/message-wire-format-page-ui.md)  
  
 [Message Decoded Page UI](../core/message-decoded-page-ui.md)  
  
 [MDN Message Page UI](../core/mdn-message-page-ui.md)  
  
 [Resend Status Details Page UI](../core/resend-status-details-page-ui.md)