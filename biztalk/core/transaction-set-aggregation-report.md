---
title: "Transaction Set Aggregation Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6e1417e-e0c6-4d30-aab5-d9bfe14cd4b8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction Set Aggregation Report
This report provides a single record that shows the number of EDI transaction sets that share the same Transaction Set ID, EDI encoding type, sender party, receiver party, and direction. This report does not provide details about the individual transaction sets.  
  
 This status report is displayed by clicking the Transaction Set Aggregation Report link at the bottom of the Group Hub page in the BizTalk Server Administration Console.  
  
## Fields in the Status Report  
 The Transaction Set Aggregation Report displays the following information for the received or sent interchanges:  
  
- A count of how many transaction sets share the same Transaction Set ID, EDI encoding type, sender party, receiver party, and direction  
  
- The Sender Party for each transaction set in the record  
  
- The Receiver Party for each transaction set in the record  
  
- The Direction (receive or send) of each transaction set in the record  
  
- The date and time at which the earliest transaction set in the time range was sent or received (Earliest Started Date/Time)  
  
  > [!NOTE]
  >  For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY. If the date is less than 75, it will be displayed as 20YY.  
  > 
  >  For example, if you receive an interchange that contains the value 991113 in ISA09, the Earliest Started Date/Time will be listed in the report as 11/13/1999.  
  
- The date and time at which the latest transaction set in the time range was sent or received (Latest Ended Date/Time)  
  
## Fields in the Query Expression for the Status Report  
 You can customize the Interchange Aggregation Report by changing the fields in the query expression that determines the data displayed. The following fields are available:  
  
|||||  
|-|-|-|-|  
|Query Expression Field|Potential Operators|Potential Values|Included By Default?|  
|Search for|Equals|Transaction Set Aggregation Report|Yes (required)|  
|Interchange Date Time|Less Than or Equals<br /><br /> Greater Than or Equals|Specific Date Time<br /><br /> Today<br /><br /> Today - 1|Yes<br /><br /> Note: Can be included twice in the query expression, once with a less-than operator and once with  a greater-than operator, to provide a range|  
|Maximum Matches|Equals|Integer (default of 50)|Yes|  
|Direction|Equals|All (default)<br /><br /> Receive<br /><br /> Send|No|  
|Receiver Party Name|Equals|All (default)<br /><br /> Specific party name (AN string)|No|  
|Sender Party Name|Equals|All (default)<br /><br /> Specific party name (AN string)|No|  
|Status|Equals<br /><br /> Not Equals|Accepted<br /><br /> Accepted with Errors<br /><br /> Sent<br /><br /> All<br /><br /> Ack Expected<br /><br /> Ack Not Expected<br /><br /> Rejected|No|  
|Transaction Set ID|Equals|All (default)<br /><br /> Specific transaction set ID|No|  
  
