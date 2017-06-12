---
title: "IBTTransmitterBatch.Clear Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 241f001a-46eb-4668-b652-ac2eed962501
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitterBatch.Clear Method (COM)
Clears the batch if one or more calls to the [TransmitMessage](../core/ibttransmitterbatch-transmitmessage-method-com.md) method failed.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransmitterBatch::Clear(  
);  
  
```  
  
```vb  
  
Sub Clear()  
  
```  
  
## Remarks  
 **Parameters**  
  
 None.  
  
 None.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
 **Remarks**  
  
 If one or more calls to the [TransmitMessage](../core/ibttransmitterbatch-transmitmessage-method-com.md) method fail, the BizTalk Server Messaging Engine will clear the batch and then deal with the messages in the batch in the following manner:  
  
-   If the message has retries remaining, it will be resubmitted and the BizTalk Server Messaging Engine will use the retry interval stamped on the message.  
  
-   If the retries have been exhausted for this message, the BizTalk Server Messaging Engine will attempt to move the message to the backup transport.  
  
-   If the BizTalk Server Messaging Engine cannot move the message to the backup transport, the BizTalk Server Messaging Engine will suspend the message.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransmitterBatch Interface (COM)](../core/ibttransmitterbatch-interface-com.md)   
 [IBTTransmitterBatch Members (COM)](../core/ibttransmitterbatch-members-com.md)