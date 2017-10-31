---
title: "Snacfg TNIPID1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 152dda2d-4ded-4af1-89b9-b932e3572429
caps.latest.revision: 4
---
# Snacfg TNIPID
## Purpose  
 Allows you to view, add, delete, or modify telnet IP (Internet Protocol) addresses. the SNA Manager is the recommended interface for adding TNIPIDs.  
  
> [!NOTE]
>  Configuration settings specified with snacfg tnipid correspond to session settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] tnipid [configpath] tnipid  [configpath] tnipid [options]  
[configpath] tnipid [options]  
[configpath] tnipid  
```  
  
 where  
  
 \#configpath  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 /list  
 Generates a list of the TNIPIDs on the local subdomain.  
  
 *tnipid*  
 Specifies the TN Internet Protocol (IP) address.  
  
 /print  
 Displays a list of the configuration settings of valid telnet IP addresses. The displayed command does not contain the word snacfg, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 /add  
 Adds a TNIPID called *tnipid*. For adding a *tnipid*, the recommended method is to use the SNA Manager, not snacfg tnipid.  
  
 /delete  
 Deletes *tnipid*.  
  
## Options for TNIPID  
 **/session:** *text*  
 Specifies the session name for the specified telnet IP address.  
  
 **/subnet:** *tnipaddress*  
 Specifies the TN Internet Protocol (IP) address. If a tnipid parses as "n.n.n.n," it will be treated as an IPADDRESS. Otherwise, it will be treated as an IPNAME.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference.md)