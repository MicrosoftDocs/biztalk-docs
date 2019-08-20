---
title: "XML Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93bccb6e-48c2-4dfe-bcf6-cb0eb032327b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# XML Support
A `DataSet` object can persist and reload its contents as XML and its schema as XSD. The `DataSet` has direct support for reading (shredding) and writing data using XML using the .NET Framework `XmlReader` and `XmlWriter` classes. When you are writing XML, the output conforms to the W3C XSD schema. XML is a good method of moving data between application tiers. The `XMLDataDocument` can use the XML services, such as XSL/T and XPath.  
  
## See Also  
 [ADO.NET DataSet for Host Integration Server](../core/ado-net-dataset-for-host-integration-server2.md)   
 [Managed Provider Programmer's Guide](../core/managed-provider-programmer-s-guide2.md)