---
title: "Get Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Get method"
ms.assetid: 0e621077-f0ef-495c-ba6b-0c6154f48113
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get Method
Used to retrieve properties based on the input key parameters (key1, key2, … keyn). The output parameter is a structure containing the properties of the record that matches the key parameters. If the component interface has only one instance (that is, there is no key), the Get function does not contain any key parameter. Also see [Find Method](../core/find-method.md).  
  
## Syntax  
  
```  
Get (key1, key2, ... keyn, properties)  
Get (key1, key2, ... keyn, getHistoryItems, properties)  
```  
  
## Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`key`|A set of parameters that must exist in the server database; otherwise an error occurs. These keys correspond to the set of Get Keys as defined for the particular Component Interface.|  
|`properties`|Contains a complete structure of the component interface properties, which is returned upon completion of the call.|  
|`getHistoryItems`|A Boolean value. If the properties of the component interface contain effective-dated items below level 0 (that is, a key field with a name of EFFDT) the `getHistoryItems` additional parameter is required.<br /><br /> If the value is:<br /><br /> -   True—All effective dated items are returned as a sequence (which could be embedded in any level). These include all past effective dated items, the current effective dated item, as well as all future effective dated items<br />-   False—Only the current and all future effective dated items are returned. If subsequent calls to update on the same instance will be made, then `getHistoryItems` should be set to False.|  
  
### Remarks  
 If the properties of the component interface contain effective dated items below level 0 (that is, a key field with a name of EFFDT), an additional parameter, `getHistoryItems`, is required. This parameter is of type Boolean. If it is set to True, all effective dated items are returned as a sequence (which could be embedded in any level). These include all past effective dated items, the current effective dated item, as well as all future effective dated items. If the `getHistoryItems` parameter is set to False, only the current and all future effective dated items are returned. If subsequent calls to update on the same instance are to be made, then `getHistoryItems` should be set to False. See also [UpdateEx Method](../core/updateex-method.md).  
  
 If the component interface does not have a key, as in the case where only one instance can exist, then the `Get()` method has the form:  
  
```  
Get(properties)  
```  
  
 For more information on effective dated items, see the PeopleSoft Enterprise documentation.  
  
> [!NOTE]
>  The BizTalk Adapter for PeopleSoft Enterprise `Get()` method is provided if the PeopleSoft `Get` function in the component interface is enabled.  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)