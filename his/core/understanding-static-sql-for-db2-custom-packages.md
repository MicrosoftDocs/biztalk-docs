---
title: "Understanding Static SQL for DB2 Custom Packages | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc8e1003-2b98-4552-9559-2de9d62b7a5e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Understanding Static SQL for DB2 Custom Packages
Distributed Relational Database Architecture (DRDA) supports two methods of defining SQL statements for execution against a remote IBM DB2 DRDA server. First, the DRDA AR can dynamically-define SQL statements at runtime, using the DRDA commands EXCSQLIMM (Execute Immediate SQL Statement) or EXCSQLSTT (Execute SQL Statement). Second, the DRDA AR can statically-define SQL statements at bind time, using the DRDA commands BGNBND (Begin Binding a Package to an RDB) and BNDSQLSTT (Bind SQL Statement to an RDB Package). All Microsoft HIS data providers for DB2 support executing CREATE CURSOR statements within the standard set of Microsoft static SQL packages for DB2 used to return results on SELECT and CALL statements. See Deployment book for information on defining the standard set of packages. Only the Microsoft ADO.NET Framework Data Provider for DB2 supports executing statements within custom-defined static SQL packages for DB2, which are created using the Microsoft.HostIntegration.DataAccessLibrary DataAccessControl.CreateCustomPackage interface. The developer can write a program to execute the CreateCustomPackage interface or can use the Visual Studio 2012 Server Explorer to reference an XML file and create the package. Using Visual Studio 2012 or another XML editor, the enterprise developer creates a Microsoft static SQL for DB2 package XML file, which contains elements that specify the bind options, package(s), statement(s), optional parameter(s) and result set(s). The DRDA AR client converts the static SQL for DB2 package XML file into a DRDA BGNBND with one or more BNDSQLSTT protocol flows.  
  
> [!NOTE]
>  The Microsoft DRDA AR client cannot execute static SQL for DB2 packages that are not defined using the Microsoft DAL DAC interface.