---
description: "Learn more about: How Data Is Stored for Inbound EDI Messages"
title: "How Data Is Stored for Inbound EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8cbcb96-c0af-4f41-b844-f0e684a4af7c
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How Data Is Stored for Inbound EDI Messages
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does the following to generate a status report entry for an inbound interchange and the acknowledgment sent in response to it:  
  
1.  When inbound message XML is sent by the EDI receive pipeline to the MessageBox, the receive pipeline creates the following entries in the status reporting data store with the following values:  
  
    -   One status report entry for each interchange received, with Status set to Accepted/Partially Accepted/Rejected  
  
    -   One status report entry for each technical (interchange) acknowledgment, one per interchange, with Status set to Generated  
  
    -   One status report entry for each functional acknowledgment, one per group in X12 and one for all groups in EDIFACT, with Status set to Generated.  
  
2.  After the send pipeline has sent the acknowledgments to the trading partner, the EDI send pipeline updates the Interchange ACK status and Functional ACK status entries to Sent, as appropriate. No changes are made to the Interchange status entry.  
  
## Data Stored by the Receive Pipeline for Inbound Interchanges  
 The receive pipeline creates a record in the status report data store for each interchange that it receives. The data stored includes:  
  
-   Record Type = Interchange Status  
  
-   Interchange Direction = Receive  
  
-   Interchange Receiver = Update Data  
  
-   Interchange Sender = Update Data  
  
-   Interchange Date = Update Data  
  
-   Interchange Time = Update Data  
  
-   Interchange Control ID = Update Data  
  
-   Interchange Status: Update Data  
  
-   Count of Groups in Interchange = Update Data (In EDIFACT Groups are optional and if not present, valued as ‘Not Applicable’)  
  
-   Interchange Receive Port ID = Update Data  
  
## Data Stored by the Receive Pipeline for Each Technical Acknowledgment Generated in Response to an Inbound Interchange  
 The send pipeline creates a record in the status report data store for each technical acknowledgment that it sends. The technical acknowledgement is the TA1 for X12 and the CONTRL message with only the UCI Segment for EDIFACT. Most data required for the entry is available from the interchange header/trailer segments (ISA/IEA or UNB/UNZ). Other data is available from send port properties. The data stored includes:  
  
-   Record Type = Interchange ACK Status  
  
-   Interchange ACK Direction = Receive  
  
-   Interchange Receiver = Update Data (required for correlation)  
  
-   Interchange Sender = Update Data (required for correlation)  
  
-   Interchange Date = Update Data  
  
-   Interchange Control ID = Update Data (required for correlation)  
  
-   Interchange ACK Status = \< Expected or Not Applicable\>. If the technical ACK is configured or valued in the incoming interchange, status = Expected. Otherwise, status = Not Applicable.  
  
-   Interchange ACK Control ID= \<not valued\>  
  
-   Interchange ACK Date = \<not valued\>  
  
-   Interchange ACK Time = \<not valued\>  
  
-   ACK/Action Code = \<not valued\>  
  
-   ACK Note Code = \<not valued\>  
  
## Data Updated by the Send Pipeline for Each Technical Acknowledgment Generated in Response to Inbound Interchanges  
 For each technical acknowledgment that the send pipeline sends, it updates the status report entry for the correlated received interchange. The source for the data will be the Interchange envelopes created by the Send Pipeline.  
  
 The EDI Assembler locates records in the data store using data in the UCI and TA1 Segments of the incoming acknowledgment, as follows:  
  
|Fields in ACK|Fields in Data store|Comment|  
|-------------------|--------------------------|-------------|  
|Interchange Sender ID|Interchange Receiver|-|  
|Interchange Receiver ID|Interchange Sender|-|  
|-|Interchange Date|-|  
|Interchange Control Number|Interchange Control ID|-|  
|-|Interchange Direction = Receive|Required in preserved interchange scenario for uniqueness|  
|Record Type|Interchange ACK Status|-|  
  
 The data stored includes:  
  
-   Record Type = Interchange ACK Status  
  
-   Interchange ACK Direction = Send- Existing Data  
  
-   Interchange ACK Status = Processed or Sent – Update Data  
  
-   Interchange Receiver = Existing Data  
  
-   Interchange Sender = Existing Data  
  
-   Interchange Date = Existing Data  
  
-   Interchange Control ID = Existing Data  
  
-   Interchange ACK Control ID= Update Data  
  
-   Interchange ACK Date = Update Data  
  
-   Interchange ACK Time = Update Data  
  
-   ACK/Action Code = Existing Data  
  
-   ACK Note Code = Existing Data  
  
