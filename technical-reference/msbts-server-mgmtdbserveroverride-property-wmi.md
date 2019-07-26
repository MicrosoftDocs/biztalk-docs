---
title: MSBTS_Server.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_Server.MgmtDbServerOverride Property (WMI)
ms:assetid: 99f86602-cc5d-4410-93ac-1177dd4205a3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577505(v=BTS.80)
ms:contentKeyID: 51529884
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connection string. This property was not implemented for BizTalk Server and is reserved for future use.


> [!NOTE]
> <P>The BizTalk Management database is also referred to as the BizTalk Configuration database.</P>



## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **Name**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

