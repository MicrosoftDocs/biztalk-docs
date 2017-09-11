---
title: "Structure of a Flat File Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00f2adf6-a47c-498b-b5ae-c6bd55bafceb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Structure of a Flat File Message
In the context of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a flat file instance message is a text file that can contain three logical parts: a header, a body, and a trailer, in that order. Both the header and the trailer are optional. The following example shows a flat file instance message that consists of all three parts, with the body shown in bold type.  
  
```  
Microsoft Corporation  
One Microsoft Way  
Redmond, WA 98033  
  
TRANSACTION-1111,1  
  
```  
  
 For the flat file disassembler to correctly distinguish the header, the body, and the trailer of a flat file instance message, you must create and configure a separate schema for each of them.  
  
 Within a particular part of a flat file instance message, different items of data are grouped into records, which themselves can contain subrecords and ultimately the individual items of data, known as fields. These records and fields are distinguished from each other using one of two different basic methodologies. The first methodology, known as positional, defines each item of data to be of a pre-established length, with pad characters being used to bring a shorter item of data up to its expected length. The second methodology, known as delimited, uses one or more special characters to separate items of data from each other. This methodology avoids the need for otherwise superfluous pad characters, but introduces some special considerations when the data itself contains the character or sequence of characters being used as a delimiter.  
  
 The remainder of this section provides a high-level overview of how BizTalk Server handles headers, bodies, and trailers in flat file instance messages, and specifically, how it decides whether the optional parts are present, and how it separates the parts of inbound flat file instance messages and combines the parts of outbound flat file instance messages. This section also provides additional information about the differences between flat file instance messages that employ positional records and fields and flat file instance messages that employ delimited records and fields.  
  
## In This Section  
  
-   [Flat File Message Headers](../core/flat-file-message-headers.md)  
  
-   [Flat File Message Bodies](../core/flat-file-message-bodies.md)  
  
-   [Flat File Message Trailers](../core/flat-file-message-trailers.md)  
  
-   [Flat File Messages with Positional Records](../core/flat-file-messages-with-positional-records.md)  
  
-   [Flat File Messages with Delimited Records](../core/flat-file-messages-with-delimited-records.md)  
  
-   [Migrating Flat File Records](../core/migrating-flat-file-records.md)