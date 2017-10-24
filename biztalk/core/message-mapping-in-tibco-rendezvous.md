---
title: "Message Mapping in TIBCO Rendezvous | Microsoft Docs"
description: Message fields and message mapping to XML in the BizTalk Adapter for TIBCO Rendezvous
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62793bec-f076-425c-b25e-c4be5bd93cc8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Mapping in TIBCO Rendezvous
TIBCO Rendezvous messages are composed of header information and a set of message fields. The header information is directly mapped to message context properties.  
  
## Message Field Elements  
 A message field is composed of the following elements:  
  
|Element|Description|  
|-------------|-----------------|  
|**Name**|Character string. Does not have to be unique in a message.|  
|**Identifier**|Short integer. Unique in a message. Implicitly limits the number of message fields to 65535. The scope of the identifier is the message (or sub message). The same identifier can be used in two sub-messages, which are themselves part of a containing message.|  
|**Value**|The message field data.|  
|**Count**|Number of items (in the case of an array)|  
|**Type**|The type of the message field.|  
  
### Mapping Process  
 TIBCO Rendezvous structured messages are mapped to XML elements in the following way:  
  
-   **Name** is used as the element name. The TIBCO Rendezvous field name may contain characters that are not valid for use in XML element names. The adapter generates valid character mappings between XML and TIBCO Rendezvous structured messages.  
  
-   **Identifier** is put into an ‘id’ attribute.  
  
-   **Value** contains a string representation that is the body of the element.  
  
-   **Count** is ignored.  
  
-   **Type** information is put into an xsi:type attribute for the generated element.  
  
     For more information, see [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Creating TIBCO Rendezvous Receive Handlers](../core/creating-tibco-rendezvous-receive-handlers.md)