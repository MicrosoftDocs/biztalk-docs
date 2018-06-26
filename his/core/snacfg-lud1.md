---
title: "Snacfg LUD1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce03c1c9-322f-4fb1-8381-4e8f829d3114
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg LUD
## Purpose  
 Allows you to view, add, delete, or modify downstream LUs. Also allows you to assign downstream LUs to LU pools that have already been created, and allows you to view the command that would create a specified downstream LU.  
  
> [!NOTE]
>  Configuration settings specified with **snacfg lud** correspond to downstream LU settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] luname [configpath] lunameconnectionnamevalue [options]  
[configpath] luname [options]  
[configpath] luname [configpath] luname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured downstream LUs.  
  
 *luname*  
 Specifies the name of the downstream LU to view, add, modify, or delete. A downstream LU name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The name cannot be the same as any other LU or pool name that uses this connection.  
  
 If no options are specified after *luname*, the result is a list of the configuration settings for the specified LU.  
  
 **/add**  
 Adds a downstream LU called *luname*. To configure the downstream LU, either specify other options after **/add**, or specify configuration options in additional **snacfg lud** commands (using the same *luname*).  
  
 **/delete**  
 Deletes *luname*.  
  
 **/print**  
 Causes the display of the **snacfg** command that would create the specified downstream LU. The displayed command does not contain the word **snacfg**, so it can be redirected to a command file. See the information about command files earlier in this section.  
  
## Options for Downstream LUs  
 <strong>/connection:</strong>connectionname  
 Specifies the connection to which the downstream LU should be assigned or moved. When **/add** is used, this option is required.  
  
 **/lunumber:** *value*  
 Specifies the LU number, which identifies the LU on its connection. When **/add** is used, this option is required. Check with the administrator of the host system for the correct value; it should match the LOCADDR= parameter of the LU definition in VTAM or in the NCP Gen.  
  
 The LU number identifies the LU to the host system.  
  
 If the number you specify has already been assigned to an LU or an APPC LU-LU pair on the intended connection, the command fails.  
  
 The range is from 1 through 254.  
  
 **/pool:** *poolname*  
 Assigns or moves the downstream LU to *poolname*. A downstream LU can be assigned to only one pool. The pool specified with *poolname* must already exist. A downstream LU pool can be created with the **snacfg poold** command.  
  
 If **/pool:** is typed without *poolname*, the specified LU is removed from whichever pool it is assigned to.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified LU. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)