---
title: MSBTS_GroupSetting.SignCertThumbprint Property (WMI)
TOCTitle: MSBTS_GroupSetting.SignCertThumbprint Property (WMI)
ms:assetid: 6e545297-da6d-4e57-9d26-4ebce88b9a72
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560718(v=BTS.80)
ms:contentKeyID: 51528784
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.SignCertThumbprint Property (WMI)

 

Gets or sets the thumbprint of the signing certificate to be used to sign outbound documents sent by any BizTalk Host instance in the BizTalk group.

The syntax shown is language neutral.

## Syntax

```C#
  
string SignCertThumbprint = "";   
```

## Remarks

This property is read-write.

The certificate thumbprint is a digest of the certificate data and is found in the certificate details and is expressed as a hexadecimal value. Example: 'FD36 90F0 EB49 F7B8 D3AB 1C69 8E02 ED84 5738 7868'.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

