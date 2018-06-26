---
title: "Import BizTalk Adapter for JD Edwards OneWorld | Microsoft Docs"
description: Import the application binding file, and review any limitations of the JD Edwards OneWorld adapter in BizTalk 
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f308d2fe-39dd-4008-94ed-292c4c26fe06
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Import the JD Edwards EnterpriseOne application
  
## Overview
Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer. BizTalk Server exports the send ports/receive location configuration into an XML file.  
  
 You can use BizTalk Server to do the following tasks:  
  
-   Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database  
  
-   Install or uninstall the assemblies in the global assembly cache (GAC)  
  
-   Import or export BizTalk Server assembly binding information to and from binding files  

To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  The Microsoft BizTalk Adapter for JD Edwards OneWorld only requires that you have Visual Studio on a source (development) computer. Visual Studio is not required on the production computer.  

## Confirm your setup
Before you use the BizTalk Server to import a binding file, verify the following:  
  
-   The CLASSPATH is pointing to a specific location for the JD Edwards-specific files. Verify that the location of these files is the same on the new computer, or edit the binding file.  
  
-   The folders for the responses exist and are identical on the new computer, or edit the binding file.  
  
-   JD Edwards system passwords, if present in the configuration, are saved as ***** in the binding file. See **Limitations** in this topic.

  
> [!NOTE]
>  Deployment overwrites Receive Location configuration. When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  
  
  
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
  
## Limitations
The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format. Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password). Then enter the correct password using the **Transport Properties** page after importing the binding file.  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully completes.  
  
> [!NOTE]
>  When importing an .msi file into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message. A supported hotfix is available from Microsoft along with a full description of the error at [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).  
  
### Work around the password limitation  

**Option 1**  

- Before you import, update the binding file by replacing the asterisks with plain text.  
  
    > [!CAUTION]
    >  This is not recommended for security reasons.  
  
- Before you import, update the binding file by replacing the asterisks with some junk value (that is, not the correct password). After you import, enter the correct password using the **Transport Properties**.  
  
    > [!NOTE]
    >  This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.  
  
**Option 2**  
  
1.  Use Enterprise Single Sign-On instead of using passwords. Using the SSO option requires no extra work; only an import of the binding file.  
  
2.  Verify the Logical system and the Transmit and Receive services.  

## Next steps
[Use BizTalk Server Exception Handling in your orchestration](../core/using-biztalk-server-exception-handling1.md)