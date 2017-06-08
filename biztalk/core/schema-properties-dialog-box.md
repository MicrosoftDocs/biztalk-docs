---
title: "Schema Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.schema.properties"
ms.assetid: d81bff33-aa23-48bc-b77e-67993de1ae3c
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Properties Dialog Box
Use the **Schema Properties** window to view detailed properties about the schemas in the project. You can also select properties for tracking and locating messages.  
  
## General Tab  
 Schema properties on the **General** tab—typically properties that schemas share with items such as maps and orchestrations—are configured in Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. The **Description** box is an exception; you can edit it in the **Schema Properties** window.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Displays the full name of the schema.|  
|**Assembly**|Displays the fully qualified name (name, version, culture, public key token) of the assembly that deploys the schema.|  
|**Type**|Indicates whether the schema is a document schema (a message instance) or a property schema.|  
|**Root name**|Displays the name of the root node of the schema.|  
|**Target namespace**|Displays the path of the selected schema's target namespace.|  
|**Description**|Type any text that helps you distinguish this schema from others. The maximum number of characters allowed is 256.|  
  
## Schema View Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Schema**|Displays the contents of an XML Schema Definition (XSD) associated with the application.|  
  
## Tracking Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Always track all properties**|Select this check box to indicate that all properties should be tracked regardless of version. This check box is available only for document schemas.|  
|**Select all message properties**|Select this check box to add all the listed properties to the Tracking database.|  
|**Properties list**|Select the check box for each property that you want to use for tracking and locating messages.|  
  
## See Also  
 [XML Schemas](../core/xml-schemas.md)   
 [Different Types of BizTalk Schemas](../core/different-types-of-biztalk-schemas.md)   
 [Property Schemas](../core/property-schemas.md)