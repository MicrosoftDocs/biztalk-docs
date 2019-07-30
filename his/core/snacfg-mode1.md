---
title: "Snacfg Mode1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1989e504-9d2b-4c65-90a7-09c5d5138769
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Snacfg Mode
## Purpose  
 Enables you to add, delete, modify, or view an APPC mode. Also enables you to view the command that would create a specified mode.  
  
> [!NOTE]
>  Configuration settings specified with snacfg mode correspond to APPC mode settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] modename [configpath] modename [options]  
[configpath] modename [options]  
[configpath] modename [configpath] modename  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured modes.  
  
 *modename*  
 Specifies the name of the mode on which to carry out actions. A mode name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The mode name cannot be the same as any other mode name in the subdomain of the server.  
  
 If no options are specified after *modename*, the configuration settings for the specified mode are displayed.  
  
 **/add**  
 Adds a mode called *modename*. To configure the mode, either specify other options after **/add**, or specify configuration options in additional **snacfg mode** commands (using the same *modename*).  
  
 **/delete**  
 Deletes *modename*.  
  
 **/print**  
 Causes the display of the **snacfg** command that would create the specified mode. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. See the information about command files earlier in this section.  
  
## Options for APPC Modes  
 **/comment:**" *text*"  
 Adds an optional comment for the mode. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/sessionlim:** *value*  
 Specifies the parallel session limit.  
  
 The range is from 1 through 254. If no parallel session limit has been specified, the default is 1.  
  
 **/conwin:** *value*  
 Specifies the minimum contention winner limit.  
  
 The range is from 0 through the parallel session limit. If no minimum contention winner limit has been specified, the default is 0.  
  
 **/conlose:** *value*  
 Specifies the partner minimum contention winner limit.  
  
 The range is from 0 through the parallel session limit. If no partner minimum contention winner limit has been specified, the default is 0.  
  
 **/autoact:** *value*  
 Specifies the automatic activation limit.  
  
 The range is from 0 through the minimum contention winner limit.  
  
 **/autopartner:{ yes &#124; no }**  
 Specifies whether this mode will be used in automatic partnering of APPC LUs.  
  
 If automatic partnering is left unspecified, the default is **yes**.  
  
 **/highpriority:{ yes &#124; no }**  
 Specifies whether communication with this mode will be given preference over low-priority communication.  
  
 If the high-priority setting is left unspecified, the default is **yes**.  
  
 **/pacesendcnt:** *value*  
 Specifies the pacing send count. A value of 0 represents an unlimited number of frames.  
  
 The range is from 0 through 63. If no pacing send count has been specified, the default is 4.  
  
 **/pacerecvcnt:** *value*  
 Specifies the pacing receive count. A value of 0 represents an unlimited number of frames.  
  
 The range is from 0 through 63. If no pacing receive count has been specified, the default is 4.  
  
 **/maxsendru:** *value*  
 Specifies the maximum size for RUs sent by the TP(s) on the local system.  
  
 The range is from 256 through 16384. If no maximum send RU size has been specified, the default is 1024.  
  
 **/maxrecvru:** *value*  
 Specifies the maximum size for RUs received from the TP(s) on the remote system.  
  
 The range is from 256 through 16384. If no maximum receive RU size has been specified, the default is 1024.  
  
 **/maxsendcomp:{ None &#124; RLE &#124; LZ9}**  
 These options offer progressively better compression, but at a progressively higher CPU usage cost.  
  
 **/maxrecvcomp:{ None &#124; RLE &#124; LZ9}**  
 These options offer progressively better compression, but at a progressively higher CPU usage cost.  
  
 **/allowcomp:{ yes &#124; no}**  
 If LZ9 is used, this option controls whether data is compressed using RLE before being further compressed using LZ9.  
  
 **/endpointcomp:{ yes &#124; no}**  
 This option controls whether intermediate nodes may use compression if one of the endpoints does not support compression or does not want to use it.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)