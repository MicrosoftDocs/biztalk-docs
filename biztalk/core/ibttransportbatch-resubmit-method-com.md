---
title: "IBTTransportBatch.Resubmit Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c026cd0-08f9-4c70-a73f-8ebe5b116559
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.Resubmit Method (COM)
Adds a message to the batch to be resubmitted.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransportBatch::Resubmit(  
        IBaseMessage*  
        pIndoc,  
DATEdtTimeStamp);  
```  
  
```vb  
  
        Sub Resubmit(  
        pIndoc  
         As IBaseMessage,  
dtTimeStamp As Date)  
```  
  
## Remarks  
 **Parameters**  
  
 *pIndoc*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message to be added to the batch.  
  
 *pIndoc*  
 **IBaseMessage** object/interface that contains the message to be added to the batch.  
  
 *dtTimeStamp*  
 [in] Date type that contains the time the message should be redelivered to this adapter.  
  
 *dtTimeStamp*  
 **Date** that contains the message should be redelivered to this adapter.  
  
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
  
 This method should only be called on send-side.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)