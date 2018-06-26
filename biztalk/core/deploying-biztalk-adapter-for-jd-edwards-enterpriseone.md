---
title: "Import JD Edwards EnterpriseOne applications | Microsoft Docs"
description: Confirm the setup, import the application binding file, and review the limitations of the JD Edwards EnterpriseOne adapter in BizTalk 
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 852f948b-48ba-4ae2-b1eb-7c88c1542a52
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Import the JD Edwards EnterpriseOne application
  
## Overview
With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exports the send ports/receive location configuration into an XML file.  
  
 You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:  
  
- Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database  
  
- Install or uninstall the assemblies in the global assembly cache (GAC)  
  
- Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files  
  
To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne only requires that you have Visual Studio on a source (development) computer. Visual Studio is not required on the production computer.  

## Confirm your setup
Before you use the BizTalk Server to import a binding file, you must verify the following:  
  
-   The CLASSPATH is pointing to a specific location for the JD Edwards EnterpriseOne-specific files. Verify that the location of these files is the same on the new computer, or edit the binding file.  
  
-   The folders for the responses exist and are identical on the new computer, or edit the binding file.  
  
-   JD Edwards EnterpriseOne system passwords, if present in the configuration, are saved as ***** in the binding file. For more information, see **Limitations** in this topic.

## Clean the target computer
When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.  
  
Before you import, remove Send ports and Receive locations bound to the orchestration. If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  

For example, from a command prompt run:  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
## Limitations
The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.  
  
 Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully completes.  
  
### Work around the password limitation  
  
1.  Use Enterprise Single Sign-On instead of using passwords. Using the SSO option requires no extra work; only an import of the binding file.  
  
2.  Verify the Logical system and the Transmit and Receive services.  


## Next steps
[Use BizTalk Server Exception Handling in your orchestration](../core/using-biztalk-server-exception-handling3.md)