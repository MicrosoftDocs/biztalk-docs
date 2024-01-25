---
description: "Learn more about: Static SQL Package XML"
title: "Static SQL Package XML"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Static SQL Package XML
Microsoft HIS 2013 (V9) supports both an old and new format, which includes an associated XML schema for validating the XML document. Microsoft HIS 2009 and HIS 2010 (V8.5) support the old format only.  
  
 The Microsoft static SQL for DB2 custom package XML file contains multiple elements to inform the DRDA Client and DRDA Server how to execute the DRDA commands BGNBND (Begin Binding a Package to an RDB) and BNDSQLSTT (Bind SQL Statement to an RDB Package). This topic describes the XML elements that you can define to describe the static SQL package bind options, package name, package sections, statements, parameters, and result sets.
