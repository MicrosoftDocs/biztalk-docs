---
title: "Snacfg APPCLLU2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c85498e-7280-453a-bdaa-b86466bb4d97
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg APPCLLU
## Purpose  
 Allows you add, delete, modify, or view a local APPC LU. Also allows you to view the command that would create a specified local APPC LU.  
  
> [!NOTE]
>  Configuration settings specified with snacfg appcllu correspond to local APPC LU settings configured with the SNA Manager.  
  
## Syntax  
  
```  
snacfg [#configpath] appcllu /list  
```  
  
## Recommended Syntax  
  
```  
  
        [configpath]  servernameLUalias  
[configpath]  LUalias servername [options]  
[configpath]  servernameLUalias [options]  
[configpath]  servernameLUalias  [configpath]  servernameLUalias   
```  
  
## Other Available Syntax  
  
```  
  
        [configpath]  [configpath]  LUalias  
[configpath]  LUalias [options]  
[configpath]  LUalias  [configpath]  LUalias   
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\System\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured local APPC LUs.  
  
 *servername* **:** *LUalias*  
 Specifies the server name and LU alias of the local APPC LU on which to carry out actions. The server name should be in the format machine_name or \\\machine_name\snaservr (for specifying the primary node on the machine) and \\\machine_name\snasrv02 (or snasrv03, snasrv04, and so on) for specifying the secondary nodes on the machine.  
  
 It is recommended that <em>servername</em>**:** be included in **snacfg appcllu** commands (other than **/add** commands) that include *LUalias*. Without <em>servername</em>**:**, if there is more than one local LU called *LUalias* in the subdomain, it is difficult to predict which of these LUs will be affected by the command. The **snacfg appcllu** command does not necessarily default to the local server if *servername* is omitted.  
  
 See the following paragraphs for details about characters permitted in the LU alias.  
  
 If no options are specified after *LUalias*, the configuration settings, partner LUs, and modes are displayed for the specified LU.  
  
 *LUalias*  
 Specifies the LU alias of the local APPC LU on which to carry out actions. See the previous paragraphs and the syntax lists for recommendations about using the server name with the LU alias.  
  
 The LU alias can be from one through eight characters long, and can contain alphanumeric characters and the special characters %, $, #, and @. Lowercase letters are converted to uppercase. For a local APPC LU, the LU alias must be unique on the server.  
  
> [!NOTE]
>  *LUalias* is used as the default LU name if **/luname:**<em>text</em> is not specified.  
  
 If no options are specified after *LUalias*, the configuration settings, partner LUs, and modes are displayed for the specified LU.  
  
 **/add**  
 Adds a local APPC LU called *LUalias*. To configure the LU, either specify other options after **/add**, or specify configuration options in additional **snacfg appcllu** commands (using the same *LUalias*).  
  
 **/connection:** *conn-name*  
 When adding or modifying a dependent local APPC LU, this option is used to specify the LU's connection assignment.  
  
 **/delete**  
 Deletes the LU called *LUalias*.  
  
 **/print**  
 Causes the display of the **snacfg** command that would create the specified local APPC LU. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file.  
  
## Options for Local APPC LUs  
 **/server:** *servername*  
 Specifies the server to which to assign or move the APPC LU. When **/add** is used, this option is required. The server name should be in the format machine_name or \\\machine_name\snaservr (for specifying the primary node on the machine) and \\\machine_name\snasrv02 (or snasrv03, snasrv04, and so on) for specifying the secondary nodes on the machine.  
  
 **/lunumber:** *value*  
 Specifies the LU number. If an LU number of 0 is specified, the LU is configured as an independent local APPC LU.  
  
 **/netname:**" *text*"  
 Specifies a name for the network of this LU. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @.  
  
 If **/netname:**<em>text</em> is not specified, the network name of the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] on which the LU is located is used as the default.  
  
> [!NOTE]
>  /luname:*text* also has a default (the LU alias). Therefore, the fully qualified LU name (network name plus LU name) can potentially be created by default, if the LU alias and local network name are configured appropriately. A fully qualified LU name is required for an APPC LU.  
  
 **/luname:**" *text*"  
 Specifies the LU name. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. For a local APPC LU, the fully qualified LU Name (Network Name plus LU Name) must be unique on the server.  
  
 If **/luname:**<em>text</em> is not specified, *LUalias* is used as the default LU name.  
  
> [!NOTE]
>  /netname:*text* also has a default (the network name of the server on which the LU is located). Therefore, the fully qualified LU name (network name plus LU name) can potentially be created by default, if the LU alias and local network name are configured appropriately. A fully qualified LU name is required for an APPC LU.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the LU. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/autopartner:{ yes**&#124; **no }**  
 Specifies whether this LU will automatically be partnered with other APPC LUs.  
  
 If automatic partnering is left unspecified, the default is **yes**.  
  
 **/defaultpool:{ yes**&#124; **no }**  
 Specifies whether this LU will be in the default outgoing local APPC LU pool. This pool makes LUs available for invoking TPs that do not specify a local LU.  
  
 **/impremotelu:** *remoteLUname*  
 Specifies an existing remote LU to be used as an implicit incoming remote LU for the local LU.  
  
 **/tptimeout:** *value*  
 Specifies the number of seconds that [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] should wait for the invokable TP to respond to a start request from the invoking TP.  
  
 **/addpartner:** *LUalias* **,** *mode*[ **,**<em>connection</em>]  
 Partners the local LU with the specified LU and the specified mode. Both *LUalias* and *mode* must exist before they can be specified as partners. If *LUalias* specifies a remote LU that is not unique on the server, the connection used by the remote LU must also be specified; otherwise, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will randomly choose one of the remote LUs called *LUalias* to act on.  
  
 Only one **/addpartner** option can be used in each command.  
  
 **/delpartner:** *LUalias* **,** *mode*[ **,**<em>connection</em>]  
 Deletes the pair listing that includes this local LU, the specified partner LU, and the specified mode. (Does not delete any LUs or modes themselves.) If *LUalias* specifies a remote LU that is not unique on the server, the connection used by the remote LU must also be specified; otherwise, Host Integration Server will randomly choose one of the remote LUs called *LUalias* to act on.  
  
 Only one **/delpartner** option can be used in each command.  
  
 **/syncpoint:{ yes &#124; no }**  
 Specifies if this Local APPC LU provides LU 6.2 SyncPoint support.  
  
 **/clientname:** *"text"*  
 Specifies client name if SyncPoint support is enabled.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)