---
title: "Snacfg CPIC1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e236c1bb-3b45-44af-a73c-76481adc12af
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Snacfg CPIC
## Purpose  
 Allows you add, delete, modify, or view a CPI-C symbolic destination name. Also allows you to view the command that would create a specified CPI-C symbolic destination name.  
  
> [!NOTE]
>  Settings specified with snacfg cpic correspond to CPI-C symbolic destination names configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] cpicname [configpath] cpicname   
   { text  |  hexstring }   
   { btexttext  |  text }   
   text{  |  |  }   
   [text] [text] [text]  
[configpath] cpicname []  
[configpath] cpicname [configpath] cpicname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured symbolic destination names.  
  
 *cpicname*  
 Specifies the symbolic destination name on which to carry out actions. A symbolic destination name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @.  
  
 If no options are specified after *cpicname*, the configuration settings for the specified symbolic destination name are displayed.  
  
 **/add**  
 Adds a symbolic destination name called *cpicname*. When you use the **/add** option, you must include the other options shown in the preceding syntax.  
  
 **/delete**  
 Deletes *cpicname*.  
  
 **/print**  
 Causes the display of the **snacfg** command that would create the specified symbolic destination name. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. See the information about command files earlier in this section.  
  
## Options for CPI-C Commands  
 **/comment:**" *text*"  
 Adds an optional comment for the symbolic destination name. The comment can contain as many as 25 characters; enclose the comment in quotes.  
  
 **Partner TP options**(use one or the other, but not both):  
 /appltpname:"**text**"  
  
 Specifies that the partner TP is an application TP, and provides the name. The name can be from 1 through 64 characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase.  
  
 If you specify both an application TP name and a service TP name in the same command, the command is rejected. If you specify an application TP for an existing symbolic destination name, it overrides any previous TP name (whether application TP or service TP).  
  
 /svcetpname:**hexstring**  
  
 Specifies that the partner TP is a service TP, and provides the hexadecimal string identifying the TP. The string can be from one through eight hexadecimal digits long.  
  
 If you specify both a service TP name and an application TP name in the same command, the command is rejected. If you specify a service TP for an existing symbolic destination name, it overrides any previous TP name (whether application TP or service TP).  
  
 **Partner LU options**(use one or the other, but not both):  
 /netname:"**text**" /luname:"**text**"  
  
 Identifies the partner LU by fully qualified LU name (network name plus LU name). Each part of the fully qualified name can be from one through eight characters long, and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase.  
  
 If you specify both a fully qualified LU name and an LU alias in the same command, the command is rejected. If you specify a fully qualified LU name for an existing symbolic destination name, it overrides any previous LU setting (whether name or alias).  
  
 /lualias:"**text**"  
  
 Identifies the partner LU by LU alias. The alias can be from one through eight characters long, and can contain alphanumeric characters and the special characters %, $, #, and @. Lowercase letters are converted to uppercase.  
  
 If you specify both an LU alias and a fully qualified LU name in the same command, the command is rejected. If you specify an LU alias for an existing symbolic destination name, it overrides any previous LU setting (whether name or alias).  
  
 **/modename:**" *text*"  
 Specifies the mode. The mode must already exist.  
  
 **/seckeytype:{ none**&#124; **same**&#124; **program}**  
 Sets the conversation security type. If **program** is specified, one or both of the following options can be set:  
  
 /secuserid:" **text**"  
 Specifies the user ID to use when the security type is **program**. The ID can contain from 1 through 10 characters.  
  
 /secpassword:" **text**"  
 This parameter is optional; it specifies the password to use with the user ID. The password can contain from 1 through 10 characters. A password need not be specified even if the security type is **program** and the user ID is set. If a display is created showing the symbolic destination name, the password will not be displayed.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference.md)