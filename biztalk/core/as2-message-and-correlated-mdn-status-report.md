---
title: "AS2 Message and Correlated MDN Status Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48ed0ee3-c844-4cb9-a84d-32b719ab8fab
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Message and Correlated MDN Status Report
This report shows all AS2 messages that are processed by the AS2 send and receive pipelines, and the MDNs correlated to those interchanges.  
  
## Fields in the Status Report  
 The AS2 Message and Correlated ACK Status Report displays the following information for the received or sent interchanges and the acknowledgments that are correlated to them:  
  
-   Sender Party Name  
  
-   Receiver Party Name  
  
-   AS2 From  
  
-   AS2 To  
  
-   AS2 Message ID  
  
-   AS2 Message Date Time  
  
-   Received Date Time  
  
-   Party Role  
  
-   MDN Status  
  
-   Encryption Status  
  
-   Signature Status  
  
-   Edi Interchange Status  
  
-   Is AS2 Message duplicate  
  
-   Days to check for duplicate  
  
-   Filename  
  
-   Reliable messaging enabled  
  
## Fields in the Query Expression for the Status Report  
 You can customize the AS2 Message and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed. The following fields are available:  
  
|||||  
|-|-|-|-|  
|Query Expression Field|Potential Operators|Potential Values|Included By Default?|  
|Search for|Equals|AS2/MDN Status|Yes (required)|  
|Message Status|Equals<br /><br /> Not Equals|All<br /><br /> Acknowledged - Processed<br /><br /> Acknowledged - Failed<br /><br /> Processed - MDN pending<br /><br /> Processed - MDN not expected<br /><br /> Not acknowledged – Resend attempts exceeded<br /><br /> Not acknowledged – Resend duration exceeded|Yes|  
|AS2 Message Date Time|Less Than or Equals<br /><br /> Greater Than or Equals|Specific Date Time<br /><br /> Today<br /><br /> Today - 1|Yes<br /><br /> Note: Can be included more than once in the query expression.|  
|Maximum Matches|Equals|Integer (default of 50)|Yes|  
|AS2 Message ID|Equals|All<br /><br /> Specific AS2 Message ID|No|  
|Direction|Equals|All (default)<br /><br /> Receive<br /><br /> Send|No|  
|Receiver Party Name|Equals|All (default)<br /><br /> Specific party name|No|  
|Sender Party Name|Equals|All (default)<br /><br /> Specific party name|No|  
  
## Additional AS2 Message and Correlated MDN Status Reports  
 If you right-click an AS2 message listed in the AS2 Message and Correlated MDN status report, you can display one of the following more detailed status reports:  
  
|Status Report|Status Displayed|  
|-------------------|----------------------|  
|Interchange/ACK Status|The status of the EDI payload of the AS2 message|  
|Resend Status Details|The resend status of the message|  
|Message Wire Format|The wire format of the AS2 message|  
|Message Decoded|The decoded format of the AS2 message|  
|MDN Message|The MDN message correlated to the AS2 message|  
  
 The format of each of the final three messages is the same. For more information, see [AS2 Message Content Status Reports](../core/as2-message-content-status-reports.md).  
  
## Correlate an AS2 Message with its EDI Payload  
 AS2 and EDI status reporting enables you to correlate status entries for an AS2 message and its EDI payload. If you have enabled both AS2 and EDI status reporting, a status entry is made in the AS2 status report for the AS2 message and a status entry is made in the EDI status report for the EDI payload of that AS2 message. If you have the AS2 status report displayed, you can display the status of the EDI payload for an AS2 message by right-clicking the AS2 message status entry, and then clicking **Interchange/ACK Status**. If there is only one EDI interchange in the AS2 message, this action will bring up the status entry for that one interchange.  
  
 If the AS2 message contains multiple EDI interchanges, and you attempt to display the status of the multiple EDI interchanges in the AS2 message, only the last EDI interchange will be displayed in the Interchange/ACK status report. In addition, the **EDI Interchange Control No** field in the AS2/MDN Status report will only show the last interchange control number. (The interchange control number correlates the AS2 message and its EDI interchange payload.)  
  
 The data for all EDI interchanges in an AS2 message is saved in the status report database. You can display all interchanges in an AS2 message in the Interchange/ACK Status report if the **Control ID Equals All** clause is in the status report query. This will also potentially display other interchanges that are not in the AS2 message; however, you can determine which EDI interchanges are in a single AS2 message by looking at other fields, such as the Sender party, Receiver party, and Interchange Date Time.  
  
 The **Party role** field in the AS2 status report and the **Direction** field in the EDI status report are opposite in their meaning. For an incoming AS2 message with an EDI payload, the **Party role** field for the AS2 message would be **Sender**, while the **Direction** field for the EDI interchange would be **Receive**. The reason for this is that for an incoming message received from a party, the role of that party is a sender. The properties of that party related to an AS2 message that it sends are that of party as AS2 message sender, as defined in the AS2 Properties dialog box in the Partner Agreement Management. As a result, the AS2 party role is opposite to the EDI direction.  
  
## Next steps
  
-   [AS2 Message Content Status Reports](../core/as2-message-content-status-reports.md)  
  
-   [Resend Status Details Report](../core/resend-status-details-report.md)  
  
## See Also  
 [AS2 Message and Correlated MDN Status Report](../core/as2-message-and-correlated-mdn-status-report.md)   
