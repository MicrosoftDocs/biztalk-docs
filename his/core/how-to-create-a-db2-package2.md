---
title: "Create a DB2 Package | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fc88244-c762-4c3f-a638-cb9882f115bc
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Create a DB2 Package

## Overview
A DB2 package is a collection of data used by a provider implemented as an IBM Distributed Relational Database Architecture (DRDA) application requester. The provider uses packages to issue SQL statements and call DB2 stored procedures. You can use `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.CreatePackages%2A` to create these packages.  
  
 The create package command creates a Host Integration Server package on a DB2 system.  
  
## Create a DB2 package  
  
1. Create a connection string to the targeted database with a call to `Microsoft.HostIntegration.DataAccessLibrary.DB2OleDbConnectionString.ReadUDL%2A`.  
  
2. Create the package with `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.CreatePackages%2A`.  
  
   The following example describes how to create a package.  
  
```  
static void CreatePackage(string myUDL, System.Exception myException)  
{  
try  
   {  
      IConnectionString connString = DB2OleDbConnectionString.ReadUDL(myUDL);  
      DataAccessControl.CreatePackages(connString, null);  
      myException = null;  
   }  
catch (System.Exception Caught)  
   {  
      myException = Caught;  
   }  
}  
```  
