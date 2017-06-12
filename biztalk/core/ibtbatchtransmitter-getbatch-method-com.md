---
title: "IBTBatchTransmitter.GetBatch Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36be99fb-e7b0-442a-b487-e8e64dbb79d1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTBatchTransmitter.GetBatch Method (COM)
Returns a new batch that will be used by the BizTalk Server Messaging Engine, which will push messages to be transmitted into the batch.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTBatchTransmitter::GetBatch(  
IBTTransmitterBatch**  
ppBatch  
);  
  
```  
  
```vb  
  
Function GetBatch() As IBTTransmitterBatch  
  
```  
  
## Remarks  
 **Parameters**  
  
 *ppBatch*  
 [out,retval] Pointer to hold the reference to the returned **IBTTransmitterBatch** object/interface, which will contain the new adapter batch.  
  
 None.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the [IBTTransmitterBatch](../core/ibttransmitterbatch-interface-com.md) containing the new adapter batch.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTBatchTransmitter Interface (COM)](../core/ibtbatchtransmitter-interface-com.md)   
 [IBTBatchTransmitter Members (COM)](../core/ibtbatchtransmitter-members-com.md)