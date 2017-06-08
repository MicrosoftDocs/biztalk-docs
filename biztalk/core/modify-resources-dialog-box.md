---
title: "Modify Resources Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.resources.modify"
ms.assetid: 6974c4d6-55b1-479c-bdc0-fe1a917c1d36
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Modify Resources Dialog Box
Use the **Modify Resources** dialog box to modify options for assemblies, scripts, bindings, COM objects, and other resources and their properties that have been added to an application, or to replace these resources with updated versions bearing the same name.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Selected resources to modify - File Name**|Displays the name of the resource that has been added to the application.|  
|**Selected resources to modify - Type**|Displays the type of resource you have selected.|  
|**Selected resources to modify - Source Location**|Displays the path to the location where the resource originally resided prior to being updated in the BizTalk application.|  
|**Refresh**|Click to replace the selected resource with an updated version of the resource by the same name. When you click **Refresh**, you replace the resource without deleting any option settings you may have made. The source location of the resource will change if you are updating the resource with a version taken from a different source location.|  
|**Overwrite All**|This check box this unavailable because it is not possible to modify an existing resource without overwriting it.|  
  
## Options Tab  
 The **Options** tab displays special configuration for the resource you have selected in **Selected files to add**.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Options - File type**|From the drop-down list, select the type of file you are adding as a resource. If you select **Assembly** or **BizTalkAssembly**, you must also specify any dependencies.|  
|**Options - Options**|Displays configuration options that you may select for the type of resource you have added. Not all resource types have options.|  
|**Options - Destination location**|Type the path to the location where the resource will be stored and the filename. The default value in this box is the source location of the selected resource.|  
  
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