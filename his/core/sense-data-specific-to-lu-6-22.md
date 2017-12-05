---
title: "Sense Data Specific to LU 6.22 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04e44703-1177-44a2-bd48-4184ae14a8e2
caps.latest.revision: 4
---
# Sense Data Specific to LU 6.2
The LU 6.2 sense codes are specified and interpreted by SNA components within [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], and, in general, are presented as return codes and as parameters to specific verbs.  
  
 The following sense codes are carried on responses flowing on LU 6.2 sessions.  
  
|Code|Meaning|  
|----------|-------------|  
|0814|Bracket bid reject  RTR forthcoming|  
|0819|RTR not required  receiver of RTR request has nothing to send|  
|0835|Invalid parameter  request contained a fixed or variable field that is invalid. Bytes 2 and 3 contain a 2-byte binary count which indexes the field error (zero origin)|  
|0846|ERP message forthcoming: The received request was rejected for a reason to be specified in a forthcoming FMH-7 request  which itself carries SNA sense data (see the following table for a list of these codes)|  
|088B|BB not accepted  BIS reply requested|  
|2010|BIS protocol error receiver detected a BIS error, for example, two BIS replies received|  
  
 The following data is carried on an FMH-7 request, coming after the flow of a negative response X'0846'.  
  
|Code|Meaning|  
|----------|-------------|  
|1008 600B|Resource failure no retry|  
|1008 6021|Allocation error TPN not recognized|  
|1008 6031|Allocation error PIP not allowed|  
|1008 6032|Allocation error PIP not specified correctly|  
|1008 6034|Allocation error conversation type mismatch|  
|1008 6041|Allocation error sync level not supported by pgm|  
|080F 6051|Allocation error security not valid|  
|084B 6031|Allocation error trans pgm not available retry|  
|084C 0000|Allocation error trans pgm not available no retry|  
|0864 0000|Deallocate abend prog|  
|0864 0001|Deallocate abend svc|  
|0846 0002|Deallocate abend timer|  
|0889 0000|Prog error no trunc or prog error purging|  
|0889 0001|Prog error trunc|  
|0889 0100|Svc error no trunc or svc error purging|  
|0889 1001|Svc error trunc|  
  
## See Also  
 [SNA Sense Codes](../core/sna-sense-codes2.md)