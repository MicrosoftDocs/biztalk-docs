---
description: "Learn more about: Structure of an XML Message"
title: "Structure of an XML Message"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Structure of an XML Message
In the context of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], an XML instance message is a valid hierarchy of XML tags that together constitute zero or more XML envelopes and one or more XML documents. For example, the following XML instance message consists of a single XML envelope (in regular font) that contains a single XML document (shown in bold type).  
  
```  
<ns0:envelope xmlns:ns0="http://myEnvelopeNamespaceURI.org">  
    <header>  
        <firstName>John</firstName>  
        <lastName>Scott</lastName>  
    </header>  
    <body>  
        <ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">            <message>Hello</message>        </ns1:document>  
    </body>  
</ns0:envelope>  
```  
  
 XML envelopes and the XML documents that they contain can be combined into valid XML instance messages in several different ways. The remainder of this section describes these different combinations.  
  
## In This Section  
  
-   [XML Message Envelopes](../core/xml-message-envelopes.md)  
  
-   [Nested XML Message Envelopes](../core/nested-xml-message-envelopes.md)
