---
title: "IBTTransportBatch.Done Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b84d540f-c82d-4bef-b1a0-88ffce0475c0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.Done Method (COM)
Posts the batch of work to the thread pool for the BizTalk Server Messaging Engine where it will be processed asynchronously.  
  
## Syntax  
  
```cpp  
  
            HRESULT IBTTransportBatch::Done(  
            IUnknown*  
            pTransaction,   
);  
```  
  
```vb  
  
            Sub Done(  
            pTransaction  
             As IUnknown,   
)  
```  
  
## Remarks  
 **Parameters**  
  
 *pTransaction*  
 [in] Pointer to the DTC transaction.  
  
 *pTransaction*  
 **IUnknown** that contains the DTC transaction.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)