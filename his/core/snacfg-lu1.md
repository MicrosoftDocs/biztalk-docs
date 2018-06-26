---
title: "Snacfg LU1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9c45c05-df32-49dc-ac02-ef50a2cb6760
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg LU
## Purpose  
 Allows you to view, add, delete, or modify 3270 LUs, on three types of connections: 802.2, SDLC, and/or X.25. Also allows you to assign 3270 LUs to LU pools that have already been configured.  
  
 Before configuring an LU, you must configure the connection that the LU will use. Also, before assigning an LU to an LU pool, you must create the LU and the LU pool.  
  
> [!NOTE]
>  Configuration settings specified with snacfg lu correspond to 3270 LU settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] luname [configpath] lunameconnectionnamevalue [options]  
[configpath] luname [options]  
[configpath] luname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured 3270 LUs.  
  
 *luname*  
 Specifies the name of the 3270 LU to view, add, modify, or delete. A 3270 LU name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. A 3270 LU name cannot be the same as any other LU name or pool name (except for APPC LU names) on the server.  
  
 If no options are specified after *luname,* the result is a list of the configuration settings for the specified LU.  
  
 **/add**  
 Adds a 3270 LU called *luname*. To configure the 3270 LU, either specify other options after **/add**, or specify configuration options in additional **snacfg lu** commands (using the same *luname*).  
  
 **/delete**  
 Deletes *luname*.  
  
## Options for 3270 LUs  
 **/connection:** *connectionname*  
 Specifies the connection to which the 3270 LU should be assigned or moved. When **/add** is used, this option is required.  
  
 **/lunumber:** *value*  
 Specifies the LU number, which identifies the LU on its connection. When /**add** is used, this option is required. Check with the administrator of the host system for the correct value; it should match the LOCADDR= parameter of the LU definition in VTAM or the NCP Gen on the host.  
  
 If the number that you specify has already been assigned to an LU or an APPC LU-LU pair on the intended connection, the command fails.  
  
 The range is from 1 through 254.  
  
 **/pool:** *poolname*  
 Assigns or moves the 3270 LU to *poolname*. A 3270 LU can be assigned to only one pool.  
  
 The pool specified with *poolname* must already exist. A 3270 LU pool can be created with the **snacfg pool** command.  
  
 If **/pool:** is typed without *poolnam*e, the specified LU is removed from whichever pool it is assigned to.  
  
 **/lutype:{ display &#124; printer }**  
 Specifies whether the 3270 LU will be used for **display** (terminal emulation) or a **printer** (that is, a local printer or a local-area network printer, attached to a PC).  
  
 If no LU type has been specified, the default is **display**.  
  
 **/displaymodel:{ mod2 &#124; mod3 &#124; mod4 &#124; mod5 &#124; 2 &#124; 3 &#124; 4 &#124; 5 }**  
 Specifies the display model; applies only when the **lutype** is **display**. The following display types are available:  
  
- Model 2 is 24 lines by 80 characters.  
  
- Model 3 is 32 lines by 80 characters.  
  
- Model 4 is 43 lines by 80 characters.  
  
- Model 5 is 27 lines by 132 characters.  
  
  Some emulators can only emulate certain display models. For more information, see your emulator documentation.  
  
  When a 3270 display LU is assigned to a 3270 LU pool, the display model setting of the pool overrides the setting of the LU.  
  
  If no display model has been specified, the default is Model 2.  
  
  **/allowmodeloverride:{ yes &#124; no }**  
  Specifies whether the user is allowed to override the display model type by using the 3270 terminal emulation program.  
  
  When a 3270 display LU is assigned to a 3270 LU pool, the model override setting of the pool overwrites the setting of the LU.  
  
  If no setting has been specified for this parameter, the default is **no**.  
  
  **/associate:**" *text*"  
  This allows you to associate a specific 3270 printer LU with a 3270 display LU. Any user or group with permission to use the display LU will also have access to the associate printer LU. The text is the printer LU name.  
  
  **/unassociate:**" *text*"  
  This allows you to unassociate a 3270 printer LU from a 3270 display LU. It is not necessary to enter any text. **Snacfg** will ignore the text and unassociate the LU. To unassociate the printer LU, use the display LU name.  
  
  **/comment:**" *text*"  
  Adds an optional comment for the specified LU. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)