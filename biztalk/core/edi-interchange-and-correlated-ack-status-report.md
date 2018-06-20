---
title: "EDI Interchange and Correlated ACK Status Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a112cc3d-d34c-4652-a8ee-3355a31d4a03
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Interchange and Correlated ACK Status Report
This report shows all EDI interchanges that are processed by the EDI send and receive pipelines, and the acknowledgment correlated to those interchanges.  
  
## Fields in the Status Report  
 The EDI Interchange and Correlated ACK Status Report displays the following information for the received or sent interchanges and the acknowledgments that are correlated to them:  
  
- Sender Party  
  
  > [!NOTE]
  >  The sender party will be determined as follows:  
  > 
  > - If the party name in the interchange matches the name configured in the EDI Properties for a party, then the configured name is displayed.  
  >   -   If the party name in the interchange does not match any of the configured EDI Properties for existing parties, the party name specified in the interchange is displayed.  
  
- Receiver Party  
  
  > [!NOTE]
  >  The receiver party name will be determined as follows:  
  > 
  > - If the party name in the interchange matches the name configured in the EDI Properties for a party, then the configured name is displayed.  
  >   -   If the party name in the interchange does not match any of the configured EDI Properties for existing parties, the party name specified in the interchange is displayed.  
  
- Control ID  
  
- Direction  
  
- Interchange Date Time  
  
- EDI encoding type  
  
- Interchange Status  
  
- Group Count  
  
- Port ID  
  
- Sender Party Alias  
  
- Receiver Party Alias  
  
- Transaction Set Correlation ID  
  
## Fields in the Query Expression for the Status Report  
 You can customize the EDI Interchange and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed. The following fields are available:  
  
|||||  
|-|-|-|-|  
|Query Expression Field|Potential Operators|Potential Values|Included By Default?|  
|Search for|Equals|Interchange/ACK Status|Yes (required)|  
|Status|Equals<br /><br /> Not Equals|Accepted<br /><br /> Accepted with Errors<br /><br /> Sent<br /><br /> All<br /><br /> Ack Expected<br /><br /> Ack Not Expected<br /><br /> Rejected<br /><br /> (These values are defined below.)|Yes|  
|Interchange Date Time|Less Than or Equals<br /><br /> Greater Than or Equals|Specific Date Time<br /><br /> Today<br /><br /> Today - 1|Yes<br /><br /> Note: Can be included more than once in the query expression.|  
|Maximum Matches|Equals|Integer (default of 50)|Yes|  
|Control ID|Equals|Interchange Control ID|No|  
|Direction|Equals|All (default)<br /><br /> Receive<br /><br /> Send|No|  
|Receiver Party|Equals|All (default)<br /><br /> Specific party name|No|  
|Sender Party|Equals|All (default)<br /><br /> Specific party name|No|  
  
## Status Definitions  
 The status values used in EDI status reports have the following definitions:  
  
- Accepted: Valid interchange  
  
- Accepted with Errors: Errors were noted in segments  
  
- Sent: The interchange was sent successfully  
  
- All: Display a message with any of the other values  
  
- Ack Expected  
  
  > [!NOTE]
  >  The Interchange Status field in the Interchange Status and ACK Details status report will be set to "Ack Expected" for an outbound message when the message is sent if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] expects a technical acknowledgment. This occurs if the **TA1 Expected** property is set in **Acknowledgements** page for the one-way agreement tab. The status will be changed to “Accepted” when the technical acknowledgment has been received and validated. Note that this only occurs for a technical acknowledgment, not a functional acknowledgment.  
  
- Ack Not Expected  
  
- Rejected: The interchange was invalid due to errors.  
  
## Additional Reports Displayed from This Report  
 You can display the following additional status reports for a transaction set shown in the Transaction Set Details report. You access the reports by right-clicking an interchange or acknowledgment listed in the EDI Interchange and Correlated ACK Status report, and then clicking the appropriate command:  
  
-   [Interchange Status and ACK Details Status Report](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [Transaction Set Details Status Report](../core/transaction-set-details-status-report.md)  
  
## Next steps
  
-   [Interchange Status and ACK Details Status Report](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [Transaction Set Details Status Report](../core/transaction-set-details-status-report.md)  
  
-   [EDI Message Content Status Report](../core/edi-message-content-status-report.md)  
  
