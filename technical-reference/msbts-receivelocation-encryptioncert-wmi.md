---
description: "Learn more about: MSBTS_ReceiveLocation.EncryptionCert (WMI)"
title: MSBTS_ReceiveLocation.EncryptionCert (WMI)
TOCTitle: MSBTS_ReceiveLocation.EncryptionCert (WMI)
ms:assetid: 6484cfd0-20c5-4650-bb42-61f4c797bafc
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560512(v=BTS.80)
ms:contentKeyID: 51528544
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ReceiveLocation.EncryptionCert (WMI)

 

This property contains the Name of the certificate used for outbound encryption.

## Syntax

```C#
  
String EncryptionCert;  
```

## Remarks

This property is read/write.

The default value for this parameter is "".

The syntax shown is language neutral.

The maximum length for this property is 256 characters.

The string must be constructed as shown below with appropriate values filled in and no extra spaces:

```C#
"E=, C=, S=, L=, O=, OU=, CN="  
```

For example, the following string specifies a certificate for a fictitious sample:

```C#
"E=lab, C=US, S=Wa, L=Redmond, O=Microsoft, OU=BizTalk, CN=EncryptSample"  
```


> [!NOTE]
> <P>The certificate must be specified in this order and without extra spaces and must not be longer than 256 characters.</P>



## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

