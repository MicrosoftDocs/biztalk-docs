---
title: "Snacfg APPCRLU1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe589389-2607-423f-879d-314522d42028
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg APPCRLU
## Purpose  
 Allows you add, delete, modify, or view a remote APPC LU. Also allows you to view the command that would create a specified remote APPC LU.  
  
> [!NOTE]
>  Configuration settings specified with snacfg appcrlu correspond to remote APPC LU settings configured with the SNA Manager.  
  
## Syntax  
  
```  
snacfg [#configpath] appcrlu /list  
```  
  
## Recommended Syntax  
  
```  
  
        [configpath]  connectionnameLUalias  
[configpath]  LUalias connectionname [options]  
[configpath]  connectionnameLUalias [options]  
[configpath]  connectionnameLUalias  [configpath]  connectionnameLUalias   
```  
  
## Other Available Syntax  
  
```  
  
        [configpath] LUalias [configpath] LUalias [options]  
[configpath] LUalias [configpath] LUalias  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured remote APPC LUs.  
  
 *connectionname* **:** *LUalias*  
 Specifies the connection and LU alias of the remote APPC LU on which to carry out actions. You should include <em>connectionname</em>**:** in **snacfg appcrlu** commands (other than **/add** commands) that include *LUalias*. Without <em>connectionname</em>**:**, if there is more than one remote LU called *LUalias* in the subdomain, it is difficult to predict which of these LUs will be affected by the command. The **snacfg appcrlu** command does not necessarily default to a connection on the local server if *connectionname* is omitted.  
  
 See the following paragraphs for details about characters permitted in the LU alias.  
  
 If no options are specified after *LUalias*, the configuration settings, partner LUs, and modes are displayed for the specified LU.  
  
 *LUalias*  
 Specifies the LU alias of the remote APPC LU on which to carry out actions. See the previous paragraphs and the syntax lists for recommendations about using the connection name with the LU alias.  
  
 The LU alias can be from one through eight characters long, and can contain alphanumeric characters and the special characters %, $, #, and @. Lowercase letters are converted to uppercase. For a remote APPC LU, the LU alias must be unique on the connection, and must not match that of a local LU on that server.  
  
 If no options are specified after *LUalias*, the configuration settings, partner LUs, and modes are displayed for the specified LU.  
  
 **/add**  
 Adds a remote APPC LU called *LUalias*. To configure the LU, either specify other options after **/add**, or specify configuration options in additional **snacfg appcrlu** commands (using the same *LUalias*).  
  
 **/delete**  
 Deletes the LU called *LUalias*.  
  
 **/print**  
 Causes the display of the **snacfg** command that would create the specified remote APPC LU. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. See the information about command files earlier in this section.  
  
## Options for Remote APPC LUs  
 **/connection:** *connectionname*  
 Specifies the connection to which to assign or move the APPC LU. When **/add** is used, this option is required.  
  
 **/netname:**" *text*"  
 Specifies a name for the network of this LU. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @.  
  
 If **/netname:**<em>text</em> is not specified, the remote network name configured for the connection supporting this LU is used as the default.  
  
> [!NOTE]
>  /luname:*text* also has a default (the LU alias). Therefore, the fully qualified LU name (network name plus LU name) can potentially be created by default, if the LU alias and remote network name are configured appropriately. A fully qualified LU name is required for an APPC LU.  
  
 **/luname:**" *text*"  
 Specifies the LU name. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. For a remote APPC LU, the fully qualified LU Name must be unique on the connection, and must not match that of a local LU on that server.  
  
 If **/luname:**<em>text</em> is not specified, *LUalias* is used as the default LU name.  
  
> [!NOTE]
>  /netname:*text* also has a default (the remote network name configured for the connection supporting this LU). Therefore, the fully qualified LU name (LU name plus network name) can potentially be created by default, if the LU alias and remote control point name are configured appropriately. A fully qualified LU name is required for an APPC LU.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the LU. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/autopartner:{ yes &#124; no }**  
 Specifies whether this LU will automatically be partnered with other APPC LUs.  
  
 If automatic partnering is left unspecified, the default is **yes**.  
  
 **/parallelsess:{ yes &#124; no }**  
 Specifies whether the remote LU supports parallel sessions.  
  
 **/uninterpname:**" *text*"  
 Specifies the uninterpreted LU name, which is required only when using dependent APPC. The name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, @ and period (.).  
  
 **/impmode:** *modename*  
 Designates *modename* as the implicit incoming mode for this LU. A mode must exist before being specified as an implicit incoming mode.  
  
 **/security:{ none**&#124; **hex,**<em>text</em>&#124; **char,**<em>text</em> **}**  
 Configures session security for a remote LU using a cleartext key. The **none** option turns off session-level security. The **hex,**<em>text</em> option specifies a 16-digit security key in hexadecimal. The **char,**<em>text</em> option specifies an eight-character security key that can include uppercase and lowercase alphanumeric characters, and the special characters $, @, #, and the period (.).  
  
 **/addpartner:** *LUalias* **,** *mode*  
 Partners the remote LU with the specified local LU and the specified mode. Both the local LU and the mode must exist before they can be specified as partners. *LUalias* should specify a local LU, not a remote LU; otherwise, an error message is displayed, indicating that no such local LU can be found.  
  
 Only one **/addpartner** option can be used in each command.  
  
 **/delpartner:** *LUalias* **,** *mode*  
 Deletes the pair-listing that includes this remote LU, the specified local LU, and the specified mode. (Does not delete any LUs or modes themselves.)  
  
 Only one **/delpartner** option can be used in each command.  
  
 **/securityex:{ none**&#124; **hex,**<em>text</em>&#124; **char,**<em>text</em> **}**  
 Configures session security for a remote LU using a scrambled key. For security purposes, Snacfg displays the security key information in a scrambled format when the /securityex option is specified. To change the security key, use the /security option instead.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)