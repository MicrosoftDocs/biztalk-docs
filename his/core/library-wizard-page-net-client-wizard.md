---
title: "Library Wizard Page (.NET Client Wizard)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15455"
ms.assetid: 470c5302-4cf7-4f2f-8d4d-aca4611a012d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Library Wizard Page (.NET Client Wizard)
Use the **Library** wizard page to identify the .NET client library you are creating.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Interface name**|Type the full name for the class in the .NET assembly. The name of the interface, when combined with the major version number and the namespace name, cannot exceed 39 Unicode characters.|  
|**Version**|Type the version information for the .NET assembly in the form *major.minor*. The major version number, when combined with the name of the interface and the namespace name, cannot exceed 39 Unicode characters.|  
|**Component class name**|View the component class name to be associated with the managed class in the .NET assembly. The format is *Namespace.Interface.MajorVersion*. The namespace name, when combined with the major version number and the name of the interface, cannot exceed 39 Unicode characters.|  
|**Type Restrictions**|Select the type appropriate to your library. As you continue to develop your project, appropriate restrictions will be applied based on this selection.<br /><br /> This step will help prevent you from creating a library that contains types that are not supported by the applications that will be using them (for example, ASMX or BizTalk Server).<br /><br /> Selecting **None** will result in no restrictions.<br /><br /> Selecting **Web Service** will allow access to data sets, but restrict access to data tables and multi-dimensional arrays.<br /><br /> Selecting **BizTalk Adapter for Host Applications** will allow access to arrays only, and restrict access to data tables, data sets, and multi-dimensional arrays.|  
|**Description**|Type the description to be associated with the interface. The description can be a maximum of 256 Unicode characters.|  
  
## See Also  
 [Library Properties](../core/library-properties.md)   
 [Remote Environment Wizard Page 1 (.NET Client Wizard)](../core/remote-environment-wizard-page-1-net-client-wizard.md)   
 [New .NET Client Library Wizard](../core/new-net-client-library-wizard.md)