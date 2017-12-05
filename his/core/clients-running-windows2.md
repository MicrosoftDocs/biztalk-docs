---
title: "Clients Running Windows2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a24cae0-da5a-4e7e-91dc-36c6954753e3
caps.latest.revision: 5
---
# Clients Running Windows
On clients running Microsoft Windows, invokable TPs are configured through the Windows registry.  
  
> [!NOTE]
>  The recommended method for setting registry variables for autostarted invokable TPs is to use the sample TP configuration program, TPSETUP. Compile INSTALL.C, the source code for TPSETUP, for the Windows environment. When you write an installation program for autostarted invokable TPs, it is recommended that you add code similar to TPSETUP to the installation program. For information about TPSETUP, see [APPC Samples](../core/appc-samples.md).  
  
 It is recommended that autostarted invokable TPs be written as Windows services. Be sure to include code like that in TPSETUP in the program that installs your TPs. Among other things, TPSETUP shows how to use the **CreateService** function when installing a TP. For important information about how services work under Windows, see the Microsoft Developer Network (MSDN®) Platform Software Development Kit.  
  
 The following table lists the registry entries used for the types of invokable TPs that can be run on Windows clients:  
  
|Type of TP|Location in registry|Possible registry entries|  
|----------------|--------------------------|-------------------------------|  
|Autostarted invokable TP running as a service|**HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services** <br /> ***TPName***<br /><br /> (and subkeys)|Registry entries created by the **CreateService** call, including entries that specify the path, display name, and other characteristics of the service.<br /><br /> —plus—<br /><br /> **Linkage OtherDependencies:**REG_MULTI_SZ:SnaBase<br /><br /> **Parameters SNAServiceType:**REG_DWORD:0x5**LocalLU:**REG_SZ:*LUalias***Parameters:**REG_SZ:*ParameterList***Timeout:**REG_DWORD:*number***ConversationSecurity:**REG_SZ:{ YES &#124; NO }**AlreadyVerified:**REG_SZ:{ YES &#124; NO }2***Username1:***REG_SZ:*Password1*2 ...***UsernameX:***REG_SZ:*PasswordX*2|  
|Autostarted invokable TP running as an application|**HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services**<br /> **SnaBase**<br /> **Parameters**<br /> **TPs** <br /> ***TPName***  Parameters|**SNAServiceType:**REG_DWORD:{ 0x5 &#124; 0x6 }**PathName:**REG_EXPAND_SZ:*path***LocalLU:**REG_SZ:*LUalias***Parameters:**REG_SZ:*ParameterList***TimeOut:**REG_DWORD:*number***ConversationSecurity:**REG_SZ:{ YES &#124; NO }**AlreadyVerified:**REG_SZ:{ YES &#124; NO }2***Username1*:**REG_SZ:*Password1*2 ...***UsernameX*:**REG_SZ:*PasswordX*2|  
|Operator-started invokable TP running as a service|**HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services** <br /> ***TPName***<br /><br /> (and subkeys)|Registry entries created by the **CreateService** call, including entries that specify the path, display name, and other characteristics of the service.<br /><br /> —plus—<br /><br /> **Linkage OtherDependencies:**REG_MULTI_SZ:SnaBase<br /><br /> **Parameters SNAServiceType:**REG_DWORD:0x1A**LocalLU:**REG_SZ:*LUalias***Timeout:**REG_DWORD:*number***ConversationSecurity:**REG_SZ:{ YES &#124; NO }**AlreadyVerified:**REG_SZ:{ YES &#124; NO }2***Username1:***REG_SZ:*Password1*2 ...***UsernameX:***REG_SZ:*PasswordX*2|  
|Operator-started invokable TP|**HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services**<br /> **SnaBase**<br /> **Parameters**<br /> **TPs**  ***TPName***  Parameters|**SNAServiceType:**REG_DWORD:0x1A**LocalLU:**REG_SZ:*LUalias***TimeOut:**REG_DWORD:*number***ConversationSecurity:**REG_SZ:{ YES &#124; NO }**AlreadyVerified:**REG_SZ:{ YES &#124; NO }2***Username1*:**REG_SZ:*Password1*2 ...***UsernameX*:**REG_SZ:*PasswordX*2|  
  
> [!NOTE]
>  Before an autostarted TP can be started as an application on a Windows client, the TPSTART program must be started. For more information, see [APPC Samples](../core/appc-samples.md).  
  
> [!NOTE]
>  **AlreadyVerified** and **Username/Password** entries are used only if **ConversationSecurity** is set to YES.