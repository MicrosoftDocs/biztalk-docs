---
title: "IBTTransmitter.Initialize Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd9ebee4-1e45-4cf2-a14d-f2e8d7e708c2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitter.Initialize Method (COM)
Initializes the adapter.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransmitter::Initialize(  
IBTTransportProxy*  
pTransProxy  
);  
  
```  
  
```vb  
  
Sub Initialize(  
pTransProxy  
 As IBTTransportProxy  
)  
  
```  
  
#### Parameters  
 *pTransProxy*  
 [in] Reference to a **IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.  
  
 *pTransProxy*  
 **IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
## Remarks  
 This method is called by the BizTalk Server Messaging Engine.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransmitter Interface (COM)](../core/ibttransmitter-interface-com.md)   
 [IBTTransmitter Members (COM)](../core/ibttransmitter-members-com.md)