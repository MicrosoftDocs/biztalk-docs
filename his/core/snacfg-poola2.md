---
title: "Snacfg PoolA2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 263e7565-1df1-4d21-9b9d-e8a5a409648d
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg PoolA
## Purpose  
 Allows you to view, add, delete, or modify LUA LU pools.  
  
 To assign existing LUA LUs to an LUA LU pool, first configure the pool with the **snacfg poola** command (including options), then add the LUs with the **snacfg lua** command (using the **/pool:**<em>poolname</em> option).  
  
> [!NOTE]
>  Configuration settings specified with snacfg poola correspond to LUA LU pool settings configured with the SNA Manager.  
  
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
 Generates a list of configured LUA LU pools.  
  
 *poolname*  
 Specifies the name of the LUA LU pool to view, add, modify, or delete. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The name cannot be the same as any other pool name or LU name (other than APPC LU names) in the installation.  
  
 If no options are specified after *poolname*, the result is a list of the configuration settings for the specified pool.  
  
 **/add**  
 Adds an LUA LU pool called *poolname*. To configure the LUA LU pool, either specify other options after **/add**, or specify configuration options in additional **snacfg poola** commands (using the same *poolname*).  
  
 **/delete**  
 Deletes *poolname*.  
  
## Options for LUA LU Pools  
 **/highpriority:{ yes &#124; no }**  
 Specifies whether LUs in this pool will be given priority over low-priority LUs. The priority setting of a pool overwrites the setting of any LUA LU assigned to the pool.  
  
 **/comment:**" *text*"  
 Adds an optional comment to the specified LUA LU pool. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)