---
title: "Snacfg Pool1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f97d8724-adc3-404e-822f-699f3f627325
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg Pool
## Purpose  
 Allows you to view, add, delete, or modify 3270 LU pools.  
  
 To assign existing 3270 LUs to a 3270 LU pool, first configure the pool with the **snacfg pool** command (including options), then add the LUs with the **snacfg lu** command (using the **/pool:**<em>poolname</em> option).  
  
> [!NOTE]
>  Configuration settings specified with snacfg pool correspond to 3270 LU pool settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] poolname [configpath] poolname [options]  
[configpath] poolname [options]  
[configpath] poolname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured 3270 LU pools.  
  
 *poolname*  
 Specifies the name of the 3270 LU pool to view, add, modify, or delete. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The name cannot be the same as any other pool name or LU name (other than APPC LU names) in the installation.  
  
 If no options are specified after *poolname*, the result is a list of the configuration settings for the specified pool.  
  
 **/add**  
 Adds a 3270 LU pool called *poolname*. To configure the 3270 LU pool, either specify other options after **/add**, or specify configuration options in additional **snacfg pool** commands (using the same *poolname*).  
  
 **/delete**  
 Deletes *poolname*.  
  
## Options for 3270 LU Pools  
 **/displaymodel:{ mod2 &#124; mod3 &#124; mod4 &#124; mod5 &#124; 2 &#124; 3 &#124; 4 &#124; 5 }**  
 Specifies the model number of the LUs that will be added to this pool. (Only display LUs can be pooled; printer LUs cannot be pooled.) The following display models are available:  
  
- Model 2 is 24 lines by 80 characters.  
  
- Model 3 is 32 lines by 80 characters.  
  
- Model 4 is 43 lines by 80 characters.  
  
- Model 5 is 27 lines by 132 characters.  
  
  Some emulators can only emulate certain display models. For more information, see your emulator documentation.  
  
  The display model setting of a pool overwrites the setting of any 3270 LU assigned to the pool.  
  
  If no display model has been specified for a pool, the default is Model 2.  
  
  **/allowmodeloverride:{ yes &#124; no }**  
  Specifies whether the user is allowed to override the display model type of the LU by using the 3270 terminal emulation program.  
  
  The model override setting of a pool overwrites the setting of any 3270 LU assigned to the pool.  
  
  If no setting has been specified for this parameter, the default is **no**.  
  
  **/comment:**" *text*"  
  Adds an optional comment to the specified 3270 LU pool. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
  **/assocprint:{ yes &#124; no }**  
  Specifies that the LU pool contains display LUs with associated 3270 printers.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)