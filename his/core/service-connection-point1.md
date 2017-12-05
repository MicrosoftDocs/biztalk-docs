---
title: "Service Connection Point1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c51b0624-bbf4-4ff1-bd5b-0b6dacdd789d
caps.latest.revision: 5
---
# Service Connection Point
During installation, a Service Connection Point in Active Directory is created by Host Integration Server 2009 that identifies this instance of the product. The Active Directory Schema defines a **serviceConnectionPoint** (SCP) object class to make it easy for a service to publish service-specific data in the directory. Users can search the Global Catalog for all instances of the product’s Service Connection Point. When the Host Integration Server 2009 is uninstalled, the Service Connection Point is removed from Active Directory.  
  
 **Service Connection Point properties**  
  
|Property|Value\Description|  
|--------------|------------------------|  
|serviceClassName|HISServer (matching the SPN used for Kerberos)|  
|serviceBindingInformation|Name of the HIS Subdomain (blank if SNA Gateway is not installed)|  
|serviceDNSNameType|‘A’ (meaning host type)|  
|serviceDNSName|NETBIOS Host name|  
|Keywords|List of words to identify this server.|  
  
 **Keyword list**  
  
|Keyword|Description|  
|-------------|-----------------|  
|“Host Integration Server 2009”|Product Name|  
|“Microsoft”|Company Name|  
|“8.0”|Product Version|  
|{3CA45AFD-4759-4768-9BA2-FA516043DA34}|SNA Gateway|  
|{39707A81-0933-453f-8D90-6A0CFA851D94}|Data Providers|  
|{7609DE49-9AAC-41f0-A606-9BA2D69012A0}|Transaction Integrator|  
|{52163C3B-D6D5-4c71-A768-DA581AA5D632}|Session Integrator|  
  
## See Also  
 [Configuring Your Enterprise](../core/configuring-your-enterprise2.md)