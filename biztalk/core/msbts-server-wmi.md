---
title: "MSBTS_Server (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 849d3788-2edd-4fad-a230-afbe320353c1
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Server (WMI)
Represents computers within a group that have Microsoft® BizTalk® Servers installed.  
  
## Syntax  
  
```  
  
class MSBTS_Server : MSBTS_Service  
```  
  
## Members  
 **MSBTS_Server** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[MgmtDbNameOverride](../core/msbts-server-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connection string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use. **Note:**  The BizTalk Management database is also referred to as the BizTalk Configuration database.|  
|[MgmtDbServerOverride](../core/msbts-server-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connection string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-server-name-property-wmi.md)|Contains the name of the server.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
  
 **MSBTS_Server** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI)](../core/msbts-server-checkifcaninstallhostinstances-method-wmi.md)|Checks if the server can host BizTalk host instances.|  
|[Start](../core/msbts-server-start-method-wmi.md)|Starts all BizTalk Server services on a specific server.|  
|[Stop](../core/msbts-server-stop-method-wmi.md)|Stops all BizTalk Server services on a specific server.|  
  
## Remarks  
 This class provides several server-wide operations. **MSBTS_Server** is created with an **MSBTS_ServerSetting** class instance.  
  
 For more information about the minimum security user rights required to administer a server, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.  
  
## See Also  
 [MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI)](../core/msbts-server-checkifcaninstallhostinstances-method-wmi.md)   
 [MSBTS_Server.MgmtDbNameOverride Property (WMI)](../core/msbts-server-mgmtdbnameoverride-property-wmi.md)   
 [MSBTS_Server.MgmtDbServerOverride Property (WMI)](../core/msbts-server-mgmtdbserveroverride-property-wmi.md)   
 [MSBTS_Server.Name Property (WMI)](../core/msbts-server-name-property-wmi.md)   
 [MSBTS_Server.Start Method (WMI)](../core/msbts-server-start-method-wmi.md)   
 [MSBTS_Server.Stop Method (WMI)](../core/msbts-server-stop-method-wmi.md)