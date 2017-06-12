---
title: "Interchange Status and ACK Details Page UI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edir2.status.interchange.ack"
ms.assetid: d4322d4d-683b-4fb3-a71e-1c6ccf82c2c8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interchange Status and ACK Details Page UI
If you right-click a row in the query results on the EDI Interchange and Correlated ACK Status Page, and click the **Interchange status and ack details** command, details about the interchange and its technical and functional acknowledgments related to that interchange will be displayed.  
  
 The error report displayed for interchange acknowledgments shows numeric error codes only. To determine what the actual error condition is, see [EDI Acknowledgment Error Codes](../core/edi-acknowledgment-error-codes.md).  
  
## Interchange Status and ACK Details Pages  
 **General**  
 Displays general information about the interchange.  
  
 **Interchange Status**  
 Displays specific information about the interchange, including the following:  
  
-   Control ID  
  
-   Receiver party ID  
  
-   Sender party ID  
  
-   Receiver party  
  
-   Sender party  
  
-   Direction  
  
-   Interchange Date Time  
  
    > [!NOTE]
    >  For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY. If the date is less than 75, it will be displayed as 20YY.  
    >   
    >  For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date will be listed in the report as 11/13/1999.  
  
-   Group Count  
  
-   Port ID  
  
-   Interchange Status  
  
-   EDI encoding type  
  
-   Transaction Set Correlation Id  
  
 **Interchange ACK**  
 Displays specific information about the technical acknowledgment related to the interchange, including the following:  
  
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
  
 **Functional ACK(s)**  
 Displays specific information about the functional acknowledgments related to the groups in the interchange, including following:  
  
-   Group Control Number  
  
-   Sender party qualifier  
  
-   Sender party ID  
  
-   Receiver party qualifier  
  
-   Receiver party ID  
  
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
  
-   Errorcode 1  
  
-   Errorcode 2  
  
-   Errorcode 3  
  
-   Errorcode 4  
  
-   Errorcode 5  
  
-   Time Received.