---
description: "Learn more about: Snacfg TN3Session"
title: "Snacfg TN3Session1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Snacfg TN3Session
## Purpose  
 Allows you to view, add, delete, or modify TN 3270 sessions. the SNA Manager is the recommended interface for adding sessions.  
  
> [!NOTE]
>  Configuration settings specified with snacfg tn3session correspond to session settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath]  luname [configpath] luname  [configpath] luname[options]  
[configpath] luname [options]  
[configpath] luname   
```  
  
 where  
  
 \#configpath  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 /list  
 Generates a list of the sessions on the local subdomain.  
  
 *luname*  
 Specifies the LU name on which the session will be activated.  
  
 /print  
 Displays a list of the configuration settings of a print session. The displayed command does not contain the word snacfg, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 /add  
 Adds a TN 3270 session called luname. For adding a session, the recommended method is to use the SNA Manager, not snacfg tn3session.  
  
 /delete  
 Deletes lu*name*.  
  
## Options for TN 3270 Sessions  
 **/tn3server:** *tn3servername*(required)  
 Specifies the computer name of the TN 3270 server on which settings will be viewed or changed. The *tn3servername* is required.  
  
 **/assocname:**" *text*"  
 Printer LUs can be marked as associated instead of generic or specific. To associate a printer LU with a terminal LU, type the Associated LU name. When this option is selected, the **terminal name** will default to IBM-3287-1. The quotes must be included.  
  
 **/portnumber:** *value*  
 Specifies the port number associated with telnet (for example, port number 23). You can type another port number to override the default value for a given session. TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client to connect to multiple host computers.  
  
 **/pooltype:** *pooltype*  
 The values for pooltype are: GenericTerminal, SpecificTerminal, GenericPrinter, SpecificPrinter, AssocPrinter.  
  
 **/maxsessions:** *value*  
 Specifies the maximum number of LU-LU sessions that one independent LU can support. The limit set by maxsessions prevents an independent LU from using up too many unreserved session control blocks.  
  
 **/modeltypes:** *model*[,model, ]  
 Values for TN3270 model types are:  
  
 Model2, Model3, Model4, Model5,  
  
 3275_2, 3276_2, 3277_2, 3278_2, 3278_2_E, 3279_2, 3279_2_E,  
  
 3276_3, 3278_3, 3278_3_E, 3279_3, 3279_3_E,  
  
 3276_4, 3278_4, 3278_4_E, 3279_4, 3279_4_E,  
  
 3278_5, 3278_5_E, 3279_5, 3279_5_E,  
  
 Dynamic, 3287_1  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)
