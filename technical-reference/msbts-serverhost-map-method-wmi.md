---
description: "Learn more about: MSBTS_ServerHost.Map Method (WMI)"
title: MSBTS_ServerHost.Map Method (WMI)
TOCTitle: MSBTS_ServerHost.Map Method (WMI)
ms:assetid: a97cd07c-77bc-41f0-ab23-4328525f5e25
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577957(v=BTS.80)
ms:contentKeyID: 51530377
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServerHost.Map Method (WMI)

 

Maps the server to the MessageBox without installing applications.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 Map();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

You must establish this mapping before an instance of this BizTalk host can be installed on this BizTalk server. You install the instance of the host by calling the **Install** method on the corresponding **MSBTS\_HostInstance** instance.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

