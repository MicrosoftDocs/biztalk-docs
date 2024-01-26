---
description: "Learn more about: Snacfg LUA"
title: "Snacfg LUA2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Snacfg LUA
## Purpose  
 Allows you to view, add, delete, or modify LUA LUs on three types of connections: 802.2, SDLC, and/or X.25. Also allows you to assign LUA LUs to LU pools that have already been configured.  
  
 Before configuring an LU, you must configure the connection that the LU will use. Also, before assigning an LU to an LU pool, you must create the LU and the LU pool.  
  
> [!NOTE]
>  Configuration settings specified with snacfg lua correspond to LUA LU settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] luname [configpath] lunameconnectionnamevalue [options]  
[configpath] luname [options]  
[configpath] luname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured LUA LUs.  
  
 *luname*  
 Specifies the name of the LUA LU to view, add, modify, or delete. An LUA LU name can be from one through eight characters long and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. An LUA LU name cannot be the same as any other LU name or pool name (except for APPC LU names) on the server.  
  
 If no options are specified after *luname*, the result is a list of the configuration settings for the specified LU.  
  
 **/add**  
 Adds an LUA LU called *luname*. To configure the LUA LU, either specify other options after **/add**, or specify configuration options in additional **snacfg lua** commands (using the same *luname*).  
  
 **/delete**  
 Deletes *luname*.  
  
## Options for LUA LUs  
 **/connection:** *connectionname*  
 Specifies the connection to which the LUA LU should be assigned or moved. When **/add** is used, this option is required.  
  
 **/lunumber:** *value*  
 Specifies the LU number, which identifies the LU on its connection. When **/add** is used, this option is required. Check with the administrator of the host system for the correct value; it should match the LOCADDR= parameter of the LU definition in VTAM or the NCP Gen on the host.  
  
 If the number that you specify has already been assigned to an LU or an APPC LU-LU pair on the intended connection, the command fails.  
  
 The range is from 1 through 254.  
  
 **/pool:** *poolname*  
 Assigns or moves the LUA LU to *poolname*. An LUA LU can be assigned to only one pool. The pool specified with *poolname* must already exist. An LUA LU pool can be created with the **snacfg poola** command.  
  
 If **/pool:** is typed without *poolname*, the specified LU is removed from whichever pool it is assigned to.  
  
 **/highpriority:{ yes &#124; no }**  
 Specifies whether this LU will be given priority over low-priority LUs.  
  
 When an LUA LU is assigned to an LUA LU pool, the priority setting of the pool overwrites the priority setting of the LU.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified LU. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)
