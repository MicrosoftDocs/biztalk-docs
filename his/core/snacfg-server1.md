---
title: "Snacfg Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42ae3bab-2e40-41ad-8df1-5fb17f96d409
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Snacfg Server
## Purpose  
 Allows you to view or change settings for servers. Can also be used to add a server, although the SNA Manager is the recommended interface for adding servers.  
  
> [!NOTE]
>  Configuration settings specified with snacfg server correspond to server settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] servername [configpath] servername [options]  
[configpath] servername [options]  
[configpath] servername  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of the servers on the local subdomain.  
  
 *servername*  
 Specifies the name of the server on which settings will be viewed or changed. The server name should be in the format machine_name or \\\machine_name\snaservr (for specifying the primary node on the machine) and \\\machine_name\snasrv02 (or snasrv03, snasrv04, and so on) for specifying the secondary nodes on the machine.  
  
 **/add**  
 Adds a Host Integration Server computer called *servername*. For adding a server, the recommended method is to use the SNA Manager, not **snacfg server**.  
  
 Before you can add connections to the server, link services must also be configured for the server. The recommended interface for configuring link services is the SNA Manager.  
  
 **/delete**  
 Deletes *servername*.  
  
## Options for Servers  
 **/netname:**" *text*"  
 Specifies the local network name, which identifies the SNA network of the local server. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. If the local network name is specified, the local control point name must also be specified (using the **/cpname** option).  
  
 **/cpname:**" *text*"  
 Specifies the local control point name, which identifies the local system to other control points (nodes) on the SNA network. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. If the local control point name is specified, the local network name must also be specified (using the **/netname** option).  
  
 When connecting to a host system and using a local control point name, the name should match the CPNAME = parameter in the host's PU definition.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified server. The comment can contain as many as 25 characters; enclose the comments in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)