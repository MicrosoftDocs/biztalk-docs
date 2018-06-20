---
title: "Message References in User Code | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a1584be-35fd-4dc2-a5a9-559300e67e0e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message References in User Code
When a message is constructed, a representation of the message is in the MessageBox database and another representation is in memory on the computer. If you make the message assignment by passing a message reference to a .NET object or to an external assembly, and then the .NET object or the external assembly modifies the representation in memory on the computer, the BizTalk Orchestration Engine is not aware of the modification.  
  
 Moreover, the orchestration engine does not invalidate the message part data that is in the representation in the MessageBox database. Message part data has the following modes of representation:  
  
- XmlDocument representation  
  
- Object representation  
  
- Stream representation  
  
- UnderlyingPart representation  
  
  How the message part data is represented in memory depends on the message construction and whether the type is a .NET class or an XML Schema definition language (XSD) schema. However, the UnderlyingPart representation is always a stream pointing into the MessageBox database. Because messages in BizTalk Server are immutable after the message is committed to the MessageBox database, the orchestration engine uses the representation in the MessageBox database to reference message part data.  
  
> [!NOTE]
>  A constructed message may already have a representation in the MessageBox database if you assign parts from a message that is already committed.  
  
 For example, the following code sends the UnderlyingPart data from the representation in the MessageBox database:  
  
```  
// In this example, assume m1 is committed to the MessageBox  
Construct m2 {   
               m2 = m1; // m2’s part data representation is the UnderlyingPart data of m1  
               m2(myContextProperty) = “123”; // m2’s part data representation is still the UnderlyingPart data of m1  
               A.test(m2.part); // orchestration engine does not invalidate the UnderlyingPart MessageBox representation  
             }  
Send(p.o, m2);  
```  
  
 Instead of using the preceding user code, you can use code that is similar to the following to return an XmlDocument document to a Message XLANG variable:  
  
```  
Void A.test(ref XmlDocument xd) {…}  
XmlDocument B.test(XmlDocument xd) {…}  
construct m2 {  
               m2 = m1;  
               m2(myContextProperty) = “123”; // m2’s part data representation is the UnderlyingPart data of m1  
               A.test(ref m2.part); // orchestration engine has enough information to know it has to invalidate the UnderlyingPart MessageBox representation  
               // or  
               m2.part = B.test(m2.part); // orchestration engine has enough information to know it has to invalidate the UnderlyingPart MessageBox representation  
             }  
```