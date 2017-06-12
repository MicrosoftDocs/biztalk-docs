---
title: "IBTTransportBatch.SubmitResponseMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a15ef76-9015-4d9a-8089-773e7a2191cf
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.SubmitResponseMessage Method (COM)
Submits the response message for a solicit-response pair.  
  
## Syntax  
  
```cpp  
  
      HRESULT IBTTransmitter::SubmitResponseMessage(  
IBaseMessage* pSolicitDocSent  
IBaseMessage* pResponseDocToSubmit);  
```  
  
```vb  
  
Sub SubmitResponseMessage(  
   ByVal   
pSolicitDocSent  
 As IBaseMessage _   ByVal pResponseDocToSubmit As IBaseMessage _)  
```  
  
## Remarks  
 **Parameters**  
  
 *pSolicitDocSent*  
 The document to send.  
  
 *pResponseDocToSubmit*  
 The response document to submit.  
  
 **Remarks**  
  
 This method ensures that the correct properties on the response message are sent, which ensures that the response message is correctly correlated back to the solicit requested message sent.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)