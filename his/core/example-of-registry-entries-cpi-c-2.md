---
title: "Example of Registry Entries (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 021d92c7-6ea3-4b17-aeec-0d726c92b8ac
caps.latest.revision: 4
---
# Example of Registry Entries (CPI-C)
For an autostarted invokable transaction program (TP) called **BounceTP** and running as a service, the following registry entries might be added to a client computer. The entries would be added to **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**, under the subkeys shown in bold type.  
  
> [!NOTE]
>  In the following list, the parameters listed directly under the **BounceTP** key (such as **DisplayName** and **ErrorControl**) are service parameters created when TPSETUP or similar code is run to install the TP. These parameters should be created by TPSETUP or similar code. They should not be set manually. For more information about TPSETUP, see [CPI-C Samples](../core/cpi-c-samples.md).  
  
 **BounceTP**  
 **DisplayName:**REG_SZ:BounceTP**ErrorControl:**REG_DWORD:0x1**ImagePath:**REG_EXPAND_SZ:c:\sna\system\bouncetp.exe**ObjectName:**REG_SZ:LocalSystem**Start:**REG_DWORD:0x3**Type:**REG_DWORD:0x10  
  
 **Linkage**  
  
 **OtherDependencies:**REG_MULTI_SZ:SnaBase  
  
 **Parameters**  
  
 **SNAServiceType:**REG_DWORD:0x5**LocalLU:**REG_SZ:JohnDoe**Parameters:**REG_SZ:Arg1 Arg2 Arg3**Timeout:**REG_DWORD:0x100**ConversationSecurity:**REG_SZ:yes**AlreadyVerified:**REG_SZ:no**JohnDoe:**REG_SZ:SecretPassword