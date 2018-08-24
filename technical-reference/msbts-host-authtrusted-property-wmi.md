---
title: MSBTS_Host.AuthTrusted Property (WMI)
TOCTitle: MSBTS_Host.AuthTrusted Property (WMI)
ms:assetid: a5cdb4fc-aa4d-4b27-845d-d93b4dc590c6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577897(v=BTS.80)
ms:contentKeyID: 51530294
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.AuthTrusted Property (WMI)

 

Indicates whether a tracking service can be trusted to collect authentication information. The syntax shown is language neutral.

## Syntax

``` 
  
boolean AuthTrusted;  
```

## Remarks

This property is read-write.

Each host can be marked as authentication trusted. These hosts are permitted to indicate that a sender of a message, which the trusted host is queuing, is an entity other than the host itself. In other words, the service accounts of an authentication trusted host are trusted to place a sender's security ID (SSID) on a message that maps to a user other than to the host specifically. For more information, see [Authenticating the Sender of a Message](https://msdn.microsoft.com/en-us/library/aa561080\(v=bts.80\)).


> [!NOTE]
> <P>You can mark any host instance as authentication trusted. However, authentication trusted host instances cannot use the same service account(s) as non-authentication trusted host instances.</P>



## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

