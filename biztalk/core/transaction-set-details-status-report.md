---
title: "Transaction Set Details Status Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d81367c7-c74e-42cb-b856-748962b727ec
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction Set Details Status Report
This report shows the details for transaction sets in a specific EDI interchange selected from within the Interchange/ACK Status report. To display this status report, right-click an interchange listed in the Query results pane of the Interchange/ACK Status report, and then click **Transaction Set Details**.  
  
 This report is available only if you have selected the **Store transaction set/payload for reporting** property in the General Page of the EDI Properties dialog box for the related party.  
  
## Fields in the Status Report  
 The Transaction Set Details Status Report displays the following information for transaction sets in received or sent interchanges:  
  
- Transaction Set ID  
  
- Document type  
  
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
  >  For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY. If the date is less than 75, it will be displayed as 20YY.  
  > 
  >  For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date Time will be listed in the report as 11/13/1999.  
  
- Processing Date/Time (not displayed by default)  
  
- Group Date/Time (not displayed by default)  
  
## Fields in the Query Expression for the Status Report  
 You can customize the EDI Interchange and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed. The following fields are available:  
  
|||||  
|-|-|-|-|  
|Query Expression Field|Potential Operators|Potential Values|Included By Default?|  
|Search for|Equals|Transaction Set Details|Yes (required)|  
|Interchange Date Time|Less Than or Equals<br /><br /> Greater Than or Equals|Specific Date Time<br /><br /> Today<br /><br /> Today - 1|Yes<br /><br /> Note: Can be included more than once in the query expression.|  
|Receiver Party Name|Equals|All (default)<br /><br /> Specific party name|Yes|  
|Sender Party Name|Equals|All (default)<br /><br /> Specific party name|Yes|  
|Direction|Equals|All (default)<br /><br /> Receive<br /><br /> Send|Yes|  
|Control ID|Equals|Interchange Control ID|Yes|  
|Transaction Set Correlation Id|Equals|Correlation Id|Yes|  
|Maximum Matches|Equals|Integer (default of 50)|Yes|  
|Status|Equals<br /><br /> Not Equals|Accepted<br /><br /> Accepted with Errors<br /><br /> Sent<br /><br /> All<br /><br /> Ack Expected<br /><br /> Ack Not Expected<br /><br /> Rejected|No|  
|Transaction Set Id|Equals|Transaction Set Id|No|  
  
## Additional Reports Displayed from This Report  
 You can display the following additional status reports for a transaction set shown in the Transaction Set Details report:  
  
-   Message Content status report. You access this report by right-clicking a transaction set in the details reports, and then clicking View Transaction Set Content. For more information, see [EDI Message Content Status Report](../core/edi-message-content-status-report.md).  
  
-   Interchange/ACK Status report. This report uses the same user interface as the [EDI Interchange and Correlated ACK Status Report](../core/edi-interchange-and-correlated-ack-status-report.md) that is displayed for multiple interchanges. The difference is that this report data for only the interchange that contains this transaction set.  
  
