---
title: "Adapter Registry Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "utilities, Adapter Registration Wizard"
  - "Adapter Registration Wizard"
ms.assetid: bd15d0c7-01bb-41f9-9157-cdcf4bb4e39a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Registry Wizard
You use the Adapter Registry Wizard to create the registry files needed to configure and register a custom adapter.  

## Location in SDK  
 *\<Installation Path\>*\SDK\Utilities\AdapterRegistryWizard\  

## To Run This Utility  
 Start the wizard by running the AdapterRegistryWizard.exe executable. The pages that follow prompt you for information about your adapter and the properties that it supports. The individual Adapter Registry Wizard pages are described in the sections that follow.  

### Generic Adapter Properties page  
 Use the Generic Adapter Properties page to specify adapter properties.  


|                              Use this                              |                                                                                           To do this                                                                                           |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                     **Transport adapter type**                     |                                                                                   Specify the adapter type.                                                                                    |
|                       **Property namespace**                       | Specify the adapter namespace. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores adapter-specific properties on the message context in this namespace. |
| **Adapter can receive messages and submit them to BizTalk Server** |                                  Identify communication patterns supported by the adapter. Used to calculate the Constraints registry entry for the adapter.                                   |
|         **Adapter can send messages from BizTalk Server**          |                                  Identify communication patterns supported by the adapter. Used to calculate the Constraints registry entry for the adapter.                                   |

### Inbound Part page  
 Use the Inbound Part page to specify inbound receiving logic for your adapter.  

|Use this|To do this|  
|--------------|----------------|  
|**Browse**|Select the assembly that implements the inbound receiving logic for your adapter. A list of the public types exposed by this assembly appear in the drop-down list. Select the type within the specified assembly that implements the inbound logic for this adapter from the drop-down list.|  
|**Adapter supports request-response protocol**|Specify the receive capabilities of your adapter. Used to calculate the Constraints registry entry for your adapter.|  
|**Adapter is isolated (that is hosted in a different process)**|Specify the receive capabilities of your adapter. Used to calculate the Constraints registry entry for your adapter.|  

### Outbound Part page  
 Use the Outbound Part page to specify outbound receiving logic for your adapter.  

|Use this|To do this|  
|--------------|----------------|  
|**Browse**|Select the assembly that implements the outbound receiving logic for your adapter. A list of the public types exposed by this assembly appears in the drop-down list . Select the type for the specified assembly that implements the outbound logic for this adapter from the drop-down list. You must also enter a comma-separated list of aliases used to identify the protocol used by this adapter (for example, submit://).|  
|**Adapter supports solicit-response protocol**|Identify the transmitting capabilities of your adapter. These values are used to calculate the Constraints registry entry for your adapter.|  

### Adapter Management page  
 Use the Adapter Management page to specify design-time management logic for your adapter.  

|Use this|To do this|  
|--------------|----------------|  
|**Browse**|Select the assembly that implements the design-time adapter management logic for your adapter. A list of the public types exposed by this assembly appears in the drop-down list. Select the type for the specified assembly that implements the adapter management logic for this adapter from the drop-down list.|  

### Output File name  
 Use the Output file name page to specify an output file name and location.  

|Use this|To do this|  
|--------------|----------------|  
|**Browse**|Choose an output file name and location. The adapter registry is written to this file.|  

## Remarks  
 The Adapter Registry Wizard utility populates the Enterprise Single Sign-On (SSO) configuration store properties with default values. If your adapter does not use the standard property pages provided by the Adapter Framework for handler and location adapter properties, you must edit the registry file manually to modify these values. For more information about these settings, see "Registration of adapter properties for SSO configuration store" in the topic [Registering an Adapter](../core/registering-an-adapter.md).  

## See Also  
 [Utilities in the SDK](../core/utilities-in-the-sdk.md)   
 [Registering an Adapter](../core/registering-an-adapter.md)