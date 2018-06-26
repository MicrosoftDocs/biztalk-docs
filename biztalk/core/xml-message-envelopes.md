---
title: "XML Message Envelopes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d01cd85d-7bf7-49fa-aa25-322213bce066
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Message Envelopes
XML envelopes serve two purposes within XML instance messages sent and received by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
- XML envelopes can contain data that supplements the data within the XML documents. This data can be promoted into the message context by the XML disassembler to provide easier access from a variety of BizTalk Server components. For outbound XML instance messages, the XML assembler can demote values from the message context into an envelope for inclusion in the instance message transmission.  
  
- XML envelopes can be used to combine multiple XML documents into a single, valid XML instance message. Without an envelope to wrap multiple documents within a single root tag, an XML instance message containing multiple documents would not qualify as well-formed XML.  
  
  A typical XML envelope (shown in bold type) contains both data and a tag used to delimit the one or more XML documents (shown in regular font) that it contains.  
  
```  
  
  <envelope fieldAttrib1="..." fieldAttrib2="..." ...>     <fieldElem1>...</fieldElem1>     <fieldElem2>...</fieldElem2>     ...     <body>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</body>    ...</envelope>  
```  
  
 Less common, but still valid, an XML envelope (shown in bold type) need not contain any data or a tag for delimiting the XML documents (shown in regular type) that it contains.  
  
```  
  
      <envelope>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</envelope>  
```  
  
 In such cases, the XML envelope consists of nothing other than the starting and ending envelope tags.  
  
## See Also  
 [Nested XML Message Envelopes](../core/nested-xml-message-envelopes.md)   
 [Structure of an XML Message](../core/structure-of-an-xml-message.md)   
 [How to Create Schemas for Envelopes](../core/how-to-create-schemas-for-envelopes.md)