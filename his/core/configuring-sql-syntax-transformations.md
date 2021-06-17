---
description: "Learn more about: Configure SQL Syntax Transformations"
title: "Configure SQL Syntax Transformations | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44d13965-dfd6-425b-a16c-4652bfb5334b
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configure SQL Syntax Transformations
The DRDA Service will utilize a set of SQL command syntax transformers. The primary SQL transformer is within the MsDrdaService.exe and is referred to as the SQL parser, providing core transformations for most commonly required syntax. The secondary SQL transformer is within the SQL Server database .NET CLR (Common Language Runtime), where the MsDrdaService setup program will install optional DB2 to SQL Server mapped functions. The DRDA Service supports **STRIP**, **TRANSLATE**, **HEX**, and **CHAR** mapped CLR functions.  
  
## SQL Transformer  
 The **sqlTransforms** attribute instructs the DRDA Service to utilize internal service or external CLR-based SQL transforms. This **optional** attribute accepts a **string** value of **Service** or **Clr**. The default value is **Service**.  
  
> [!NOTE]
>  To enable SQL Server CLR Integration, execute the following stored procedure.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 *SQL Server stored procedure to enable CLR integration.*  
  
 For more information, see [CLR Integration - Enabling](/sql/relational-databases/clr-integration/clr-integration-enabling).  
  
## SQL Transformer Unicode Output  
 The SQL Transformer will output NCHAR and NVARCHAR for all string values. The `sqlTransformsUnicodeOutput` attribute instructs the DRDA Service to encode output from the CLR-based SQL transformer in Unicode or ANSI. This `optional` attribute accepts a `Boolean` value. The default value is `false`, which instructs the DRDA Service to output `ANSI CHAR` and `VARCHAR` strings.