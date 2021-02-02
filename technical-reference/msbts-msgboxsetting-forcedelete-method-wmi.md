---
description: "Learn more about: MSBTS_MsgBoxSetting.ForceDelete Method (WMI)"
title: MSBTS_MsgBoxSetting.ForceDelete Method (WMI)
TOCTitle: MSBTS_MsgBoxSetting.ForceDelete Method (WMI)
ms:assetid: 7399c9ff-ef94-44b7-973d-a183d63109d2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560820(v=BTS.80)
ms:contentKeyID: 51528934
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MsgBoxSetting.ForceDelete Method (WMI)

 

Deletes the MessageBox object.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 ForceDelete();  
```

## Remarks

This operation bypasses all delete constraints and will succeed even if incomplete instances are still running or are suspended in this MessageBox.

For more information about the minimum security user rights required to administer the MessageBox database, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

