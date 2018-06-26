---
title: "Data provider properties for the Siebel connection string | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conncting, to the Siebel system"
  - "Data Provider for Siebel, connection string"
ms.assetid: 8ab0c29e-e06b-4e74-be4e-9aa862a05539
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data provider properties for the Siebel connection string
The [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) uses the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to access the Siebel system. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in turn uses the Siebel COM Data Control library to access the Siebel system. The Siebel COM Data Control comes bundled with the Siebel Web client.  

 To establish connectivity to a Siebel system, ADO.NET clients must specify the Siebel connection properties that are encoded into a database connection string. This is required because the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implements **DbConnection** to access the underlying [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding.  

 The connection string to connect to a Siebel system using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] contains the following properties.  


|        Property        |                                                                                                                                                     Description                                                                                                                                                      |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Password        |            The password for the user on the Siebel system; this value is case-sensitive. **Note:**  The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Siebel system.             |
|        Username        |                  The user name on the Siebel system; this value is case-sensitive. **Note:**  The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Siebel system.                  |
|      Compression       |      The compression algorithm to use between the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] and the Siebel system. Supported values are **none** or **zlib**. This parameter is optional. If it is not specified, the Siebel system supplies a default value (**zlib**).       |
|       Encryption       | The type of encryption to use between the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] and the Siebel system. Supported values are **none**, **mscrypto**, or **rsa**. This parameter is optional. If it is not specified, the Siebel system supplies a default value (**none**). |
|        Language        |                                                                                                             The language of the object manager. An example value is **enu**. This parameter is required.                                                                                                             |
| SiebelEnterpriseServer |                                                                                                                        The name of the Siebel Enterprise Server. This parameter is required.                                                                                                                         |
|     SiebelGateway      |                                                                                                                     Consists of the Siebel server IP and port. For example, Siebel_Server:1234.                                                                                                                      |
|  SiebelObjectManager   |                                                                                                             The name of the Siebel object manager on the enterprise server. This parameter is required.                                                                                                              |
|    SiebelRepository    |                                     The Siebel repository. Required if more than one repository exists on the server; otherwise, optional. **Note:**  If more than one repository exists on the server, you must specify a target repository in the SiebelRepository parameter.                                      |
|      SiebelServer      |                                                                                                       The Siebel server. Required for all Siebel 7.5 server connections; otherwise, do not set this parameter.                                                                                                       |
|       Transport        |                                                                               The transport; only **tcpip** is supported. This parameter is optional. If it is not specified, the Siebel system supplies a default value (**tcpip**).                                                                                |

 For example:  

```  
Username=YourUserName;Password=YourPassword;SiebelGateway=Siebel_Server:1234;SiebelObjectManager=obj_mgr;SiebelEnterpriseServer=ent_server;Language=enu;SiebelRepository=siebel_rep  
```  

## See Also  
 [Use the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)