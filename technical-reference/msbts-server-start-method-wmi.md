---
title: MSBTS_Server.Start Method (WMI)
TOCTitle: MSBTS_Server.Start Method (WMI)
ms:assetid: 3618084a-ccb4-4534-bcbf-e135c385bcdf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559573(v=BTS.80)
ms:contentKeyID: 51527269
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server.Start Method (WMI)

 

Starts all BizTalk Server services on a specific server.

## Method Declaration

*The syntax shown is language neutral.*

``` 
uint32 Start();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

The execution of this method is valid anytime the server is in a stopped state.

For more information about the minimum security user rights required to administer a server, see [Minimum Security User Rights](https://msdn.microsoft.com/en-us/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

