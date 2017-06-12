---
title: "MSBTS_TrackedMessageInstance (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03d251f7-4f09-4f7b-bd8a-388b6669258a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance (WMI)
Represents tracked message instances stored in the MessageBox or Archived databases.  
  
## Syntax  
  
```  
class MSBTS_TrackedMessageInstance : MSBTS_BTSObject  
```  
  
## Members  
 **MSBTS_TrackedMessageInstance** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[MessageInstanceID](../core/msbts-trackedmessageinstance-messageinstanceid-property-wmi.md)|Contains the ID of the message instance.|  
|Name (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[PartCount](../core/msbts-trackedmessageinstance-partcount-property-wmi.md)|Contains the number of message parts.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[SourceDBName](../core/msbts-trackedmessageinstance-sourcedbname-property-wmi.md)|Contains the name of the SQL database where the tracked message is stored, either the MessageBox or Archived database.|  
|[SourceDBServerName](../core/msbts-trackedmessageinstance-sourcedbservername-property-wmi.md)|Contains the name of the SQL Server where the tracked message is stored, either the MessageBox or Archived database.|  
  
 **MSBTS_TrackedMessageInstance** defines the following method:  
  
|Property|Description|  
|--------------|-----------------|  
|[SaveToFile](../core/msbts-trackedmessageinstance-savetofile-method-wmi.md)|Saves the message context and parts into multiple output files.|  
  
## Remarks  
 This class only supports **GetObject**, and does not support **Create**, **Update**, **Delete**, or **Enum** operations.  
  
 For sample code illustrating the **MSBTS_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](../core/saving-a-message-to-a-file-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.