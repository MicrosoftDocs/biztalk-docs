---
title: "Snacfg LINK2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c8923eb-f626-4db1-9ab1-126831a06a9e
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg LINK
## Purpose  
 Allows you to view, delete, or modify adapters.  
  
> [!NOTE]
>  This command has been superseded by **Linkcfg**, as described in **About Linkcfg**.  
  
> [!IMPORTANT]
>  If you specify adapter properties with **snacfg link**, these properties must match existing properties in your installation, or a nonfunctioning configuration may result. To protect against errors with **snacfg link**, use the SNA Manager instead.  
  
 Before configuring link services, you must use the SNA Manager to add the server on which the link services will be located.  
  
## Syntax  
  
```  
  
[configpath]   
```  
  
## Recommended Syntax  
  
```  
  
        [configpath]servernamelinkname [configpath]servernamelinkname [options]  
[configpath]servernamelinkname [options]  
[configpath]servernamelinkname  
```  
  
## Other Available Syntax  
  
```  
  
        [configpath]linkname [configpath]linkname [options]  
[configpath]linkname [options]  
[configpath]linkname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured link services.  
  
 *servername*  
 Specifies the name of the server on which to view or change link services. Separate the name of the server from the name of the link service with a colon (**:**). It is recommended that *servername* be included in every **snacfg link** command that includes *linkname*. Without *servername*, if there is more than one link service called *linkname* in the installation, it is difficult to predict which link service called *linkname* will be affected by the command. The **snacfg link** command does not necessarily default to the local server if *servername* is omitted.  
  
 *linkname*  
 Specifies the name of the link service to view, modify, or delete. Link services names can contain from one through eight alphanumeric characters.  
  
 For adding link services, the recommended method is to use the SNA Manager, not **snacfg link**.  
  
 If no options are specified after *linkname*, the result is a list of the configuration settings for the specified link.  
  
 **/add**  
 Adds a link service called *linkname*. To configure the link service, either specify other options after **/add**, or specify configuration options in additional **snacfg link** commands (using the same <em>servername</em>**:**<em>linkname</em> combination).  
  
 For adding link services, the recommended method is to use the SNA Manager, not **snacfg link**.  
  
 **/delete**  
 Deletes *linkname*.  
  
## Options for Link Services  
 **/server:** *servername*  
 Specifies the server on which to install the link service.  
  
 **/linktype:{ Token**&#124; **Ether**&#124; **SDLC**&#124; **X25**&#124; **Channel &#124; Twinax }**  
 Specifies the type of adapter with which *linkname* works.  
  
 **/linetype:{ leased**&#124; **softdial**&#124; **manual}**(for SDLC lines only)  
 Specifies the type of SDLC line (and, where applicable, the modem) that the link service will use:  
  
- A **leased** line is a telecommunications line committed solely to SDLC communications with a particular remote system.  
  
- A **softdial** line is a switched SDLC line on which the modem is dialed automatically by Host Integration Server. Such a modem must be attached to an SDLC adapter with a built-in serial (COM) port. Otherwise it is considered a **manual** modem.  
  
- A **manual** line is a switched SDLC line on which the modem stores a phone number, or on which the modem is dialed manually.  
  
  **/carrier:{ on**&#124; **off}**(for SDLC lines only)  
  Specifies whether the constant carrier option for an SDLC line is **on** or **off**.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)