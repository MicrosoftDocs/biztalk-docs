---
title: "IBTTransportBatch.SubmitRequestMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 772f55ee-b0a4-49e4-83b4-dc1c5e35f4e8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.SubmitRequestMessage Method (COM)
Submits a request message for a request-response pair.  
  
## Syntax  
  
```cpp  
  
            HRESULT IBTTransmitter::SubmitRequestMessage(  
      IBaseMessage* pRequest   String* bstrCorrelationToken   bool fFirstResponseOnly   DateTime dtExpirationTime  
      IBTTransmitter* pResponseCallback   
);  
```  
  
```vb  
  
Sub SubmitRequestMessage(  
   ByVal   
pRequest  
 As IBaseMessage _   ByVal bstrCorrelationToken As String _   ByVal fFirstResponseOnly As Boolean _   ByVal dtExpirationTime As DateTime _   ByVal pResponseCallback As IBTTransmitter _)  
```  
  
## Remarks  
 **Parameters**  
  
 *pRequest*  
 The request message to be submitted.  
  
 *bstrCorrelationToken*  
 The unique identifier used to correlate the response message back to the request message.  
  
 *fFirstResponseOnly*  
 **true** if only the first response should be delivered, otherwise, **false**.  
  
 *dtExpirationTime*  
 The timeout after which no response messages will be returned.  
  
 *pResponseCallback*  
 The [IBTTransmitter](../core/ibttransmitter-interface-com.md)callback interface on which the response message will be delivered.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)