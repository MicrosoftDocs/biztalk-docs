---
title: "Binding Files and Application Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings"
  - "deploying [applications], binding files"
  - "assemblies, binding files"
  - "bindings, applying"
  - "groups, assemblies"
  - "applications, binding files"
  - "binding files, applications"
  - "bindings, hosts"
  - "deploying, assemblies"
  - "updating, assemblies"
  - "assemblies, updating"
  - "hosts, bindings"
  - "binding files, assemblies"
  - "applications, moving"
  - "assemblies, deploying"
  - "binding files, about binding files"
  - "bindings, about bindings"
  - "groups, deploying"
  - "binding files, deploying"
  - "bindings, binding files"
ms.assetid: 396ad021-8001-4ed8-8b28-85b72f981fae
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Binding Files and Application Deployment
This topic provides overview information about using binding files to make BizTalk assembly and application deployment easier. You may find that binding files speed deployment in the following scenarios by avoiding the need to manually configure bindings:  
  
-   Moving an application from one deployment environment to another.  
  
-   Updating an assembly.  
  
-   Deploying an assembly to multiple BizTalk groups.  
  
## What is a binding?  
 A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party. This enables communication between different components of a BizTalk business solution. You can create bindings by using the BizTalk Server Administration console.  
  
## What is a binding file?  
 A binding file is an .xml file that contains binding information for each BizTalk orchestration, pipeline, map, or schema in the scope of a BizTalk assembly, application, or group. The binding file describes what host each orchestration is bound to and its trust level as well as the settings for each send port, send port group, receive port, receive location, and party that has been configured. You can generate binding files and then apply the bindings they contain to an assembly, application, or group to avoid needing to manually configure bindings in different deployment environments.  
  
## Why use binding files?  
 You may want to use binding files in the following scenarios.  
  
### Moving from one environment to another  
 You can use binding files to make it easier to move an application from one deployment environment to another, such as from a development environment to a test environment. This is because bindings often must be reconfigured for different deployment environments, but by using binding files, you can avoid repeatedly performing this manual configuration step.  
  
 One way you can do this is to create a library of bindings from which to select when deploying the application into a new environment. For example, you can create a binding file for your test environment and another one for your production environment and then add them both to the application. When you import the application into the test environment, you can select an option to apply the test bindings. Likewise, when you import the application into the production environment, you can select an option to apply the production bindings. This avoids the need to reconfigure bindings manually for different environments. Another way is to import bindings that you have created for the current environment after importing the application into it. This automatically applies the bindings.  
  
### Updating an assembly  
 When you update an assembly in an application, its bindings are often overwritten or else the assembly may not be bound at all, forcing you to manually reconfigure bindings. To avoid this, you can use a binding file as follows:  
  
-   **Updating the same version of an assembly.** If the assembly has early bound ports or dynamic ports, and you changed the port configuration in the BizTalk Server Administration console, the settings will be lost when you update the assembly with an assembly having the same version number. You can export a binding file for the assembly you are going to update. After updating the assembly you can import the assembly into the application and then import its binding file to reapply the previous bindings.  
  
-   **Updating an assembly with a newer version.** You can export a binding file for the assembly that you are going to update and then edit it to reflect the new assembly version. After you import the new assembly version into the application, you can import the binding file into the application to apply the bindings. For instructions on editing a binding file, see [Customizing Binding Files](../core/customizing-binding-files.md).  
  
### Deploying an assembly to multiple BizTalk groups  
 When you deploy an assembly into multiple BizTalk groups, you can transport the bindings for the assembly along with the assembly. This avoids the need to separately configure the bindings for the assembly in each group. You can do this as follows:  
  
1.  Create a binding file for the assembly that you want to deploy by exporting the assembly's bindings.  
  
2.  Add the assembly and its binding file to an application. If you are deploying the assembly separately from other artifacts, the application can contain only the assembly and the binding file.  
  
3.  Export an .msi file for the application, being sure to select the binding file to export as well.  
  
4.  Import the application .msi file into the BizTalk groups and applications where you want to deploy it. The bindings in the file are automatically applied to the assembly on import.  
  
## How can I generate and use binding files?  
 A binding file is not automatically generated for a BizTalk assembly, application, or group, but you can generate a binding file by exporting bindings, as described in [Exporting Bindings](../core/exporting-bindings6.md). You can then import the binding file into an application or group, as described in [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md) and [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md), which automatically applies its bindings.  
  
 Alternatively, you can add the binding file to an application so that its bindings are applied when the application is imported into another group, rather than being applied immediately, as described in [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md). Using the last method, you can add multiple binding files to an application and optionally specify a target deployment environment for each one. When you import the application, you can then select which bindings to apply, based on the target deployment environment, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). Using the last method, you can also import separate binding files for the different assemblies in your application.  
  
 You can edit binding files after you generate them to change their binding information. For more information, see [Customizing Binding Files](../core/customizing-binding-files.md).  
  
## How are bindings applied?  
 Bindings are applied when a binding file is imported into an application, or when an application is imported into a new BizTalk group. When using binding files, it is important to understand how artifacts are bound to hosts and in the order in which bindings are applied.  
  
### Binding to hosts  
 When bindings are exported either separately or as part of an application, hosts and trust levels are stored in the binding file as follows:  
  
- **Send Port.** Trust level of the host associated with the send handler.  
  
- **Receive Location.** Trust level of the host associated with the receive handler.  
  
- **Orchestration.** Trust Level of the host.  
  
  When the bindings are imported into an application, or an application is imported from the .msi file into a new BizTalk group, hosts and trust levels in the binding files are matched to hosts and trust levels in the application, as follows:  
  
- **Send Port.** The send port is bound to a send handler of the same name and bound to a host with the same trust level as that stored in the binding file.  
  
- **Receive Location.** The receive location is bound to a receive handler of the same name and bound to a host with the same trust level as that stored in the binding file.  
  
- **Orchestrations.** The orchestration is bound to a host with the same name and trust level and as that in the binding file.  
  
### Order in which bindings are applied  
 When you import an application, bindings are applied in the following order:  
  
1. Application bindings generated by BizTalk Server that were not explicitly added to the application via a binding file, but that were explicitly selected by the user for export into the application .msi file.  
  
2. Bindings in binding files that have been added to the application, and which do not have a target deployment environment specified. These bindings are applied in no specific order.  
  
3. Bindings in binding files that have been added to the application, and which have an associated target deployment environment that matches the deployment environment selected for application import. These bindings are applied in no specific order.  
  
   As bindings are applied during the import process, bindings that have already been applied are overwritten by new bindings that have the same name. In other words, the last binding of a particular name to be applied takes effect.  
  
   For example, if an existing application includes a send port named SendPort1, and a binding file is applied that describes a send port with the same name, the settings in the binding file will overwrite the existing settings for SendPort1. If an existing application includes an orchestration named ErrorHandling.ErrorHandler.ResubmitLogic, for example, and a binding file describes an orchestration having the same name, all of the existing bindings for the orchestration will be written with the bindings in the binding file.  
  
## See Also  
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)