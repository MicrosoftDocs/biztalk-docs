---
description: "Learn more about: Nested XML Message Envelopes"
title: "Nested XML Message Envelopes"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Nested XML Message Envelopes
XML envelopes can be nested to create complex document structures. Nested XML envelopes can occur in two forms, known as flexible and canonical. The following example shows the flexible form of enveloped documents, in which documents and envelopes (shown in bold type) can appear at the same level within an enclosing envelope.  
  
```  
<envelope1>  
    <document1/>    <envelope2>  
        <document2/>  
        <document3/>  
    </envelope2>    <document4/>  
</envelope1>  
```  
  
 The following example shows a similar instance message that conforms to the canonical form of enveloped documents, in which all documents appear at the same level within the innermost envelope.  
  
```  
<envelope1>  
    <envelope2>  
        <document1/>  
        <document2/>  
        <document3/>  
        <document4/>  
    </envelope2>  
</envelope1>  
  
```  
  
 Given an instance message in either of the forms described, the XML disassembler will produce document1, document2, document3, and document4. The message context of each of these documents includes the properties promoted from the corresponding document as well as the properties promoted within each of the enclosing envelopes. The following table shows the promoted properties that will be include in the message context of each unwrapped documents for both the flexible and canonical examples, given the property promotions specified in the first column for the various envelopes and documents.  
  
|Specified property promotions|Resulting message context properties for flexible example|Resulting message context properties for canonical example|  
|-----------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|  
|envelope1: p1<br /><br /> envelope2: p3<br /><br /> document1: p2<br /><br /> document2: p4 and p5<br /><br /> document3: no promotions<br /><br /> document4: no promotions|document1: p1, p2<br /><br /> document2: p1, p3, p4, p5<br /><br /> document3: p1, p3<br /><br /> document4: p1|document1: p1, p2, p3<br /><br /> document2: p1, p3, p4, p5<br /><br /> document3: p1, p3<br /><br /> document4: p1, p3|  
  
## See Also  
 [XML Message Envelopes](../core/xml-message-envelopes.md)   
 [Structure of an XML Message](../core/structure-of-an-xml-message.md)   
 [How to Create Schemas for Envelopes](../core/how-to-create-schemas-for-envelopes.md)
