---
title: "IBTTransportBatch.CancelResponseMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97afd5ed-694a-4b96-804c-2f57ef81e355
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.CancelResponseMessage Method (COM)
Adds a cancellation request to the batch to cancel a request for a response message.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportBatch::CancelResponseMessage(  
BSTR  
bstrCorrelationToken  
);  
  
```  
  
```vb  
  
Sub CancelResponseMessage(  
bstrCorrelationToken  
 As String  
)  
  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrCorrelationToken*  
 [in] String that contains the correlation token of the message that a response was requested for.  
  
 *bstrCorrelationToken*  
 **String** that contains the correlation token of the message that a response was requested for.  
  
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