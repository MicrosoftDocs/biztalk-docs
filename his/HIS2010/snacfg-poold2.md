---
title: "Snacfg PoolD2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 293a2c90-2215-4813-bd6c-6c1aed0b618e
caps.latest.revision: 3
---
# Snacfg PoolD
## Purpose  
 Allows you to view, add, or delete downstream LU pools. Also allows you to view the command that would create a specified downstream LU pool.  
  
 To assign existing downstream LUs to a downstream LU pool, first configure the pool with the **snacfg poold** command; then add the LUs with the **snacfg lud** command (using the **/pool:***poolname* option).  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] poolname [configpath] poolname [] [text]  
[configpath] poolname [configpath] poolname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured downstream LU pools.  
  
 *poolname*  
 Specifies the name of the downstream LU pool to view, add, or delete. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The name cannot be the same as any other pool name or LU name (other than APPC LU names) in the subdomain.  
  
 If no options are specified after *poolname*, the result is a list of the configuration settings for the specified pool.  
  
 **/add**  
 Adds a downstream LU pool called *poolname*.  
  
 **/delete**  
 Deletes *poolname*.  
  
 **/print**  
 Causes the display of the **snacfg** command that would create the specified downstream LU pool. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. See the information about command files earlier in this section.  
  
 **/comment:**" *text*"  
 Adds an optional comment to the specified downstream LU pool. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
## See Also  
 [Snacfg Reference](../HIS2010/snacfg-reference1.md)