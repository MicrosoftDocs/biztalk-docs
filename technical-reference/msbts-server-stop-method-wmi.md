---
title: MSBTS_Server.Stop Method (WMI)
TOCTitle: MSBTS_Server.Stop Method (WMI)
ms:assetid: 2b3a74f9-593d-4059-b04e-bd93fefee4a2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559357(v=BTS.80)
ms:contentKeyID: 51526961
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server.Stop Method (WMI)

 

Stops all BizTalk Server services on a specific server.

## Method Declaration

*The syntax shown is language neutral.*

``` 
uint32 Stop();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

The execution of this method is valid anytime the specified server is in a running state.

For more information about the minimum security user rights required to administer a server, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

