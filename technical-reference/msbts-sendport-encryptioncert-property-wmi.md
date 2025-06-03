---
description: "Learn more about: MSBTS_SendPort.EncryptionCert Property (WMI)"
title: MSBTS_SendPort.EncryptionCert Property (WMI)
TOCTitle: MSBTS_SendPort.EncryptionCert Property (WMI)
ms:assetid: 5917c349-4c6a-43c2-9e6e-9d206bdbc17b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560289(v=BTS.80)
ms:contentKeyID: 51528226
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_SendPort.EncryptionCert Property (WMI)

 

This property contains the Name of the certificate used for outbound encryption.

*The syntax shown is language neutral.*

## Syntax

```C#
string EncryptionCert;  
```

## Remarks

This property is read-write.

The default value for this parameter is "".

The syntax shown is language neutral.The maximum length for this property is 256 characters.

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



This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.EncryptionCert** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

