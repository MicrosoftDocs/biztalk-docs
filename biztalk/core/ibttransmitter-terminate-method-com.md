---
title: "IBTTransmitter.Terminate Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77b8eee7-3fd8-4083-a73f-c155f0df9255
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitter.Terminate Method (COM)
Finishes processing any messages the adapter is currently processing and prepares for termination.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransmitter::Terminate(  
);  
  
```  
  
```vb  
  
Sub Terminate()  
  
```  
  
#### Parameters  
 None.  
  
 None.  
  
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
  
 The adapter should not start any new work after this call, but may complete outstanding work items as necessary.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransmitter Interface (COM)](../core/ibttransmitter-interface-com.md)   
 [IBTTransmitter Members (COM)](../core/ibttransmitter-members-com.md)