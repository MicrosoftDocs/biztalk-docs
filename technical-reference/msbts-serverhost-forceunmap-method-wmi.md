---
title: MSBTS_ServerHost.ForceUnmap Method (WMI)
TOCTitle: MSBTS_ServerHost.ForceUnmap Method (WMI)
ms:assetid: 32ebde10-54e1-462d-bbff-321ed4b827f6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559511(v=BTS.80)
ms:contentKeyID: 51527189
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.ForceUnmap Method (WMI)

 

Unmaps the server from the MessageBox even whether or not all applications cannot be uninstalled.

## Method Declaration

*The syntax shown is language neutral.*

``` 
uint32 ForceUnmap();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

