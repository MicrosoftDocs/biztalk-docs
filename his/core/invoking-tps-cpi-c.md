---
title: "Invoking TPs (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 212388b4-9c9c-4f5a-be1b-200746078203
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Invoking TPs (CPI-C)
An invoking transaction program (TP) can be located on any system on the SNA network. An invoking TP identifies itself by issuing [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md), which specifies the name of the invoking TP and the symbolic destination name to be used. A local logical unit (LU) alias can be specified for the invoking TP by using a registry or environment variable, as shown in the following table.  
  
|Operating system on computer that contains invoking TP|Location and name of variable|  
|------------------------------------------------------------|-----------------------------------|  
|Windows Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, or Windows Server 2012|Location in Windows registry:<br /><br /> HKEY_LOCAL_MACHINE   SYSTEM     CurrentControlSet       Services         SnaBase           Parameters             Client *\<exename>*:REG_SZ:*localLUalias*<br /><br /> Any *exename* registry entries under the Client key represent the file names of Win32 executable files (without the file extension) for any invoking TPs. A REG_SZ value associated with each *exename* registry entry specifies the local LU alias for the invoking TP.<br /><br /> For example, the APING.EXE Common Programming Interface for Communications (CPI-C) sample included with the Microsoft® Host Integration Server software development kit (SDK) would have the following registry entry:<br /><br /> HKEY_LOCAL_MACHINE   SYSTEM     CurrentControlSet       Services         SnaBase           Parameters             Client                APING:REG_SZ:*localLUalias*|  
  
 The registry parameter for the local LU alias takes greatest precedence when associating a local LU to an invoking CPI-C application. If a registry value is not configured, two other methods are used to associate a local LU to the CPI-C application.  
  
 A local APPC LU can be associated with the user context under which the CPI-C application is running A local APPC LU can be configured by checking the **member of default local APPC LU pool** check box. Of the two possible options, a local LU associated with user context has the higher precedence.  
  
 If the local LU alias is not specified in a registry or environment variable, SNA service must be configured to supply it through one of these two types of default local LUs. Otherwise, [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md) will fail. For more information, see [Invoking TPs and SNA Service Configuration](../core/invoking-tps-and-sna-service-configuration-cpi-c.md).  
  
 Next, the symbolic destination name specified in [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md) provides the name of the invokable (or partner) TP and the partner LU alias (the LU alias to be used by the invokable TP). With this information available, the invoking TP can issue the [Allocate](../Topic/Allocate%20\(CPI-C\)1.md) call.  
  
 After a TP successfully issues an Allocate call, an allocation request flows. For more information about what happens after an invoking TP requests an invokable TP, see [Matching Invoking and Invokable TPs](../core/matching-invoking-and-invokable-tps-cpi-c.md).