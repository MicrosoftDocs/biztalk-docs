---
title: "Import bindings for TIBCO Rendezvous | Microsoft Docs"
description: Deploy your BizTalk Adapter for TIBCO Rendezvous applications using Import Bindings feature in BizTalk Server
ms.custom: ""
ms.date: "10/24/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec5751a9-0a08-4cf8-a3ef-e51e488a4180
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploy TIBCO Rendezvous ports and assemblies
  
## Overview
Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer. The wizard exports the send ports/receive location configuration into an XML file.  
  
 You use BizTalk Server to do the following tasks:  
  
- Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database.  
  
- Install or uninstall the assemblies in the global assembly cache (GAC).  
  
- Import or export BizTalk Server assembly binding information to and from binding files.  
  
  For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for TIBCO Rendezvous only requires that you have Visual Studio on a source (development) computer. Visual Studio is not required on the production computer.  

## Confirm your setup

Before you use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, confirm that the folders for the responses exist, and that they are identical on the new computer, or you must edit the binding file.  
  
## Clean the target computer
Deployment overwrites the receive location configuration. When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  
  
Before you import, remove send ports and receive locations bound to the orchestration.  
  
If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
For example, at a command prompt, run:  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## Next steps
[Use BizTalk Server Exception Handling in your orchestration](../core/using-biztalk-server-exception-handling4.md)  
[Troubleshoot](../core/troubleshooting-tibco-rendezvous.md)