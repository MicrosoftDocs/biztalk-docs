---
title: IBTTransportBatch.SubmitResponseMessage Method (COM)
TOCTitle: IBTTransportBatch.SubmitResponseMessage Method (COM)
ms:assetid: 1a15ef76-9015-4d9a-8089-773e7a2191cf
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559026(v=BTS.80)
ms:contentKeyID: 51526549
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.SubmitResponseMessage Method (COM)

 

Submits the response message for a solicit-response pair.

## Syntax

``` c++
  
      HRESULT IBTTransmitter::SubmitResponseMessage(  
IBaseMessage* pSolicitDocSent  
IBaseMessage* pResponseDocToSubmit);  
```

``` vb
  
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

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

