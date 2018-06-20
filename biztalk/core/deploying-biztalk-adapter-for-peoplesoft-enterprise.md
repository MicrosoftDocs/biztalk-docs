---
title: "Import PeopleSoft applications | Microsoft Docs"
description: Use an XML binding file to import your PeopleSoft adapter applications into BizTalk Server, and read any limitations when importing 
ms.custom: ""
ms.date: "10/19/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f53d1b4-e1df-41ff-b554-1bb1d20b9111
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploy BizTalk Adapter for PeopleSoft Enterprise
This section provides information about deploying BizTalk Adapter for PeopleSoft Enterprise.  

## Overview
Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exports the send ports/receive location configuration into an XML file.  
  
 You use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform these tasks:  
  
- Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.  
  
- Install or uninstall the assemblies in the global assembly cache (GAC).  
  
- Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files.  
  
To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  The Microsoft BizTalk Adapter for PeopleSoft Enterprise only requires that you have Visual Studio on a source (development) computer. Visual Studio is not required on the production computer.  

## Confirm your setup
Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:  
  
-   The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files. Verify that the location of these files is the same on the new computer—or edit the binding file.  
  
-   The folders for the responses must exist and be identical on the new computer—or edit the binding file.  
  
-   PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file. See **Limitations** in this topic.

> [!NOTE]
>  Deployment overwrites receive location configuration. When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  
  
 For step-by-step directions about importing binding files, see [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md). 
  
## Clean the target computer
To clean the target computer for deploying the new application, remove send ports and receive locations bound to the orchestration.  
  
If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**  
  
For example, at a command prompt, run:  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## Limitations
The Transport Adapter password is stored as asterisks (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation finishes.  
  

### Work around the password limitation  

**Option 1**   
  
- Before you import, update the binding file by replacing the asterisks with plain text.  
  
  > [!CAUTION]
  >  This practice is not recommended for security reasons.  
  
- Before you import, update the binding fileby replacing the asterisks with some junk value (that is, not the correct password). After you import, enter the correct password in the **Transport Properties** in BizTalk Server Administration.  
  
  > [!NOTE]
  >  This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.  
  
**Option 2**  
  
-   Use Enterprise Single Sign-On (SSO) instead of using passwords. Using the SSO option requires an import of the binding file.  
  
- Verify the logical system and the Transmit and Receive services. 
  
## Next steps
[Use BizTalk Server Exception Handling in your orchestration](../core/using-biztalk-server-exception-handling2.md)