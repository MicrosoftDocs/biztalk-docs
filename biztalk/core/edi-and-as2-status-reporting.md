---
title: "EDI and AS2 Status Reporting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9e58b29-9be0-41d6-ad35-1aae28e1a784
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI and AS2 Status Reporting
EDI status reporting enables operations personnel to track the status of EDI and AS2 transmissions. If enabled, status reports provide comprehensive status of a document exchange transaction, including an interchange and any acknowledgments correlated to the interchange. These reports provide data on receipt, validation, batching, and acknowledgment processing of EDI and AS2 messages.  
  
 You can use these reports to get the status of pending and unacknowledged interchanges, complete interchanges, error scenarios, or business scenarios. With these reports, you can do the following:  
  
- Confirm the receipt of interchanges  
  
- List outgoing interchanges awaiting acknowledgment  
  
- List all rejected interchanges received  
  
- List outgoing interchanges that are reported as rejected or partially accepted.  
  
  Data included in the status reports is obtained from interchange control segments, such as ISA, TA1, GS, UNB, and UNG (with the exception of the Functional ACK status).  
  
  **Status Reporting UI**  
  
  EDI and AS2 status reports are available from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. From the **Group Hub** page of the **BizTalk Group** node, you have links to EDI interchange and correlated acknowledgment status, batch status, and AS2 message and correlated MDN status. Each of these reports provides a range of status parameters that you can include or exclude from a query expression, enabling you to build the status report that they need.  
  
  In addition to seeing the status of an EDI interchange, you can also view the transaction sets in an interchange. You do so by enabling the storage of message payloads in the EDI tables of the tracking (BizTalkDTADb) database. You can view the transaction sets by using the view details command in the status reporting UI.  
  
  You can also store inbound or outbound AS2 messages or MDNs in the non-repudiation database. You can view the transaction sets or AS2 messages by right-clicking the message in the status report and selecting the appropriate command.  
  
  **Status Report Components**  
  
  The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components involved in status reporting are the following:  
  
- The EDI Disassembler in the EDI receive pipeline that creates and updates status entries in the data store for an incoming interchange  
  
- The EDI Assembler in the EDI send pipeline that creates and updates status entries in the data store for an outgoing interchange  
  
- The data stores that store the status report entries. These are the BAM Primary Import database for tracking data and the EDI Message Content table of the BizTalk tracking database (BizTalkDTADb) for EDI transaction sets and/or AS2 message contents  
  
- Status reporting UI on the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, which is used to display status reporting data  
  
- Agreement property and fallback agreement property options in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, which is used to enable and configure status reporting  
  
- DTA and SQL Analysis Server that leverage the BAM infrastructure.  
  
## In This Section  
  
-   [Configuration of EDI and AS2 Status Reporting](../core/configuration-of-edi-and-as2-status-reporting.md)  
  
-   [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md)  
  
-   [Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md)  
  
-   [How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)