---
title: "Different Types of BizTalk Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad8847d3-6f0e-4982-b4a8-92a5f39a4b48
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Different Types of BizTalk Schemas
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports the following four types of schemas:  
  
- **XML schema**. An XML schema defines the structure of a class of XML instance messages. Because this type of schema uses XML Schema definition (XSD) language to define the structure of an XML instance message, and this is the intended purpose of XSD, such schemas use XSD in a straightforward way.  
  
- **Flat file schema**. A flat file schema defines the structure of a class of instance messages that use a flat file format, either delimited or positional or some combination thereof. Because the native semantic capabilities of XSD do not accommodate all of the requirements for defining the structure of flat file instance messages—such as the various types of delimiters that might be used for different records and fields within the flat file—BizTalk Server uses the annotation capabilities of XSD to store this extra information within an XSD schema. BizTalk Server defines a rich set of specific annotation tags that can be used to store all of the required additional information.  
  
- **Envelope schema**. An envelope schema is a special type of XML schema. Envelope schemas are used to define the structure of XML envelopes, which are used to wrap one or more XML business documents into a single XML instance message. When you define an XML schema to be an envelope schema, a couple of additional property settings are required, depending on such factors as whether there are more than one root record defined in the envelope schema.  
  
- **Property schema**. A property schema is used with one of the two mechanisms that exist within BizTalk Server for what is known as property promotion. Property promotion is the process of copying specific values from deep within an instance message to the message context. From the message context, these values are more easily accessed by various BizTalk Server components. These components use the values to perform actions such as message routing. Promoted property values can also be copied in the other direction, from the more easily accessible message context back into the depths of the instance message, just before the instance message is sent to its destination. A property schema is a simple version of a BizTalk schema that plays a role in the process of copying promoted properties back and forth between the instance message and the message context.  
  
  The remainder of section provides additional information about these four types of schemas in BizTalk Server.  
  
## In This Section  
  
-   [XML Schemas](../core/xml-schemas.md)  
  
-   [Flat File Schemas](../core/flat-file-schemas.md)  
  
-   [Envelope Schemas](../core/envelope-schemas.md)  
  
-   [Property Schemas](../core/property-schemas.md)