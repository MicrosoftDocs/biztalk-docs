---
title: "Snacfg PrintServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb328695-71d1-4e2a-b139-ce953f5c6392
caps.latest.revision: 4
---
# Snacfg PrintServer
## Purpose  
 Allows you to add, delete, or view printer servers from one subdomain or multiple subdomains.  
  
> [!NOTE]
>  Configuration settings specified with snacfg printserver correspond to settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
[configpath]  [configpath] servername [configpath] servername  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of print servers in the Host Integration Server subdomain.  
  
 **/add**  
 Adds the print server name of the Host Integration Server computer that is running the Host Integration Server Host Print Service. To configure the server name, specify the name after the **/add**. The print server name must match the computer name of the computer running Host Print Service.  
  
 You can add print servers for Host Integration Server computers that do not yet exist. For example, you can prepare a configuration file to be used at another location and add the server names using this parameter. Until the computers are configured with Host Integration Server running Host Print Service, SNA Manager will show them as offline.  
  
 **/delete**  
 Deletes the print server.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference.md)