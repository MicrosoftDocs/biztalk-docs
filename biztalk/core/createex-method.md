---
title: "CreateEx Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreateEx method"
ms.assetid: b62bbe25-b24d-42a7-a44c-c83521a6f0a6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CreateEx Method
Creates a new record using a set of unique keys and specified properties.  
  
## Syntax  
  
```  
CreateEx  
(key1, key2, ..., keyn, interactiveMode, properties)  
```  
  
## Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Key in/out parameter`|Individual key parameters (key1, key2, ... keyn), which must be supplied.<br /><br /> This set of keys must not exist in the server database, that is, they must be unique.<br /><br /> These keys correspond to the set of CreateEx Keys as defined for the particular component interface.|  
|`interactiveMode`|Error handling.<br /><br /> When accessing properties in a component interface, Microsoft BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft-provided APIs, which read and write individual fields in the component interface; however, these changes are not propagated to the PeopleSoft server one at a time. Instead, the psjoa.jar (with which the BizTalk Adapter for PeopleSoft Enterprise interacts) packages all the changes and sends the changes to the server in one package.<br /><br /> If any of the individual updates fail, a generic error is returned, which does not pinpoint the actual error. With the interactive mode set to TRUE, every field update is sent to the server individually. This has a substantial impact on performance, but it does provide specific error information if the update fails (for example, if an invalid value is used for setting a field).<br /><br /> The interactiveMode provides maximum performance and provides error reporting at the field update level. To use this feature properly, it is recommended that normal calls be made with the interactiveMode set to FALSE. There should be no impact on performance. If an error is returned, the same call can be retried with the interactiveMode flag set to TRUE. When the call fails, the server returns a more precise error message.|  
|`properties`|A structure that contains all the properties of the component interface. When the `CreateEx` method is called, these properties are inserted into the record created with the specified key(s).|  
  
## Remarks  
 In some situations, it is common practice to call `CreateEx()` without a set of explicit keys, but the `CreateEx` function returns the keys. This behavior is supported with PeopleCode that gets triggered on the server. For example, to create a purchase order, the client may not know what the next available PO number is. By specifying NEXT as the PO number key, the call triggers PeopleCode, which determines the next available PO number. This information must be returned to the calling client, using the in/out key parameters.  
  
> [!NOTE]
>  For this mechanism to work, the key must also be a property at level 0. Otherwise, the original key is returned.  
  
 The BizTalk Adapter for PeopleSoft Enterprise `CreateEx()` method is provided if the PeopleSoft Create and Save functions in the component interface are enabled.  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)