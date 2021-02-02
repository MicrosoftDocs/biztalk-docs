---
description: "Learn more about: MSBTS_Host.DecryptCertThumbprint Property (WMI)"
title: MSBTS_Host.DecryptCertThumbprint Property (WMI)
TOCTitle: MSBTS_Host.DecryptCertThumbprint Property (WMI)
ms:assetid: 1660cc95-d73e-49f5-a3b1-de781efb02eb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558750(v=BTS.80)
ms:contentKeyID: 51526414
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.DecryptCertThumbprint Property (WMI)

 

Contains the thumbprint of the public key certificate used to decrypt inbound messages for this host.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string DecryptCertThumbprint;  
```

## Remarks

This property is read-write.

The certificate thumbprint is a digest of the certificate data and is found in the certificate details expressed as a hexadecimal value. For example: 'FD36 90F0 EB49 F7B8 D3AB 1C69 8E02 ED84 5738 7868'.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

