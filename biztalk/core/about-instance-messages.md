---
title: "About Instance Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de7fc3d3-57a7-4df9-b981-127e21941e22
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About Instance Messages
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends and receives instance messages, each of which typically represents one or more business documents such as a purchase order. An instance message is an instance of a message structure defined by one or more schemas. A schema, or a set of schemas being used together, defines what constitutes a valid instance message. For example, a purchase order might be defined to have several records within it, such as a ShipTo record, a BillTo record, an Items record, and so on. Each of these records can be defined to contain their own subrecords and fields. The corresponding schema defines the potential contents of these records and fields and the corresponding instance messages contain actual purchase orders that contain purchase order data structured according to the schema.  
  
 BizTalk Server can send and receive instance messages in an extensible variety of formats although one format, XML, has special significance as the format into which all message formats are translated for internal processing. A particular XML document uses a well-defined set of starting and ending tags, arranged hierarchically, to organize the data within the message and determine where one data item ends and another begins. One or more corresponding XML schemas define which tags are allowed within other tags, in what order, thereby governing the structure of conforming messages.  
  
 Another broad category of formats, known as flat file formats, are commonly used by legacy systems. These formats use some combination of delimiters (such as tabs) and fixed length fields to determine where one data item ends and another begins.  
  
 This section provides a high-level overview of the structure of these two types of messages that are commonly handled by BizTalk Server.  
  
## In This Section  
  
-   [Structure of an XML Message](../core/structure-of-an-xml-message.md)  
  
-   [Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md)