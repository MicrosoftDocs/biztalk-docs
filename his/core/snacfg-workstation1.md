---
description: "Learn more about: Snacfg Workstation"
title: "Snacfg Workstation1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Snacfg Workstation
## Purpose  
 The workstation assignment feature allows you to add, delete, modify, or view workstations. You can specify parameters such as IP address, workstation name, and define access parameters to the workstation.  
  
> [!NOTE]
>  Configuration settings specified with snacfg workstation correspond to local workstation settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] workstationid [configpath] workstationid [configpath] workstationid [options]  
[configpath] workstationid [options]  
[configpath] workstationid  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of configured workstations.  
  
 **/print**  
 Displays a list of the configuration settings of a workstation. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 **/add**  
 Adds the workstation ID using a either a name or IP address to identify the workstation. The workstation ID is usually the workstation name.  
  
 If using an IP address to identify the workstation, the **/address** option is a required parameter.  
  
 To configure the workstation, either specify other options after **/add** or specify configuration options in additional **snacfg workstation** *workstationid* commands.  
  
 **/delete**  
 Deletes the workstation.  
  
## Options for Workstation  
 **/insert:** *luname*[ *,luname,*]  
 Assigns the specified 3270 or LUA LUs or pools to the workstation. Separate multiple names with commas.  
  
 **/remove:** *luname*[ *,luname,*]  
 Deletes the assignment of 3270 or LUA LUs or pools to the workstation. Separate multiple names with commas.  
  
 **/insertrlu:** *luname*[, *luname*,...]  
 Assigns APPC Remote LUs to the workstation. Separate multiple names with commas. The name *rluname* can be either the RLU alias or its fully-qualified name of the form "*netname.luname*".  
  
 **/removerlu:** *luname*[, *luname*,...]  
 Deletes the assignment of APPC Remote LUs to the workstation. Separate multiple names with commas. The name *rluname* can be either the RLU alias or its fully-qualified name of the form "*netname.luname*".  
  
 **/comment:**" *comment*"  
 Sets the workstation's comment field. The quotes must be included.  
  
 **/wkstaonly:{ yes &#124; no }**  
 If **yes**,it restricts resources available on the computer to the LUs assigned to the workstation. Users will not be able to access LUs assigned to them unless the LU is also assigned to the workstation. If **no**, it allows users access to the LUs assigned to the workstation and the LUs assigned to the user. The default is **no**.  
  
 **/address:{ yes &#124; no }**  
 If **yes**, Host Integration Server will look for an IP address in place of an alphanumeric name for the workstation ID. This parameter must be set to **yes** if using an IP address. The default is **no**.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)
