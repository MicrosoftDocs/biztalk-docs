---
title: "IBTTransmitter.TransmitMessage Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58912bda-c466-4cb1-bfc9-20689be108af
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitter.TransmitMessage Method (COM)
Transmits a message for a adapter.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransmitter::TransmitMessage(  
        IBaseMessage*  
        pMessage,  
BOOL*bDeleteMessage);  
```  
  
```vb  
  
Function TransmitMessage(  
pMessage  
 As IBaseMessage  
) As Boolean  
  
```  
  
#### Parameters  
 *pMessage*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message.  
  
 *bDeleteMessage*  
 [out,retval] Pointer to a Boolean used to return the delete message. **true** if the message was transmitted; otherwise, **false**.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 **true** if the message was transmitted; otherwise, **false**.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|FAILED HRESULT|Indicates that the message could not be transmitted successfully. In this scenario the Messaging Engine will handle the message in the following manner:<br /><br /> -   If the message has retries remaining, it will be resubmitted, the Messaging Engine will use the retry interval stamped on the message.<br />-   If the retries have been exhausted for this message, the Messaging Engine will attempt to move the message to the backup transport.<br />-   If the Messaging Engine cannot move the message to its backup transport, the Messaging Engine will suspend the engine.|  
  
## Remarks  
 This method is called by the BizTalk Server Messaging Engine.  
  
 If the return value is **true**, then the adapter transmitted the message synchronously. If the return value is **false**, then the adapter will transmit the message asynchronously and call back the BizTalk Server Messaging Engine to notify it of the transmission outcome.  
  
 If the adapter fails to transmit the message successfully and you do not want the adapter to handle the retry semantics, it should throw an exception. In this scenario, the BizTalk Server Messaging Engine will handle the retry semantics. Typically, this means that the message will be redelivered to the adapter until it either successfully transmits the message or the retry attempts are exhausted. If the retry attempts are exhausted, the message will be moved to the backup transport for transmission.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransmitter Interface (COM)](../core/ibttransmitter-interface-com.md)   
 [IBTTransmitter Members (COM)](../core/ibttransmitter-members-com.md)