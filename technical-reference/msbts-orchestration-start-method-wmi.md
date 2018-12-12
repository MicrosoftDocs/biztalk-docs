---
title: MSBTS_Orchestration.Start Method (WMI)
TOCTitle: MSBTS_Orchestration.Start Method (WMI)
ms:assetid: f490f947-1047-40fa-9470-422f4ef2f8b2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561937(v=BTS.80)
ms:contentKeyID: 51533441
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration.Start Method (WMI)

 

Starts the orchestration by enabling its activation subscription.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 Start(  
    uint32 AutoEnableReceiveLocationFlag,   
    uint32 AutoResumeOrchestrationInstanceFlag,  
    uint32 AutoStartSendPortsFlag  
);  
```

#### Parameters

*AutoEnableReceiveLocationFlag*  
\[in\] Specifies whether receive locations associated with this orchestration should be automatically enabled. Permissible values for this parameter are (1) "No auto enable of receive locations related to this orchestration", or (2) "Enable all receive locations related to this orchestration". Note that the integer values must be used in code and script. The default value is 1.

*AutoResumeOrchestrationInstanceFlag*  
\[in\] Specifies whether service instances of this orchestration type that were manually suspended previously should be automatically resumed. Permissible values for this parameter are (1) "No auto resume of service instances of this orchestration", or (2) "Automatically resume all suspended service instances of this orchestration" Note that the integer values must be used in code and script. The default value is 2.

*AutoStartSendPortsFlag*  
\[in\] Specifies whether send ports and send port groups imported by this orchestration should be automatically started. Permissible values for this parameter are (1) "No auto start of send ports and send port groups of this orchestration", or (2) "Start all send ports and send port groups associated with this orchestration." Note that the integer values must be used in code and script. If the value is 1 and there exists a send port or send port group that is in the Bound state, WMI will fail this orchestration start operation. The default value is 2.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

