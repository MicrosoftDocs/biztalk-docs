---
title: "Important Considerations for Updating Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "updating, applications"
  - "applications, planning"
  - "applications, updating"
  - "planning, applications"
  - "planning, updating"
  - "updating, planning"
ms.assetid: e7690bdf-943d-4bb6-b8cd-a6841b722d40
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Important Considerations for Updating Applications
The following are important issues to consider before updating an application, especially one that is running in a production environment.  
  
## General considerations  
  
-   Parties and rules are visible at a group scope, so adding additional parties and rules could disrupt other applications.  
  
-   If you are undeploying an artifact on which another artifact depends, the dependent artifact must be undeployed first.  
  
    > [!NOTE]
    >  The BizTalk Server Administration console will display a warning and prevent you from undeploying artifacts in the incorrect order.  
  
-   If a BizTalk assembly in an existing application is updated, you may need to restart host instances for the changes to take effect. Restarting a host instance stops all other applications that are running on the host instance.  
  
-   If you use Visual Studio to deploy an application into a production environment (which we strongly recommend against doing) and the Restart Host Instances option is set to True in project properties, all host instances will restart when you deploy the application, including those that are not associated with this application. This will stop all other applications that are running on any host instance on the local computer.  
  
-   If you want to update a BizTalk Server assembly (containing an orchestration, schema, or map) which is deployed as a BizTalk application, you can do any of the following:  
  
    -   Perform a side-by-side deployment. You can appropriately modify the newer assembly typically by incrementing the version. This makes both the assemblies have a distinct fully qualified assembly name. For more information, see [How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md).  
  
    -   Replace the existing BizTalk Server assembly with a new assembly. You must stop all host instances that can possibly load the out-dated assembly, replace the out-dated assembly in the GAC, and then restart the host instances.  
  
-   If you deploy an entirely new application to replace an existing application, you must correct any references between other applications and the application that you are replacing.  
  
## Considerations for updating schemas  
  
-   If you add an assembly to an application that includes a new schema with the same message type as an existing schema in the BizTalk group, the schema with the highest version number will be used when schema resolution occurs in pipelines. In addition, if one message type refers to more than one .NET type, this ambiguity may cause pipeline execution failure. This is because schema lookup uses message type, the target namespace, and root name of the instance. This can occur for pipelines in any application that uses a schema with the same message type as the new schema. For more information about schema resolution, see [Schema Resolution in Pipeline Components](../core/schema-resolution-in-pipeline-components.md).  
  
-   When you update a schema, you must also update the maps that reference the schema (or create new maps) as well as any orchestrations that rely on the schema.  
  
-   If you increment a schema version, you should update the reference to the schema for any pipeline instances and pipeline components that use it.  
  
-   Undeploying a schema causes the previous version of the schema, if available, to become active.  
  
## Considerations for updating policies  
  
-   The highest version of a policy that is in a deployed state is used by the BizTalk Server runtime.  
  
## See Also  
 [Updating BizTalk Applications](../core/updating-biztalk-applications.md)