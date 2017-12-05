---
title: "Specifying a File Name for Table G for Code Conversion | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0aa962a-f57f-42f0-8b86-55f822b21fd9
caps.latest.revision: 4
---
# Specifying a File Name for Table G for Code Conversion
The sample emulators use a user-defined table referred to as Table G in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] for converting between ASCII and EBCDIC characters. The sample applications require that the file name of this table be specified. Use the COMTBLG registry or create a COMTBLG environment variable to specify the file name. The registry entry is described in the sections on Host Integration Server Client Binary Setup.  
  
 A sample Table G file, COMTBLG.DAT, is installed with Host Integration Server in the SYSTEM subdirectory below the root directory where the product is installed. The default location where Host Integration Server is installed is the following:  
  
 C:\Program Files\Microsoft Host Integration Server 2010  
  
 To use this COMTBLG.DAT file, copy it to the client computers where the sample programs will be run, and specify the file name using the COMTBLG environment variable or the registry entry.  
  
## See Also  
 [LUA Samples](../core/lua-samples.md)