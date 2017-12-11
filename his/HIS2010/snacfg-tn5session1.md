---
title: "Snacfg TN5Session1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8119c6ff-1b46-4cf5-8f87-af041c62fa58
caps.latest.revision: 4
---
# Snacfg TN5Session
## Purpose  
 Enables you to view, add, delete, or modify TN 5250 sessions. the SNA Manager is the recommended interface for adding sessions.  
  
> [!NOTE]
>  Configuration settings specified with snacfg tn5session correspond to session settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] appcrlualias [configpath] appcrlualias [configpath] appcrlualias[options]  
[configpath]  appcrlualias [options]  
[configpath] appcrlualias  
```  
  
 where  
  
 \#configpath  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 /list  
 Generates a list of the sessions on the local subdomain.  
  
 *appcrlualias*  
 Specifies the APPC remote LU alias name on which the session will be activated.  
  
 /print  
 Displays a list of the configuration settings of a print session. The displayed command does not contain the word snacfg, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 /add  
 Adds a TN 5250 session called *appcrlualias*. For adding a session, the recommended method is to use the SNA Manager, not snacfg tn5session.  
  
 /delete  
 Deletes *appcrlualias*.  
  
## Options for TN 5250 Sessions  
 **/tn5server:** *tn5servername*(required)  
 Specifies the computer name of the TN 5250 server on which settings will be viewed or changed.  
  
 **/locallu:** *appclualias*(required)  
 Specifies the name of the APPC LU alias to view, add, modify, or delete. An APPC LU alias name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The APPC LU alias name cannot be the same as any other APPC LU alias name or pool name on the server.  
  
 **/mode:** *modename*  
 Specifies the name of the mode on which to carry out actions. A mode name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The mode name cannot be the same as any other mode name in the subdomain of the server.  
  
 If no options are specified after modename, the configuration settings for the specified mode are displayed.  
  
 **/user:** *username*  
 Specifies the name of the user to view, change settings for, or delete. For adding TN 5250 users, the recommended method is to user the SNA Manager, not **snacfg tn5session**. If you are adding a user, *username* must match the name in the user's account on the Windows domain or on the local system.  
  
 **/password:** *password*  
 Specifies the current password for the user's account identified in *username*.  
  
 **/modeltypes:** *model*(,model, )  
 Specifies the model type. Values for TN5250 model types are:  
  
 5555_C01, 5555_B01, 3477_FC, 3477_FG  
  
 3180_2, 3179_2, 3196_A1  
  
 5292_2, 5291_1, 5251_11  
  
 **/portnumber:** *value*  
 Specifies the port number associated with telnet (for example, port number 23). You can type another port number to override the default value for a given session. TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client to connect to multiple host computers.  
  
 **/comment:**" *text*"  
 Optionally, type a comment of up to 25 characters.  
  
## See Also  
 [Snacfg Reference](../HIS2010/snacfg-reference1.md)