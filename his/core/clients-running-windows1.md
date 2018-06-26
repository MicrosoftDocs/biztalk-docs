---
title: "Clients Running Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df09f0b6-3621-473c-b3a1-8bae02c2c660
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Clients Running Windows
On clients running Microsoft Windows, invokable TPs are configured through the Windows registry.  

> [!NOTE]
>  The recommended method for setting registry variables for autostarted invokable TPs is to use the sample TP configuration program, TPSETUP. Compile INSTALL.C, the source code for TPSETUP, for the Windows environment. When you write an installation program for autostarted invokable TPs, it is recommended that you add code similar to TPSETUP to the installation program.  

 It is recommended that autostarted invokable TPs be written as Windows services. Be sure to include code like that in TPSETUP in the program that installs your TPs. Among other things, TPSETUP shows how to use the **CreateService** function when installing a TP. For important information about how services work under Windows, see the Microsoft Developer Network (MSDN®) Platform Software Development Kit.  

 The following table lists the registry entries used for the types of invokable TPs that can be run on Windows clients:  


|                     Type of TP                     |                                                                            Location in registry                                                                             |                                                                                                                                                                                                                                                                                                                                   Possible registry entries                                                                                                                                                                                                                                                                                                                                    |
|----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Autostarted invokable TP running as a service    |                    **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services** <br /> ***TPName***<br /><br /> (and subkeys)                     | Registry entries created by the **CreateService** call, including entries that specify the path, display name, and other characteristics of the service.<br /><br /> —plus—<br /><br /> <strong>Linkage OtherDependencies:</strong>REG_MULTI_SZ:SnaBase<br /><br /> <strong>Parameters SNAServiceType:</strong>REG_DWORD:0x5<strong>LocalLU:</strong>REG_SZ:*LUalias*<strong>Parameters:</strong>REG_SZ:*ParameterList*<strong>Timeout:</strong>REG_DWORD:*number*<strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }<strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }2<strong>*Username1:*</strong>REG_SZ:*Password1*2 ...<strong>*UsernameX:*</strong>REG_SZ:*PasswordX*2 |
| Autostarted invokable TP running as an application | **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services**<br /> **SnaBase**<br /> **Parameters**<br /> **TPs** <br /> ***TPName***  Parameters |                                                                                                          <strong>SNAServiceType:</strong>REG_DWORD:{ 0x5 &#124; 0x6 }<strong>PathName:</strong>REG_EXPAND_SZ:*path*<strong>LocalLU:</strong>REG_SZ:*LUalias*<strong>Parameters:</strong>REG_SZ:*ParameterList*<strong>TimeOut:</strong>REG_DWORD:*number*<strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }<strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }2<strong>*Username1*:</strong>REG_SZ:*Password1*2 ...<strong>*UsernameX*:</strong>REG_SZ:*PasswordX*2                                                                                                          |
| Operator-started invokable TP running as a service |                    **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services** <br /> ***TPName***<br /><br /> (and subkeys)                     |                         Registry entries created by the **CreateService** call, including entries that specify the path, display name, and other characteristics of the service.<br /><br /> —plus—<br /><br /> <strong>Linkage OtherDependencies:</strong>REG_MULTI_SZ:SnaBase<br /><br /> <strong>Parameters SNAServiceType:</strong>REG_DWORD:0x1A<strong>LocalLU:</strong>REG_SZ:*LUalias*<strong>Timeout:</strong>REG_DWORD:*number*<strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }<strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }2<strong>*Username1:*</strong>REG_SZ:*Password1*2 ...<strong>*UsernameX:*</strong>REG_SZ:*PasswordX*2                          |
|           Operator-started invokable TP            |    **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services**<br /> **SnaBase**<br /> **Parameters**<br /> **TPs**  ***TPName***  Parameters    |                                                                                                                                                                 <strong>SNAServiceType:</strong>REG_DWORD:0x1A<strong>LocalLU:</strong>REG_SZ:*LUalias*<strong>TimeOut:</strong>REG_DWORD:*number*<strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }<strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }2<strong>*Username1*:</strong>REG_SZ:*Password1*2 ...<strong>*UsernameX*:</strong>REG_SZ:*PasswordX*2                                                                                                                                                                 |

> [!NOTE]
>  Before an autostarted TP can be started as an application on a Windows client, the TPSTART program must be started. 

> [!NOTE]
>  **AlreadyVerified** and **Username/Password** entries are used only if **ConversationSecurity** is set to YES.