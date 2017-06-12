---
title: "Add Resources Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.resources.add"
ms.assetid: c3e28cea-aeb2-4d93-a45e-faaa5a6d6533
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Add Resources Dialog Box
Use the **Add Resources** dialog box to add assemblies, scripts, bindings, COM objects, and other resources to an application.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Selected files to add - File Name**|Displays the name of the resource that you have selected to add to the application.|  
|**Selected files to add - Type**|Displays the type of resource that you have selected.|  
|**Selected files to add - Source Location**|Displays the path to the location where the resource resides prior to being added to the application.|  
|**Add**|Displays the **Select Files to Add** dialog box, to which you can browse and select the resource to add to the application.|  
|**Remove**|Click to remove the selected resource from the application.|  
|**Overwrite All**|Select this check box when you are adding a resource that you already know is in the database, but that you want to replace. If you do not select **Overwrite All**, an existing resource by the same name as one you are adding will cause the add process to fail.|  
  
## Options Tab  
 The **Options** tab displays special configuration for the resource you have selected in **Selected files to add**.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Options - File type**|From the drop-down list, select the type of file you are adding as a resource. If you select **Assembly** or **BizTalkAssembly**, you must also specify any dependencies.|  
|**Options - Options**|Displays configuration options that you may select for the type of resource you have added. Not all resource types have options.|  
|**Options - Destination location**|Type the path of the location to which the resource file will be copied when the application is installed, including the resource file name. An absolute path, relative path, or Universal Naming Convention (UNC) path are all acceptable. Folders that do not exist will be created upon installation if required security rights are in place and there is sufficient space. The default value in this box is as follows: *path of application installation folder*\\*resource file name*. The path of the installation folder is specified by the %BTAD_InstallDir% environment variable. Example: %BTAD_InstallDir%\MyResource.xml.|  
|**Options – Target Environment (BizTalkBinding File type)**|A string specifying which environment the binding file is associated with. If you choose this environment at import time, this binding file is applied. If you do not specify a string, this binding file is applied to all environments.|  
  
## Dependencies Tab  
 The **Dependencies** tab appears only when **Assembly** or **BizTalk Assembly** is selected in the **File type** list on the **Options** tab. It displays information about other files on which the selected resource has a dependency.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Dependent Assemblies - Name**|Displays the name, version, culture, and public key token of a resource upon which the assembly you have selected in **Selected files to add** depends.|  
|**Dependent Assemblies - Status**|Displays status information about the depended-upon assembly.|  
|**Add to Application**|Click to select assembly files with which the new resource has a dependency.|  
  
## See Also  
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)