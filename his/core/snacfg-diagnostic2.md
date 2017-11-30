---
title: "Snacfg Diagnostic2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 643d211c-e7d4-4b19-8993-35fee9ef0aa6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Snacfg Diagnostic
## Purpose  
 Allows you to view and configure settings for event logging (auditing), and view or change the connection designated to receive NetView alerts.  
  
> [!NOTE]
>  Configuration settings specified with snacfg diagnostic correspond to diagnostic settings configured with the SNA Manager.  
  
## Syntax  
  
```  
snacfg [#configpath] diagnostic /list  
snacfg [#configpath] diagnostic [options]  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list that tells the settings for event logs (auditing), the name of the NetView management connection (if one has been specified), and the default connection for the **DISPLAY** verb (if one has been specified).  
  
 **/logserver:** *servername*  
 Specifies a centralized server on which event logs for this Host Integration Server installation should be stored.  
  
 If **/logserver:** is typed without *servername*, the setting reverts to the default, which is to store event logs for the local server on the local server.  
  
 **/auditlevel:{ 6**&#124; **8**&#124; **10**&#124; **off}**  
 Sets the level of Host Integration Server events to be recorded in the Windows Event Log. These events can be viewed with the Windows Event Viewer, which is described in the Windows documentation. The following table describes the available levels:  
  
|Level|Description|Events to be recorded|  
|-----------|-----------------|---------------------------|  
|6|Detailed problem analysis|All events that can be recorded|  
|8|General information messages|General activity but not all events|  
|10|Significant system events|Major events only|  
|off|Auditing disabled|No events|  
  
 **/popupserver:** *servername*  
 Specifies the server to which pop-up error messages for this Host Integration Server installation should be routed.  
  
 Pop-up messages will always appear on the local server; routing them to a remote server means they will appear on both the remote and local server.  
  
 If **/popupserver:** is typed without *servername*, the setting reverts to the default, which is the local server.  
  
 **/netviewconn:** *connectionname*  
 Specifies the name of the connection through which NetView alerts are sent. The connection called *connectionname* must already exist.  
  
 If **/netviewconn:** is typed without *connectionname,* the setting is cleared so that the configuration contains no NetView connection name.  
  
 **/cnosdisplayconn:** *connectionname*  
 Specifies the default connection to be used for the **DISPLAY** verb when no connection is provided. The connection called *connectionname* must already exist.  
  
 If **/cnosdisplayconn:** is typed without *connectionname,* the setting is cleared so that the configuration contains no default connection for the **DISPLAY** verb.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)