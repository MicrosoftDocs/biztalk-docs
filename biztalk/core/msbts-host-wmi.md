---
title: "MSBTS_Host (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd0a6c58-236b-4673-8960-c654aef6a894
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host (WMI)
Represents a Microsoft BizTalk Server Host.  
  
## Declaration  
  
```  
class MSBTS_Host : MSBTS_Service  
```  
  
## Members  
 **MSBTS_Host** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[AuthTrusted](../core/msbts-host-authtrusted-property-wmi.md)|Indicates whether a tracking service can be trusted to collect authentication information.|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[DecryptCertComment](../core/msbts-host-decryptcertcomment-property-wmi.md)|Represents a comment field that allows you to associate a friendly name with a decryption certificate.|  
|[DecryptCertThumbprint](../core/msbts-host-decryptcertthumbprint-property-wmi.md)|Contains the thumbprint of the public key certificate used to decrypt inbound messages for this host.|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[HostTracking](../core/msbts-host-hosttracking-property-wmi.md)|Indicates whether instances of this BizTalk Host will host the tracking sub service.|  
|[HostType](../core/msbts-host-hosttype-property-wmi.md)|Indicates which runtime model the instances of the BizTalk Host will be running in.|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[IsDefault](../core/msbts-host-isdefault-property-wmi.md)|Indicates whether the BizTalk Host represented by this WMI instance is the default BizTalk Host in the BizTalk group.|  
|[LastUsedLogon](../core/msbts-host-lastusedlogon-property-wmi.md)|Contains the default logon for the BizTalk Host instance creation user interface.|  
|[MgmtDbNameOverride](../core/msbts-host-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-host-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-host-name-property-wmi.md)|Contains the name of the host.|  
|[NTGroupName](../core/msbts-host-ntgroupname-property-wmi.md)|Contains the name of the Microsoft Windows NT group.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
  
 **MSBTS_Host** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[Start](../core/msbts-host-start-method-wmi.md)|Starts all BizTalk Host instances in the BizTalk group for the given BizTalk Host.|  
|[Stop](../core/msbts-host-stop-method-wmi.md)|Stops all BizTalk Host instances in the BizTalk group for the given BizTalk Host.|  
|[MSBTS_Host.Cluster Method (WMI)](../core/msbts-host-cluster-method-wmi.md)|Clusters all BizTalk Host Instances of the given BizTalk Host.|  
|[MSBTS_Host.GetClusterResourceGroupNames (WMI)](../core/msbts-host-getclusterresourcegroupnames-wmi.md)|Returns List of cluster resource groups available.|  
|[MSBTS_Host.UnCluster Method (WMI)](../core/msbts-host-uncluster-method-wmi.md)|Un-Clusters all BizTalk Host Instances of the given BizTalk Host.|  
  
## Remarks  
 For more information about the minimum security user rights required to administer a Host, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.