## Data Stored by the Receive Pipeline for Each Functional Acknowledgment Generated in Response to an Inbound Interchange  
 The send pipeline creates a record in the status report data store for each functional acknowledgment that it sends. The send pipeline creates a record of each functional acknowledgment sent (in response to an interchange received) in the status report data store. If no group is present in EDIFACT, one functional ACK will still be created. The functional ACK status report entry will be populated from the functional group header/trailer (GS/GE or UNG/UNE). The technical acknowledge is the 997 for X12 and the full CONTRL message for EDIFACT. The data stored includes:  
  
-   Record Type = Functional ACK Status  
  
-   Functional ACK Direction = Receive  
  
-   Functional ACK Status = \< Expected or Not Applicable\>. If the functional acknowledgment tab in PAM is selected, status will set to Expected. Otherwise, status will be set to Not Applicable.  
  
-   Interchange Receiver = Update Data (required for correlation)  
  
-   Interchange Sender = Update Data (required for correlation)  
  
-   Interchange Date = Update Data  
  
-   Interchange Control ID = Update Data (required for correlation)  
  
-   Group Control Number = Update Data (required for correlation. In EDIFACT if no group segments present this field is valued using UNH.1)  
  
-   Functional ID Code = Update Data (not valued in EDIFACT if group is not present)  
  
-   Count of Transaction Sets = Data (in EDIFACT this is mapped to UNE.1 while UNG/UNE are present or UNZ.1 if no group segments are present)  
  
-   Functional ACK Interchange Control ID= \<not valued\>  
  
-   Functional ACK Interchange Date = \<not valued\>  
  
-   Functional ACK Interchange Time = \<not valued\>  
  
-   Count of Transaction Sets Delivered = \<not valued\>  
  
-   Count of Transaction Sets Accepted = \<not valued\>  
  
-   ACK/Action Code = \<not valued\>  
  
-   Error/Syntax Error Code  = \<not valued\>  
  
-   Additional X12 ACK Error Code 2 = \<not valued\>  
  
-   Additional X12 ACK Error Code 3 = \<not valued\>  
  
-   Additional X12 ACK Error Code 4 = \<not valued\>  
  
-   Additional X12 ACK Error Code 5 = \<not valued\>  
  
## Data Updated by the Send Pipeline for Each Functional Acknowledgment Generated in Response to Inbound Interchanges  
 For each functional acknowledgment that the send pipeline sends, it updates the status report entry for the correlated received interchange. The source for the data will be the Interchange envelopes created by the Send Pipeline.  
  
 The EDI Assembler locates records in the data store using data in the Interchange and Group Header Segments of the incoming acknowledgment, as follows:  
  
|Fields in ACK|Fields in Data store|Comment|  
|-------------------|--------------------------|-------------|  
|Interchange Sender ID|Interchange Receiver|-|  
|Interchange Receiver ID|Interchange Sender|-|  
|Interchange Date|Interchange Date|-|  
|Interchange Control Number|Interchange Control ID|-|  
|Group Control Number|Group Control Number|Optional in EDIFACT|  
|-|Interchange Direction = Receive|Required in preserved interchange scenario for uniqueness|  
|Record Type|Functional ACK Status|-|  
  
 The data stored includes:  
  
-   Record Type = Functional ACK Status  
  
-   Functional ACK Direction = Send – Existing Data  
  
-   Functional ACK Status = Sent/Processed – Update Data  
  
-   Interchange Receiver =  Existing Data  
  
-   Interchange Sender = Existing Data  
  
-   Interchange Date = Existing Data  
  
-   Interchange Control ID = Existing Data  
  
-   Group Control Number = Existing Data  
  
-   Functional ID Code = Existing Data  
  
-   Count of Transaction Sets = Existing Data  
  
-   Functional ACK Interchange Control ID= Update Data  
  
-   Functional ACK Interchange Date = Update Data  
  
-   Functional ACK Interchange Time = Update Data  
  
-   Count of Transaction Sets Received = Existing Data  
  
-   Count of Transaction Sets Accepted = Existing Data  
  
-   ACK/Action Code = Existing Data  
  
-   Error/Syntax Error Code  = Existing Data  
  
-   Additional X12 ACK Error Code 2 = Existing Data  
  
-   Additional X12 ACK Error Code 3 = Existing Data  
  
-   Additional X12 ACK Error Code 4 = Existing Data  
  
-   Additional X12 ACK Error Code 5 = Existing Data  
  
## See Also  
 [How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [How Data Is Stored for Outbound EDI Messages](../core/how-data-is-stored-for-outbound-edi-messages.md)
