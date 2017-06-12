---
title: "IBTTransmitterBatch.BeginBatch Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84cdad96-142d-40ea-b640-b310dd31dab8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitterBatch.BeginBatch Method (COM)
Initializes the batch.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransmitterBatch::BeginBatch(  
        LONG*  
        pnMaxBatchSize,  
IUnknown**ppTransaction);  
```  
  
```vb  
  
Function BeginBatch(  
pnMaxBatchSize  
 As Long  
) As IUnknown  
  
```  
  
## Remarks  
 **Parameters**  
  
 *pnMaxBatchSize*  
 [out] Pointer to an integer used to return the maximum number of messages the adapter will allow in this batch.  
  
 *pnMaxBatchSize*  
 **Long** used to return the maximum number of messages the adapter will allow in this batch.  
  
 *ppTransaction*  
 [out,retval] Address of a pointer to receive an **IUnknown** interface, which will contain the transaction that the Messaging Engine will use in agent interactions. This parameter may be **NULL**.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns a **IUnknown** that contains the transaction that the Messaging Engine will use in agent interactions. This parameter may be **NULL**.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
 **Remarks**  
  
 The BizTalk Server Messaging Engine calls this method prior to pushing messages into the batch.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransmitterBatch Interface (COM)](../core/ibttransmitterbatch-interface-com.md)