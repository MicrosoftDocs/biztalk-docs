---
title: MSBTS_SendHandler2.HostNameToSwitchTo Property (WMI)
TOCTitle: MSBTS_SendHandler2.HostNameToSwitchTo Property (WMI)
ms:assetid: d4f9a5ad-ab84-4ad7-835c-c58365947473
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578611(v=BTS.80)
ms:contentKeyID: 51531620
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendHandler2.HostNameToSwitchTo Property (WMI)

 

This property contains the name of the BizTalk Host that this transport handler should switch to. To switch this transport handler to a different host, you must update this property with the name of the new host.

## Syntax

```C#
  
stringHostNameToSwitchTo;  
```

## Remarks

The syntax shown is language neutral.

This property may be written to switch the transport handler to a different host.

The maximum length for this property is 80 characters.

The default value for this property is "".

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

