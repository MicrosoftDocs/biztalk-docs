---
title: "Calling Static SQL for DB2 Custom Packages | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe07d0e6-95e8-4da3-aff7-a3042bd70be5
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Calling Static SQL for DB2 Custom Packages
## Package Naming Convention  
 DRDA defines a fully-qualified static SQL package using a PKGNAM (RDB Package Name) that consists of these multiple parts.  
  
- RDBNAM (Relational Database Name)  
  
- RDBCOLID (RDB Collection Identifier)  
  
- PKGID (RDB Package Identifier)  
  
  `RDBNAME.RDBCOLID.PKGID.PKGCNSTKN.PKGSN`  
  
  *Fully-qualified package name with consistency token.*  
  
> [!NOTE]
>  If more than one package has the same value for PKGNAM, then the packages are distinguished by the VRSNAM (Version Name) or PKGCNSTKN (package name consistency token).  
  
-   PKGCNSTKN (RDB Package Consistency Token)  
  
-   VRSNAM (Version Name)  
  
## Executing Static SQL Statements  
 You can use ADO.NET Command and Parameter objects to execute static SQL statement using an EXEC STATIC syntax referencing the fully-qualified package name.  
  
 `EXEC STATIC RDBNAME.RDBCOLID.PKGID.PKGCNSTKN.PKGSN`  
  
 *Command syntax for executing static SQL statement, using fully-qualified package name.*  
  
 Optionally, you can use ADO.NET Command and Parameter objects to execute static SQL statement using a CALL syntax referencing the package alias name.  
  
 `CALL RDBNAME.RDBCOLID.PKALIAS.PKGSN`  
  
 *Command syntax for executing static SQL statement, using package alias name.*  
  
> [!NOTE]
>  When binding the package, you must specify a value for Alias (V85) or packageSectionAlias (V90).  
  
## Static SQL Result Set Metadata  
 The Microsoft DRDA Client can use early metadata or late metadata to interpret the resultset columns.  
  
### Result Set using Early Metadata  
 You can use early metadata specified in the package XML to define the result set columns (data types, encoding). First, specify one or more Column elements in the Result Set element. Second, set the MsDb2Client connection property Use Early Metadata to true. Third, load the static SQL for DB2 package XML file using the MsDb2Client property.  
  
### Result Set using Late Metadata  
 You can use late metadata returned by the DRDA Server to define the result set columns (data types, encoding), by setting the MsDb2Client connection property Use Early Metadata to false.