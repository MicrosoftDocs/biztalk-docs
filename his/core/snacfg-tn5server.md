---
title: "Snacfg TN5Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 014bf3b3-2e18-4abd-a5db-a43307d5ce59
caps.latest.revision: 4
---
# Snacfg TN5Server
## Purpose  
 Allows you to view, add, delete, or modify TN 5250 servers. the SNA Manager is the recommended interface for adding TN 5250 servers.  
  
> [!NOTE]
>  Configuration settings specified with snacfg tn5server correspond to server settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] TN5Servername [configpath] TN5Servernname [configpath] TN5Servernname[options]  
[configpath] TN5Servername [options]  
[configpath] TN5Servername  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of the TN 5250 servers on the local subdomain.  
  
 *Tn5servername*  
 Specifies the computer name of the TN 5250 server on which settings will be viewed or changed.  
  
 **/print**  
 Displays a list of the configuration settings of a print session. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 **/add**  
 Adds a Host Integration Server computer called *tn5servername*. For adding a TN 5250 server, the recommended method is to use the SNA Manager, not **snacfg tn5server**.  
  
 Before you can add connections to the server, link services must also be configured for the server. The recommended interface for configuring link services is the SNA Manager.  
  
 **/delete**  
 Deletes *tn5servername*.  
  
## Options for TN 5250 Servers  
 **/portnumber:** *value*  
 Specifies the port number associated with telnet (for example, port number 23). You can type another port number to override the default value for a given session. TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client to connect to multiple host computers.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified server. The comment can contain as many as 25 characters; enclose the comments in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference.md)