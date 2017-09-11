---
title: "Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, schema types"
  - "deploying, schemas"
  - "schemas"
  - "schemas, about schemas"
  - "property schemas"
  - "envelope schemas"
  - "schemas, deploying"
  - "XML schemas"
  - "flat file schemas"
ms.assetid: aea772bd-e7ab-448e-ba82-e7c8f38087db
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schemas
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the XML Schema definition (XSD) language to define the structure of all messages that it processes, and refers to these definitions of message structure as *schemas*. With few exceptions, structured messages are the core of any application. These structured messages can take any form, large or small, and target a wide array of back-end systems and data stores. Systems that create and consume the structured messages frequently use different formats. Two of the most common formats for structured messages are XML and flat files.  
  
 BizTalk Server supports the following four types of schemas:  
  
-   XML schema. An XML schema defines the structure of a class of XML instance messages. Because this type of schema uses XML Schema definition (XSD) language to define the structure of an XML instance message, and this is the intended purpose of XSD, such schemas use XSD in a straightforward way. For more information about XML schemas, see [XML Schemas](../core/xml-schemas.md).  
  
-   Flat file schema. A flat file schema defines the structure of a class of instance messages that use a flat file format, either delimited or positional or some combination thereof. Because the native semantic capabilities of XSD do not accommodate all of the requirements for defining the structure of flat file instance messages—such as the various types of delimiters that might be used for different records and fields within the flat file—BizTalk Server uses the annotation capabilities of XSD to store this extra information within an XSD schema. BizTalk Server defines a rich set of specific annotation tags that can be used to store all of the required additional information. For more information about flat file schemas, see [Flat File Schemas](../core/flat-file-schemas.md).  
  
-   Envelope schema. An envelope schema is a type of XML schema. Envelope schemas are used to define the structure of XML envelopes, which are used to wrap one or more XML business documents into a single XML instance message. When you define an XML schema to be an envelope schema, additional property settings are required, depending on such factors as whether there are more than one root record defined in the envelope schema. For more information about Envelope schemas, see [Envelope Schemas](../core/envelope-schemas.md).  
  
-   Property schema. A property schema is used with one of the two mechanisms that exist within BizTalk Server for property promotion. *Property promotion* is the process of copying specific values from deep within an instance message to the message context. From the message context, these values are more easily accessed by various BizTalk Server components. These components use the values to perform actions such as message routing. Promoted property values can also be copied in the other direction, from the more easily accessible message context back into the depths of the instance message, just before the instance message is sent to its destination. A property schema, which is a simple version of a BizTalk schema, plays a role in the process of copying promoted properties back and forth between the instance message and the message context. For more information about property schemas, see [Property Schemas](../core/property-schemas.md).  
  
## Schema Deployment  
 You deploy different types of schemas, such as message schemas, property schemas, and envelope schemas. Because each schema is different, there are small differences in how they are handled after deployment. This section addresses what is common to all schemas, and also describes the differences relating to the types of schema.  
  
 When you deploy a schema, the Management database stores the contents of the schema. You can deploy multiple schemas with the same target namespace. BizTalk Server explicitly points to the schema in the Pipeline Designer that is used at run time. If you use default pipelines, or if you do not specify a schema in the Pipeline Designer, and if multiple versions of the same schema have been deployed, BizTalk Server determines the schema to use. In this case, it will be the schema associated with the most recent version—with the highest version number—of the assembly deployed using that schema.  
  
 When you remove the most recent version of the assembly that deployed a schema, the schema from the highest previous version of the same assembly becomes the active schema.  
  
 If you deploy schemas with duplicate target namespaces, you must reference a schema from a custom-designed user pipeline. This gives the Messaging Engine additional information to be able to load the right schema.  
  
 For example, one case where you would use a duplicate target namespace is when you create multiple versions of a Web Service schema.  
  
## See Also  
 [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md)   
 [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md)   
 [Artifacts](../core/artifacts.md)