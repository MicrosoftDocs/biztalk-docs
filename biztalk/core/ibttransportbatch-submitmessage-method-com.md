---
title: "IBTTransportBatch.SubmitMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f821d270-bc2e-4237-976c-6862286d3be9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.SubmitMessage Method (COM)
Adds a message to the batch to be processed by the BizTalk Server Messaging Engine.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportBatch::SubmitMessage(  
IBaseMessage*  
pIndoc  
);  
  
```  
  
```vb  
  
Sub SubmitMessage(  
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
|BTS_E_URL_DISALLOWED|The URL specified on the message context was not valid at the time the API was called.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
 **Remarks**  
  
 The context properties ***InboundTransportLocation*** and ***InboundTransportType*** should be present in the message context; this is used to look up the receive port configuration for this URL.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)