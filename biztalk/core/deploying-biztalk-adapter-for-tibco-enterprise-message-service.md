---
title: "Import bindings for TIBCO EMS | Microsoft Docs"
description: Deploy your BizTalk Adapter for TIBCO Enterprise Message Service applications using Import Bindings feature in BizTalk Server
ms.custom: ""
ms.date: "10/23/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69dae448-4ec6-4a56-a628-bb447bc21b62
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploy TIBCO EMS ports and assemblies

## Overview
With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exports send ports/receive location configuration into an XML file.  
  
 You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:  
  
- Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.  
  
- Install or uninstall the assemblies in the global assembly cache (GAC).  
  
- Import or export BizTalk assembly binding information to and from binding files.  
  
  For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  Microsoft BizTalk Adapter for TIBCO Enterprise Message Service only requires that you have Visual Studio on a source (development) computer. Visual Studio is not required on the production computer.  

## Confirm your setup
Before you use BizTalk Server to import a binding file, verify the following:  
  
-   The folders for the responses must exist and be identical on the new computer, or edit the binding file.  
  
-   TIBCO Enterprise Message Service system passwords, if present in the configuration, must be saved as ***** in the binding file. See **Limitations** in this topic.


## Clean the target computer
Deployment overwrites the receive location configuration. When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  

Before you import, remove any send ports and receive locations bound to the orchestration.  
  
If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs`  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs`
  

For example, at a command prompt, run:  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## Limitations
The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
 This is a known limitation. When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully finishes.  
  
 
### Password Limitation Workaround  
 To work around this password limitation, you can use one of the following methods:  
  
-   Edit the binding file before importing by replacing the stars with plain text.  
  
    > [!CAUTION]
    >  This is not recommended for security reasons.  
  
-   Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
    > [!NOTE]
    >  This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.  
  
-   Verify the Logical system and the Transmit and Receive services.  

## Next steps
[Use BizTalk Server Exception Handling in your orchestration](../core/using-biztalk-server-exception-handling5.md)