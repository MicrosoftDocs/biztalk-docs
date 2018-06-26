---
title: "Interchange Status and ACK Details Status Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ebba4af5-6dff-4bb8-9c63-739ef49bbbb8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interchange Status and ACK Details Status Report
This status report displays details of an interchange and its correlated interchange (technical) acknowledgment and functional acknowledgments. You display this report for right-clicking an interchange within the Interchange/ACK status report, and then clicking **Interchange status and ack details**.  
  
 This report provides the following separate views for the interchange and the correlated acknowledgments:  
  
## Interchange Status  
 This view provides a table showing the values for the following fields:  
  
- Sender party ID  
  
- Receiver party ID  
  
- Control ID  
  
- Receiver party name  
  
- Sender party name  
  
- Direction  
  
- Interchange Date Time  
  
  > [!NOTE]
  >  For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY. If the date is less than 75, it will be displayed as 20YY.  
  > 
  >  For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date will be listed in the report as 11/13/1999.  
  
- Group count  
  
- Port ID  
  
- Interchange Status  
  
- EDI encoding type  
  
- Transaction Set Correlation Id  
  
  If a technical acknowledgment is enabled for a party as an interchange receiver (in the ACK Processing and Validation Settings page of the EDI Properties dialog box), BizTalk Server expects a technical (interchange) acknowledgment to be returned in response to an interchange that it sends. When it initially creates an interchange status entry for an outbound interchange, it will enter ACK Expected in the Interchange Status field. When it receives a technical acknowledgment and correlates it to the original interchange, it will update the Interchange Status field to indicate that it has received the acknowledgment.  
  
## Interchange Ack Status  
 This view displays status values for an interchange (technical) acknowledgment:  
  
-   Ack Interchange Control ID  
  
-   Receiver party  
  
-   Sender party  
  
-   Direction  
  
-   Ack Interchange Date  
  
-   Ack Interchange Time  
  
-   Ack Status  
  
-   Status Code  
  
-   Ack Note Code1  
  
-   Ack Note Code2  
  
## Functional Ack(s)  
 This view displays status values for an functional acknowledgment:  
  
-   Group Control Number  
  
-   Receiver party  
  
-   Sender party  
  
-   Direction  
  
-   Status  
  
-   Status Code  
  
-   Functional ID Code  
  
-   TS Count  
  
-   Ack Interchange Control ID  
  
-   Ack Interchange Date  
  
-   Ack Interchange Time  
  
-   Delivered TS Count  
  
-   Accepted TS Count  
  
-   ErrorCode 1  
  
-   ErrorCode 2  
  
-   ErrorCode 3  
  
-   ErrorCode 4  
  
-   ErrorCode 5  
  
-   Time Received