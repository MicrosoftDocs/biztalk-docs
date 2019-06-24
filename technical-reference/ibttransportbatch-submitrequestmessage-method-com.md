---
title: IBTTransportBatch.SubmitRequestMessage Method (COM)
TOCTitle: IBTTransportBatch.SubmitRequestMessage Method (COM)
ms:assetid: 772f55ee-b0a4-49e4-83b4-dc1c5e35f4e8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560878(v=BTS.80)
ms:contentKeyID: 51529029
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.SubmitRequestMessage Method (COM)

 

Submits a request message for a request-response pair.

## Syntax

``` c++
  
            HRESULT IBTTransmitter::SubmitRequestMessage(  
      IBaseMessage* pRequest   String* bstrCorrelationToken   bool fFirstResponseOnly   DateTime dtExpirationTime  
      IBTTransmitter* pResponseCallback   
);  
```

``` vb
  
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
The [IBTTransmitter](ibttransmitter-interface-com.md)callback interface on which the response message will be delivered.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

