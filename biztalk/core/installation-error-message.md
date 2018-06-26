---
title: "Installation Error Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation, error message"
  - "error messages, installation"
ms.assetid: 593b033f-03da-43ae-a948-f87aa5e4bccd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installation Error Message
After you install Microsoft BizTalk Adapter for TIBCO Enterprise Message Service, defining a send or receive location for it might result in the following error:  
  
 The Messaging Engine failed to add a receive URL "\< send/receive location URL\>" to the adapter "TIBCO EMS". Reason: "File or assembly name TIBCO.EMS, or one of its dependencies, was not found."  
  
## Possible Causes  
 This error usually has one of the following causes.  
  
### Assembly Not in GAC  
 BizTalk Adapter for TIBCO EMS is a .NET Framework application, and uses the .NET Framework assembly, TIBCO.EMS. This assembly must be present in the .NET Framework global assembly cache (GAC) for the .NET Framework to find it at run time.  
  
#### Solution  
 To determine if the assembly is present in the GAC, open a command prompt and type the following command:  
  
 `GACUTIL /L TIBCO.EMS`  
  
 If the result shows zero items, you must add the assembly to the GAC. To do this, open a command prompt, change directories to your TIBCO EMS installation clients\cs directory (the default installation location is C:\TIBCO\EMS\Clients\CS), and run the following command:  
  
 `GACUTIL /i TIBCO.EMS.DLL`  
  
### Different Version of Assembly in GAC  
 The TIBCO.EMS.dll assembly is in the GAC, but it is a different version from the one used to build BizTalk Adapter for TIBCO EMS. If the TIBCO.EMS.dll that is installed on the computer is from a product version 4.2 or above, it should be compatible with the version used to build the adapter (you can verify that information with TIBCO).  
  
#### Solution  
 The .NET Framework provides a way to work around this problem. It is called *binding redirection*, which uses a configuration file.  
  
 Follow these steps to eliminate the error message:  
  
1. With any text editor, open the file BTSNTSVC.exe.config.  
  
    The file is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directory (the default installation location is: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).  
  
2. Add the following entry to the BTSNTSVC.exe.config file, as a child of the \<assemblyBinding\> element:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name='TIBCO.EMS'  
        publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
    <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
        newVersion='1.0.0.0' />  
</dependentAssembly>  
```  
  
 If the BTSNTSVC.exe.config file has not been previously modified, the \<assemblyBinding\> element would not look like this:  
  
```  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
    <probing privatePath="BizTalk Assemblies;Developer  
        Tools;Tracking;Tracking\interop" />  
    <dependentAssembly>  
        <assemblyIdentity name='TIBCO.EMS'  
            publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
        <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
            newVersion='1.0.0.0' />  
    </dependentAssembly>  
</assemblyBinding>  
```  
  
1. In a command prompt, type the command: `GACUTIL /L TIBCO.EMS`.  
  
2. Copy the TIBCO.EMS assembly version number from the output.  
  
   > [!CAUTION]
   >  Two version numbers appear: one is the version number of the gacutil utility. You want the second version number, which appears just after **Version=**.  
  
3. Paste the version number in the BTSNTSVC.exe.config file, between the quotation marks, right after **newVersion=** (bold characters in the previous XML example).  
  
4. Save the modified BTSNTSVC.exe.config file.  
  
5. Restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host.  
  
## See Also  
 [Troubleshooting TIBCO Enterprise Message Service](../core/troubleshooting-tibco-enterprise-message-service.md)