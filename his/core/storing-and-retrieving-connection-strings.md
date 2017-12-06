---
title: "Storing and Retrieving Connection Strings1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c32375ba-b254-4c1a-8479-3f03eac58a8f
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Storing and Retrieving Connection Strings
We recommend that you not embed connection strings in your code. If the location of the server ever changes, your application must be recompiled. In addition, unencrypted connection strings that are compiled into an application's source code can be viewed using the MSIL Disassembler (ildasm.exe).  
  
 To avoid storing connection strings in your code, you can store them in the web.config file for an ASP.NET application and in the app.config file for a Windows application. Although configuration files are mainly used in ASP.NET applications, where they are protected from being browsed to, you can also use them in a Windows application. The syntax and format of the app.config and web.config files is identical for both ASP.NET and Windows applications.  
  
 The connection string can be stored in the configuration file in the `<connectionStrings>` element. Connection strings are stored as key/value pairs, where the name key can be used to look up the value stored in the `connectionString` attribute at run time.  
  
 You can work with configuration files programmatically by using the `MsDb2Configuration` class. The methods of the `WebConfigurationManager` object also enable you to obtain a configuration section, each of which has its own object type. In addition, the `System.Configuration` namespace provides classes for working with configuration information stored in configuration files.  
  
## Example  
  
## See Also  
 [Working with Connection Strings and the Managed Provider for DB2](../core/working-with-connection-strings-and-the-managed-provider-for-db2.md)