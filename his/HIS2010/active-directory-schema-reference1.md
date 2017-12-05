---
title: "Active Directory Schema Reference1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9cfd288f-c5e1-4439-9b49-159533e72171
caps.latest.revision: 3
---
# Active Directory Schema Reference
The Active Directory schema contains formal definitions of every object class that can be created in an Active Directory forest. The schema also contains formal definitions of every attribute that can exist on an Active Directory object. The Active Directory global catalog contains replicas of all the objects for the forest, along with a subset of the attributes for each object. This topic contains the following sections:  
  
-   [Active Directory Classes](../HIS2010/active-directory-schema-reference1.md#bkmk_ADClasses)  
  
-   [Active Directory Attributes](../HIS2010/active-directory-schema-reference1.md#bkmk_ADAttributes)  
  
> [!NOTE]
>  The Host Integration Server Active Directory schema does not follow the Microsoft standards for naming schema for both the common-name (CN) and the LDAP display name (ldapDisplayName) of schema objects. The original schema has not been updated to maintain backwards compatibility with older versions of the product.  
  
##  <a name="bkmk_ADClasses"></a> Active Directory Classes  
 The following table describes the Active Directory classes.  
  
|||  
|-|-|  
|**Class Name**|**Description**|  
|MS-HostIntegrationServer-Global-Params|Container class for the SNA Sub-domain name.|  
|MS-HostIntegrationServer-WMI-Provider|Container class for instances of Host Integration Server WMI providers that can be used for resource location.|  
|MS-HostIntegrationServer-MQBridgeConfiguration|Deprecated|  
|MS-HostIntegrationServer-Service|Container class for instances of Host Integration Server services.|  
  
##  <a name="bkmk_ADAttributes"></a> Active Directory Attributes  
 The following table describes Active Directory attributes.  
  
|||  
|-|-|  
|**Attribute Name**|**Description**|  
|MS-HostIntegrationServer-Config-Path|Indicates the location of the shared configuration for an instance of the MS-HostIntegrationServer-Service class.|  
|MS-HostIntegrationServer-Server-Role|Indicates whether an instance of the MS-HostIntegrationServer-Service class has primary responsibility for the configuration or is a backup.|  
|MS-HostIntegrationServer-Service-State|Indicates the state of the Window service represented by an instance of the MS-HostIntegrationServer-Service class.|  
|MS-HostIntegrationServer-Major-Version|Indicates the major version of the product for an instance of the MS-HostIntegrationServer-Service class.|  
|MS-HostIntegrationServer-Minor-Version|Indicates the minor version of the product for an instance of the MS-HostIntegrationServer-Service class.|  
|MS-HostIntegrationServer-Domain-Name|Name for the logical grouping of Host Integration Servers that can provide load-balancing of resources.|  
|MS-HostIntegrationServer-MQBridgePublicKeyInfo|Deprecated|  
|MS-HostIntegrationServer-MQBridgeRole|Deprecated|  
|MS-HostIntegrationServer-PrimaryMQBridgeName|Deprecated|  
|MS-HostIntegrationServer-MQBridgeForeignComputer|Deprecated|  
|MS-HostIntegrationServer-MQBridgeEnableEncryption|Deprecated|  
  
## See Also  
 [Active Directory Services](../HIS2010/active-directory-services1.md)   
 [How Host Integration Server Uses Active Directory](../HIS2010/how-host-integration-server-uses-active-directory1.md)   
 [How to Configure Active Directory During Host Integration Server Installation](../HIS2010/how-to-configure-active-directory-during-host-integration-server-installation2.md)