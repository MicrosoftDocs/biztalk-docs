---
title: "IBTTransmitterBatch.TransmitMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22dd77c3-f3f5-4f01-b945-54110f5d2596
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitterBatch.TransmitMessage Method (COM)
Adds messages to the adapter batch that are ready to be transmitted.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransmitterBatch::TransmitMessage(  
        IBaseMessage*  
        pMessage,  
BOOL*bDeleteMsgOnDone);  
```  
  
```vb  
  
Function TransmitMessage(  
pMessage  
 As IBaseMessage  
) As Boolean  
  
```  
  
## Remarks  
 **Parameters**  
  
 *pMessage*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message.  
  
 *pMessage*  
 **IBaseMessage** object/interface that contains the message to be transmitted.  
  
 *bDeleteMsgOnDone*  
 [out,retval] Pointer to a Boolean used to return the status of the deleted message. **true** if the message was transmitted; otherwise, **false**.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 **true** if the message was transmitted; otherwise, **false**.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|FAILED HRESULT|If the **TransmitMessage** method fails, the Messaging Engine will continue to push messages onto the batch until either the batch is full or there are no more messages destined for the batch. The Messaging Engine will then call the **Clear** method on the batch and then handle the messages in the following manner:<br /><br /> -   If the message has retries remaining, it will be resubmitted, the Messaging Engine will use the retry interval stamped on the message.<br />-   If the retries have been exhausted for this message, the Messaging Engine will attempt to move the message to the backup transport.<br />-   If the Messaging Engine cannot move the message to its backup transport, the Messaging Engine will suspend the message.|  
  
 **Remarks**  
  
 This method is called by the BizTalk Server Messaging Engine.  
  
 If the return value is **true**, the adapter sends the message on the batch synchronously. If the return value is **false**, the adapter sends the message on the batch asynchronously. If **false** is returned, then adapter is responsible for updating the message information in the database after sending the message. The adapter can resubmit the message, delete the message, suspend the message, or move it to the backup transport.  
  
 The adapter does not actually transmit the message when this message is called, the transmission begins when the **Done** method is called.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransmitterBatch Interface (COM)](../core/ibttransmitterbatch-interface-com.md)   
 [IBTTransmitterBatch Members (COM)](../core/ibttransmitterbatch-members-com.md)