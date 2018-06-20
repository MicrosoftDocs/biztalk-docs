---
title: "Example of Registry Entries (CPI-C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3dcf6fb5-f0fd-4124-8b91-96982883ca6f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Example of Registry Entries (CPI-C)
For an autostarted invokable transaction program (TP) called **BounceTP** and running as a service, the following registry entries might be added to a client computer. The entries would be added to **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**, under the subkeys shown in bold type.  
  
> [!NOTE]
>  In the following list, the parameters listed directly under the **BounceTP** key (such as **DisplayName** and **ErrorControl**) are service parameters created when TPSETUP or similar code is run to install the TP. These parameters should be created by TPSETUP or similar code. They should not be set manually. 
  
 **BounceTP**  
 <strong>DisplayName:</strong>REG_SZ:BounceTP<strong>ErrorControl:</strong>REG_DWORD:0x1<strong>ImagePath:</strong>REG_EXPAND_SZ:c:\sna\system\bouncetp.exe<strong>ObjectName:</strong>REG_SZ:LocalSystem<strong>Start:</strong>REG_DWORD:0x3<strong>Type:</strong>REG_DWORD:0x10  
  
 **Linkage**  
  
 <strong>OtherDependencies:</strong>REG_MULTI_SZ:SnaBase  
  
 **Parameters**  
  
 <strong>SNAServiceType:</strong>REG_DWORD:0x5<strong>LocalLU:</strong>REG_SZ:JohnDoe<strong>Parameters:</strong>REG_SZ:Arg1 Arg2 Arg3<strong>Timeout:</strong>REG_DWORD:0x100<strong>ConversationSecurity:</strong>REG_SZ:yes<strong>AlreadyVerified:</strong>REG_SZ:no<strong>JohnDoe:</strong>REG_SZ:SecretPassword