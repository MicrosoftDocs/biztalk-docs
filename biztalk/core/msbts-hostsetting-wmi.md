---
title: "MSBTS_HostSetting (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59e7065d-178d-4d74-8a3e-77cb0068e89f
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting (WMI)
Creates a Microsoft BizTalk Server host setting.  
  
## Declaration  
  
```  
class MSBTS_HostSetting : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_AppTypeSetting** defines the following properties/methods:  
  
|Property|Description|  
|--------------|-----------------|  
|[AuthTrusted](../core/msbts-hostsetting-authtrusted-property-wmi.md)|Indicates whether a BizTalk host can be trusted to collect authentication information.|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkId=83193](http://go.microsoft.com/fwlink/?LinkId=83193).|  
|[MSBTS_HostSetting.ClusterResourceGroupName Property (WMI)](../core/msbts-hostsetting-clusterresourcegroupname-property-wmi.md)|When the host instances of this host are clustered, this property contains the cluster resource group name set by the Administrator.|  
|[MSBTS_HostSetting.DBQueueSizeThreshold Property (WMI)](../core/msbts-hostsetting-dbqueuesizethreshold-property-wmi.md)|Maximum number of items in the Database.|  
|[MSBTS_HostSetting.DBSessionThreshold Property (WMI)](../core/msbts-hostsetting-dbsessionthreshold-property-wmi.md)|Maximum number of DB Sessions (per CPU) allowed before throttling begins.|  
|[DecryptCertComment](../core/msbts-hostsetting-decryptcertcomment-property-wmi.md)|Represents a comment field that allows you to associate a friendly name with a decryption certificate.|  
|[DecryptCertThumbprint](../core/msbts-hostsetting-decryptcertthumbprint-property-wmi.md)|Contains the thumbprint of the decryption certificate.|  
|[MSBTS_HostSetting.DeliveryQueueSize Property (WMI)](../core/msbts-hostsetting-deliveryqueuesize-property-wmi.md)|Size of the in-memory Queue that the host maintains as a temporary placeholder for delivering messages.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkId=83193](http://go.microsoft.com/fwlink/?LinkId=83193).|  
|[MSBTS_HostSetting.GlobalMemoryThreshold Property (WMI)](../core/msbts-hostsetting-globalmemorythreshold-property-wmi.md)|Maximum System-wide Virtual Memory (in percent) usage allowed before throttling begins.|  
|[HostTracking](../core/msbts-hostsetting-hosttracking-property-wmi.md)|Indicates whether instances of this BizTalk Host will host the tracking sub service.|  
|[HostType](../core/msbts-hostsetting-hosttype-property-wmi.md)|Indicates which runtime model the instances of the BizTalk Host will be running in.|  
|[MSBTS_HostSetting.InflightMessageThreshold Property (WMI)](../core/msbts-hostsetting-inflightmessagethreshold-property-wmi.md)|Maximum number of in-memory in-flight messages allowed before throttling Message Delivery begins.|  
|[IsDefault](../core/msbts-hostsetting-isdefault-property-wmi.md)|Indicates whether the BizTalk Host represented by this WMI instance is the default BizTalk Host in the BizTalk group.|  
|[MSBTS_HostSetting.IsHost32BitOnly Property (WMI)](../core/msbts-hostsetting-ishost32bitonly-property-wmi.md)|This property indicates whether the host instance process should be created as 32-bit on both 32-bit and 64-bit servers.|  
|[LastUsedLogon](../core/msbts-hostsetting-lastusedlogon-property-wmi.md)|Contains a default logon for the BizTalk Host instance creation user interface.|  
|[MSBTS_HostSetting.MessageDeliverySampleSpaceSize Property (WMI)](../core/msbts-hostsetting-messagedeliverysamplespacesize-property-wmi.md)|This property indicates the number of samples that are used for determining the rate of the Message Delivery to all Service Classes of the Host|  
|[MSBTS_HostSetting.MessageDeliverySampleSpaceWindow (WMI)](../core/msbts-hostsetting-messagedeliverysamplespacewindow-wmi.md)|Time-window (in milliseconds) beyond which samples will be deemed invalid for consideration.|  
|[MSBTS_HostSetting.MessageDeliveryOverdriveFactor Property (WMI)](../core/msbts-hostsetting-messagedeliveryoverdrivefactor-property-wmi.md)|Percent factor by which the system will overdrive the Input rate for Message Delivery Throttling.|  
|[MSBTS_HostSetting.MessageDeliveryMaximumDelay Property (WMI)](../core/msbts-hostsetting-messagedeliverymaximumdelay-property-wmi.md)|Maximum Delay (in milliseconds) imposed for Message Delivery Throttling. Zero indicates disable Message Delivery Throttling.|  
|[MSBTS_HostSetting.MessagePublishSampleSpaceSize Property (WMI)](../core/msbts-hostsetting-messagepublishsamplespacesize-property-wmi.md)|Number of samples that are used for determining the rate of the Message Publishing by the Service Classes.|  
|[MSBTS_HostSetting.MessagePublishSampleSpaceWindow Property (WMI)](../core/msbts-hostsetting-messagepublishsamplespacewindow-property-wmi.md)|Time-window (in milliseconds) beyond which samples will be deemed invalid for consideration.|  
|[MSBTS_HostSetting.MessagePublishOverdriveFactor Property (WMI)](../core/msbts-hostsetting-messagepublishoverdrivefactor-property-wmi.md)|Percent Factor by which the system will overdrive the Input rate.|  
|[MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI)](../core/msbts-hostsetting-messagepublishmaximumdelay-property-wmi.md)|Maximum Delay (in milliseconds) imposed for Message Publishing Throttling. Zero indicates disable Message Publishing Throttling.|  
|[MgmtDbNameOverride](../core/msbts-hostsetting-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-hostsetting-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-hostsetting-name-property-wmi.md)|Contains the name of the BizTalk host.|  
|[NTGroupName](../core/msbts-hostsetting-ntgroupname-property-wmi.md)|Contains the name of the Windows NT group.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkId=83193](http://go.microsoft.com/fwlink/?LinkId=83193).|  
|[MSBTS_HostSetting.ThreadPoolSize Property (WMI)](../core/msbts-hostsetting-threadpoolsize-property-wmi.md)|Maximum number of messaging engine threads per CPU.|  
|[MSBTS_HostSetting.ThreadThreshold Property (WMI)](../core/msbts-hostsetting-threadthreshold-property-wmi.md)|Maximum number of threads in the process (per CPU) allowed before throttling begins.|  
|[MSBTS_HostSetting.ProcessMemoryThreshold Property (WMI)](../core/msbts-hostsetting-processmemorythreshold-property-wmi.md)|Maximum Process Memory (in percent) allowed before throttling begins.|  
  
## Remarks  
 For sample code using the MSBTS_HostSetting class, see [Creating, Updating, and Deleting a Host Instance Using WMI](../core/creating-updating-and-deleting-a-host-instance-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.