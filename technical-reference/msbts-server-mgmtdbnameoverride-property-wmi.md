---
title: MSBTS_Server.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_Server.MgmtDbNameOverride Property (WMI)
ms:assetid: b653938a-238e-4d30-9137-4382dde71387
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578253(v=BTS.80)
ms:contentKeyID: 51530740
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connection string. This property was not implemented for BizTalk Server and is reserved for future use.


> [!NOTE]
> <P>The BizTalk Management database is also referred to as the BizTalk Configuration database.</P>



## Property Declaration

*The syntax shown is language neutral.*

``` 
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

