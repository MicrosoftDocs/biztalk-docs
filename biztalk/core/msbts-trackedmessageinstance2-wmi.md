---
title: "MSBTS_TrackedMessageInstance2 (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63780b56-6364-4483-92c3-144835c8a2eb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance2 (WMI)
This class reflects tracked message instances stored in the MessageBox database or Archived database.  This class only supports GetObject and does not support Create/Update/Delete/Enum operations.  
  
## Declaration  
 class MSBTS_TrackedMessageInstance2 : MSBTS_BTSObject  
  
## Members  
  
|Property name|Description|  
|-------------------|-----------------|  
|[MSBTS_TrackedMessageInstance2.MessageInstanceID Property (WMI)](../core/msbts-trackedmessageinstance2-messageinstanceid-property-wmi.md)|This property contains the ID of this message.|  
|[MSBTS_TrackedMessageInstance2.SourceDBServerName Property (WMI)](../core/msbts-trackedmessageinstance2-sourcedbservername-property-wmi.md)|Name of the SQL server where the tracked message is stored.|  
|[MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI)](../core/msbts-trackedmessageinstance2-sourcedbname-property-wmi.md)|Name of the SQL database where the tracked message is stored.|  
|[MSBTS_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI)](../core/msbts-trackedmessageinstance2-mgmtdbnameoverride-property-wmi.md)|This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name.|  
|[MSBTS_TrackedMessageInstance2.MgmtDbServerOverride Property (WMI)](../core/msbts-trackedmessageinstance2-mgmtdbserveroverride-property-wmi.md)|This optional property can be used to override the data source part of the BizTalk Messaging Management database connect string.|  
|[MSBTS_TrackedMessageInstance2.PartCount Property (WMI)](../core/msbts-trackedmessageinstance2-partcount-property-wmi.md)|Number of message parts|  
  
|Method name|Description|  
|-----------------|-----------------|  
|[MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI)](../core/msbts-trackedmessageinstance2-savetofile-method-wmi.md)|This method saves message context and parts into multiple output files.|  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.