---
title: "GetServiceContractCallPoint | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be03d100-0cba-4b80-8056-b582a2cd74ce
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetServiceContractCallPoint
Pushes the name of the current service contract call point onto the stack.  
  
## Syntax  
  
```  
  
<wcf:Operation Name="GetServiceContractCallPoint" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current contract call point.  
  
## Remarks  
 A Windows Communication Framework service can be intercepted at different points in the lifetime of the service contract. These locations are defined by the `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` enumeration:  
  
|Contract call point|Description|  
|-------------------------|-----------------|  
|ClientReply|Client reply call point.|  
|ClientRequest|Client request call point.|  
|ClientFault|Client fault point.|  
|ServiceReply|Service reply call point.|  
|ServiceRequest|Service request call point.|  
|ServiceFault|Service fault point.|  
|CallbackRequest|Callback request call point.|  
|CallbackReply|Callback reply call point.|  
|CallbackFault|Callback fault point.|  
  
## Example  
 The following sample contains an event filter expression configured to find a specific operation ("Receive") in the client reply state. This is done by using a combination of operations including `GetOperationName`, `GetServiceContractCallPoint`, and logical operations.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ClientReply</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## See Also  
 [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)