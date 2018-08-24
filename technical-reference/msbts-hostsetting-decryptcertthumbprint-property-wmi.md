---
title: MSBTS_HostSetting.DecryptCertThumbprint Property (WMI)
TOCTitle: MSBTS_HostSetting.DecryptCertThumbprint Property (WMI)
ms:assetid: c9f22e37-8d2b-4182-9e56-2017baf3e75f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547984(v=BTS.80)
ms:contentKeyID: 51531286
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.DecryptCertThumbprint Property (WMI)

 

Contains the thumbprint of the decryption certificate.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

``` 
  
string DecryptCertThumbprint;  
```

## Remarks

This property is read-write.

The certificate thumbprint is a digest of the certificate data and is found in the certificate details expressed as a hexadecimal value. For example: 'FD36 90F0 EB49 F7B8 D3AB 1C69 8E02 ED84 5738 7868'.

The maximum length for this property is 80 characters.

For sample code using the **MSBTS\_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](creating-updating-and-deleting-a-host-instance-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

