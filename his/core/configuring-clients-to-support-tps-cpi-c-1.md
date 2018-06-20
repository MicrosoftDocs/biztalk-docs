---
title: "Configure Clients to Support TPs (CPI-C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b02b239d-04a2-4707-a8fa-d26222019d3d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configure Clients to Support TPs (CPI-C)

## Overview
On client computers, invokable transaction programs (TPs) are configured through the Windows registry.  

> [!NOTE]
>  On client computers, the recommended method for setting registry variables for autostarted invokable TPs is to use the sample TP configuration program, TPSETUP. Compile INSTALL.C, the source code for TPSETUP, for the target environment. When you write an installation program for autostarted invokable TPs, it is recommended that you add code similar to TPSETUP to the installation program.   

 For clients it is recommended that autostarted invokable TPs be written as Windows services. Be sure to include code like that in TPSETUP in the program that installs your TPs. Among other things, TPSETUP shows how to use the **CreateService** function when installing a TP.  

 The following table lists the registry entries used for the types of invokable TPs that can be run on Windows client computers.  


|                                                        Type of TP                                                         |                                                                            Location in registry                                                                             |                                                                                                                                                                                                                                                                                                           Possible registry entries                                                                                                                                                                                                                                                                                                           |
|---------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                Autostarted invokable TP running as a service on a client.                                 |                    **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services** <br /> ***TPName***<br /><br /> (and subkeys)                     | Registry entries created by the **CreateService** call, including entries that specify the path, display name, and other characteristics of the service.<br /><br /> —plus—<br /><br /> Linkage OtherDependencies:REG_MULTI_SZ:SnaBase<br /><br /> Parameters SNAServiceType:REG_DWORD:0x5 LocalLU:REG_SZ:*LUalias* Parameters:REG_SZ:*ParameterList* Timeout:REG_DWORD:*number* AcceptNames:REG_SZ:*TPNameList* ConversationSecurity:REG_SZ:{ YES &#124; NO } AlreadyVerified:REG_SZ:{ YES &#124; NO }*Username1*:REG_SZ:*Password1* ...*UsernameX*:REG_SZ:*PasswordX*<br /><br /> For more information, see the notes following this table. |
| Autostarted invokable TP running as an application on a client. For more information, see the notes following this table. | **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services**<br /> **SnaBase**<br /> **Parameters**<br /> **TPs** <br /> ***TPName***  Parameters |                        <strong>SNAServiceType:</strong>REG_DWORD:{ 0x5 &#124; 0x6 }<strong>PathName:</strong>REG_EXPAND_SZ:*path*<strong>LocalLU:</strong>REG_SZ:*LUalias*<strong>Parameters:</strong>REG_SZ:*ParameterList*<strong>TimeOut:</strong>REG_DWORD:*number*<strong>AcceptNames:</strong>REG_SZ:*TPNameList*<strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }<strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }<strong>*Username1*:</strong>REG_SZ:*Password1* ...<strong>*UsernameX*:</strong>REG_SZ:*PasswordX*<br /><br /> For more information, see the notes following this table.                        |
|                              Operator-started invokable TP running as a service on a client.                              |                    **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services** <br /> ***TPName***<br /><br /> (and subkeys)                     |                                  Registry entries created by the **CreateService** call, including entries that specify the path, display name, and other characteristics of the service.<br /><br /> —plus—<br /><br /> Linkage OtherDependencies:REG_MULTI_SZ:SnaBase<br /><br /> Parameters SNAServiceType:REG_DWORD:0x1A LocalLU:REG_SZ:*LUalias* Timeout:REG_DWORD:*number* ConversationSecurity:REG_SZ:{ YES &#124; NO } AlreadyVerified:REG_SZ:{ YES &#124; NO }*Username1*:REG_SZ:*Password1* ...*UsernameX*:REG_SZ:*PasswordX*<br /><br /> For more information, see the note following this table.                                  |
|                           Operator-started invokable TP running as an application on a client.                            | **HKEY_LOCAL_MACHINE**<br /> **SYSTEM**<br /> **CurrentControlSet**<br /> **Services**<br /> **SnaBase**<br /> **Parameters**<br /> **TPs** <br /> ***TPName***  Parameters |                                                                                                       <strong>SNAServiceType:</strong>REG_DWORD:0x1A<strong>LocalLU:</strong>REG_SZ:*LUalias*<strong>TimeOut:</strong>REG_DWORD:*number*<strong>ConversationSecurity:</strong>REG_SZ:{ YES &#124; NO }<strong>AlreadyVerified:</strong>REG_SZ:{ YES &#124; NO }<strong>*Username1*:</strong>REG_SZ:*Password1* ...<strong>*UsernameX*:</strong>REG_SZ:*PasswordX*<br /><br /> For more information, see the note following this table.                                                                                                        |

> [!NOTE]
>  Before an autostarted TP can be started as an application on a client, the TPSTART program must be started. 

> [!NOTE]
>  AlreadyVerified and Username/Password entries are used only if ConversationSecurity is set to YES.  

## Next steps

-   [Registry Entries for Clients (CPI-C)](../core/registry-entries-for-clients-cpi-c-1.md)  

-   [Example of Registry Entries (CPI-C)](../core/example-of-registry-entries-cpi-c-1.md)