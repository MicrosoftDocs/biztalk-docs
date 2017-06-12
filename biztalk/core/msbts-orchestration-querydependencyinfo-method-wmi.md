---
title: "MSBTS_Orchestration.QueryDependencyInfo Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6da32e40-b5b1-43f2-891a-c81a5cc4402b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.QueryDependencyInfo Method (WMI)
Retrieves information about services that this service depends on through either a **CALL** or **START** relationship.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 QueryDependencyInfo(  
    uint32 Direction,  
    string XMLDependencyInfo  
);  
```  
  
#### Parameters  
 *Direction*  
 [in] Permissible values for this property are (1) "Downstream" and (2) "Upstream". Note that the integer values must be used in code and script.  
  
 *XMLDependencyInfo*  
 [out] XML string displaying the dependency information.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 **QueryDependencyInfo** walks the service dependency tree either upstream or downstream from the service and constructs an XML representation of the tree.  
  
 The format of the XML is illustrated in the example below where one orchestration A calls orchestration B, and they both exist in the same assembly:  
  
```  
<RootOrchestration Name="A" AssemblyName="X" AssemblyVersion="1.0.0.0" AssemblyCulture="neutral" AssemblyPublicKeyToken="cb1543ab759ce10e" EnlistedHost="">  
<DownstreamOrchestration Relationship="CALL" Name="B" AssemblyName="X" AssemblyVersion="1.0.0.0" AssemblyCulture="neutral" AssemblyPublicKeyToken="cb1543ab759ce10e" EnlistedApp="App2"/>  
</RootOrchestration>  
```  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.