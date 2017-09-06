---
title: "UninstallApp Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f45c9530-8138-40f1-b279-1428c5a7fbbc
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# UninstallApp Command
Uninstalls a BizTalk application from the local computer and also removes the application from the list of programs in Add or Remove Programs in Control Panel. This command has the same effect as removing an application by using Add or Remove Programs. If multiple .msi files have been installed for this application, all of the items installed by all of the .msi files are uninstalled.  
  
 The application name that you specify for this command must match the name of the application as displayed in Add or Remove Programs. If you are unsure of the application name, you can use the **ListPackage** command to obtain it, as described in [ListPackage Command](../core/listpackage-command.md).  
  
> [!IMPORTANT]
>  Although it is possible to uninstall an application by double-clicking the .msi file, doing this is not supported. This is because multiple .msi files can be installed for the same application, and using this method will not uninstall all of the items associated with the application.  
  
## Usage  
 **BTSTask UninstallApp /ApplicationName:** *value*  
  
## Parameters  
  
|Parameter|Required|Description|  
|---------------|--------------|-----------------|  
|**/ApplicationName** (or **/A**, see Remarks)|Yes|Name of the BizTalk application to uninstall. If the name includes spaces, you must enclose it in double quotation marks (").|  
  
## Sample  
 **BTSTask UninstallApp /ApplicationName:MyApplication**  
  
## Remarks  
 Parameters are not case-sensitive. You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)