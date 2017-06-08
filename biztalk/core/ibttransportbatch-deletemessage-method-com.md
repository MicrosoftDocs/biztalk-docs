---
title: "IBTTransportBatch.DeleteMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c556ef11-2db1-4d2e-ae84-e0300ab6ec86
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.DeleteMessage Method (COM)
Adds a message to the batch to be deleted.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportBatch::DeleteMessage(  
IBaseMessage*  
pIndoc  
);  
  
```  
  
```vb  
  
Sub DeleteMessage(  
pIndoc  
 As IBaseMessage  
)  
  
```  
  
## Remarks  
 **Parameters**  
  
 *pIndoc*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message to be added to the batch.  
  
 *pIndoc*  
 **IBaseMessage** object/interface that contains the message to be added to the batch.  
  
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
  
 **Remarks**  
  
 Adapters should call this method if they are sending messages asynchronously; once the message has been successfully transmitted the message needs to be deleted. If the message is sent synchronously, the message engine automatically deletes the message.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)