---
title: "Limitations When Querying and Retrieving Lists | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JD Edwards OneWorld adapters, querying limitations"
  - "querying, limitations [JD Edwards OneWorld adapters]"
ms.assetid: 1b6f5d2a-d1e2-4c78-8f4a-f00d10f008b9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Limitations When Querying and Retrieving Lists
The JD Edwards OneWorld communication architecture is a single-message, single-reply architecture. You cannot return a list of messages or an array. The underlying code is C++, which calls with a pointer to a single structure, makes changes in the structure, and then exits.  
  
## Querying and Retrieving Lists  
 You cannot query and retrieve lists of records based on search criteria using Microsoft BizTalk Adapter for JD Edwards OneWorld due to a limitation with the JD Edwards OneWorld business function architecture.  
  
 In JD Edwards OneWorld, database connectivity is provided by using a set of proprietary (and complex) internal function calls. These calls mask the underlying database version by requiring very explicit and low-level calls to create lists of columns to retrieve or update, and create specialized structures for sorting or selection. The sets of APIs are not exposed through the Java (or any other) connectivity method; therefore, record sets cannot be handled through business functions.  
  
 Within the JD Edwards OneWorld toolset, you can create business functions that handle a single record or operate on a group of records; however, accessing lists of items outside the JD Edwards OneWorld tools is more difficult.  
  
 To work around this issue, you can create a custom business function that returns a list of record keys based on a query. You must segment the lists, because JDENET (the JD Edwards OneWorld internal proprietary messaging API) has a limitation on the message buffer size for managing large or unbounded result sets. The client code must iterate (loop) through successive calls to the business function, until an indicator is returned stating that the list is complete.  
  
## Controlling Iteration  
 All calls to JD Edwards OneWorld business functions are stateless; therefore, the business function cannot maintain an open cursor and return more rows on request. Positioning information must be passed to the JD Edwards OneWorld XE business function on each call.  
  
 The following is a list of techniques for controlling iteration:  
  
- On the JD Edwards OneWorld side, write the result set to a temporary storage file, which returns an ID (such as a file name or job number) that can be given on successive calls, along with the record number to position the cursor. Any successive call is positioned within the list based on the passed-in record number.  
  
  > [!NOTE]
  >  Calls through BizTalk Adapter for JD Edwards OneWorld can be load-balanced; however, they are eventually served by a single application server based on the credentials and business function being called. Therefore, if a call creates a temporary file on a server, additional calls are served by the same server. For more information, see Object Configuration Mapping in the JD Edwards OneWorld CNC Guides.  
  
- Position information (such as a primary key value) can be returned on the second and subsequent calls, and the query can be reissued based on the key as an additional parameter. This method is used in the repository browsing code for BizTalk Adapter for JD Edwards OneWorld.  
  
  > [!NOTE]
  >  Of the first two techniques, the recommended method is to use primary key values and reissue the query. This method requires the smallest amount of code and places the optimization and caching burden on the database.  
  
- The calling application can store a list of primary keys (such as a cross reference). For example, if a customer relationship management (CRM) system creates a customer record and then adds it to JD Edwards OneWorld using a business function call, the business function that adds a customer record sets the value for the AN8 field (short address number) and is visible in the return buffer. This number can then be written to a reference field on the original customer record, or stored into a customized cross-reference table.  
  
- The majority of all master records in JD Edwards OneWorld have a concept of a lookup, or alternate key. This key can be used to store the key information from the calling system. Business functions can perform the lookup on the JD Edwards OneWorld side. When parameters are passed to the business function to create a customer record, the long key value is set.  
  
  For more information on these concepts, see the Interoperability topic in the JD Edwards OneWorld Help system.  
  
## See Also  
 [Planning and Architecture](../core/planning-and-architecture17.md)