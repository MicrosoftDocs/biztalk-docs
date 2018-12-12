---
title: MSBTS_ServerHost.Unmap Method (WMI)
TOCTitle: MSBTS_ServerHost.Unmap Method (WMI)
ms:assetid: c0566f22-ce16-4205-a491-b7f9efe247ae
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578437(v=BTS.80)
ms:contentKeyID: 51530926
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.Unmap Method (WMI)

 

Unmaps the server from the MessageBox.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 Unmap();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

After you have successfully uninstalled this instance of the BizTalk host from this BizTalk server, this method remove the mapping for the BizTalk server from the BizTalk host.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

