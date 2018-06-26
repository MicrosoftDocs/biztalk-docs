---
title: "Exporting Bindings6 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings, exporting"
  - "exporting, bindings"
ms.assetid: 052a429e-3237-44d4-8933-00aa5edfb212
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Exporting Bindings
The topics in this section describe how to export bindings for a BizTalk group, assembly, or application into an .xml file. (Bindings define how hosts, send ports, send port groups, receive ports, receive locations, parties are associated with orchestrations, pipelines, maps, and schemas.) You can then import the bindings from the .xml file into another group or application. Importing bindings overwrites any existing bindings of the same name in the group or application. You can also add bindings to an application, which does not overwrite existing bindings. The bindings that you add do not take effect until you import the application.  
  
 You may find that using binding files speeds application deployment in the following scenarios by avoiding the need to manually configure bindings:  
  
- Moving an application from one deployment environment to another.  
  
- Updating an assembly.  
  
- Deploying an assembly together with its bindings to multiple BizTalk groups.  
  
  For more information about using binding files for these purposes, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
  For more information about importing and adding bindings, see [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md), [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md), and [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).  
  
> [!IMPORTANT]
>  The binding file may contain sensitive data. Be sure to take steps to secure the file.  
  
> [!NOTE]
>  For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file. After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function. You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location. For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
## In This Section  
  
-   [How to Export Bindings for a BizTalk Group](../core/how-to-export-bindings-for-a-biztalk-group.md)  
  
-   [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md)  
  
-   [How to Export Bindings for a BizTalk Assembly](../core/how-to-export-bindings-for-a-biztalk-assembly.md)  
  
-   [How to Export Bindings for an EDI-AS2 Solution](../core/how-to-export-bindings-for-an-edi-as2-solution.md)