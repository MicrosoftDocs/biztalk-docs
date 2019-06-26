---
title: MSBTS_Host.Start Method (WMI)
TOCTitle: MSBTS_Host.Start Method (WMI)
ms:assetid: b4f439b6-de26-4adb-9497-3b4140c6acf2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578217(v=BTS.80)
ms:contentKeyID: 51530696
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.Start Method (WMI)

 

Starts all BizTalk Host instances in the BizTalk group for the given BizTalk Host.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 StartService();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For more information about the minimum security user rights required to administer a Host, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

