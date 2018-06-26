---
title: "Schema Migration from Previous Versions of BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bdc86401-2002-40b8-a919-2c00cf42b557
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Migration from Previous Versions of BizTalk Server
This version of BizTalk Server uses XML Schema definition (XSD) language to represent message schemas, while previous versions used the XML-Data Reduced (XDR) syntax to represent message schemas. If you are migrating from a previous version of BizTalk Server, you must convert your schemas to use XSD rather than XDR.  
  
 You need to perform the following tasks to convert a BizTalk schema from XDR syntax to XSD syntax:  
  
- Change the extension of the schema file from.xdr to.xsd.  
  
- Add the renamed schema to the appropriate BizTalk project.  
  
- Convert the renamed schema from XDR to XSD by opening the schema in BizTalk Editor.  
  
- Make the conversion permanent by saving the schema.  
  
  For detailed information about how to perform these steps, see [How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md).  
  
## See Also  
 [About Schemas](../core/about-schemas.md)   
 [How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md)   
 [Migrating Flat File Records](../core/migrating-flat-file-records.md)