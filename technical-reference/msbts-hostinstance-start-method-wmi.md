---
title: MSBTS_HostInstance.Start Method (WMI)
TOCTitle: MSBTS_HostInstance.Start Method (WMI)
ms:assetid: 1324a112-4b24-4449-94b3-dd236e8725c1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547614(v=BTS.80)
ms:contentKeyID: 51526365
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.Start Method (WMI)

 

Starts the given instance of the BizTalk host.

## Method Declaration

*The syntax shown is language neutral.*

```C#
uint32 StartService();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For more information about the minimum security user rights required to administer a Host instance, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).


> [!NOTE]
> <P>Always specify the name of the local server when using WMI. When you enumerate host instances, both local and remote instances will be returned. You can then call the start or stop methods.</P>



For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

