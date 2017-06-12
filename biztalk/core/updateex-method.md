---
title: "UpdateEx Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UpdateEx method"
ms.assetid: 2fa9c9cc-fd01-4765-8c31-facac188a19d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# UpdateEx Method
Used to update properties based on the input key parameters (key1, key2, … keyn). When using `UpdateEx`, you cannot delete items in a collection. A separate method facilitates deletion. For more information, see [DeleteOnly Method](../core/deleteonly-method.md).  
  
## Syntax  
  
```  
UpdateEx (key1, key2, ... keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`key`|A set of parameters that must exist in the server database, or an error occurs. These keys correspond to the set of Get Keys as defined for the particular component interface.|  
|`correctionMode`|A Boolean flag. When set to true, allows modifications to component interfaces with effective-dated items either by updating the field values, or by inserting new items into a collection. Specifically, it allows modification to items that have EFFDT prior to the current effective date. Without this flag set to TRUE, any modification to these items results in an error returned from PeopleSoft server.<br /><br /> The `correctionMode` argument is only exposed for those component interfaces that contain effective-dated items. Otherwise, it is not shown as part of the argument.<br /><br /> You should avoid setting `correctionMode` to TRUE in a production environment. (This is also the recommendation from PeopleSoft.) Events that have already occurred as determined by the past EFFDT key should not be modified. This allows for the creation of an audit trail. The `correctionMode` flag in `UpdateEx` allows this safety mechanism to be bypassed. The recommended practice is for past events to be deactivated by setting a field in the item, and adding (instead of deleting) the updated item.|  
|`interactiveMode`|A flag used for error handling.<br /><br /> When accessing properties in a component interface, BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft-provided APIs that read and write individual fields in the component interface; however, these changes are not propagated to the PeopleSoft server one at a time. Instead, the psjoa.jar (with which BizTalk Adapter for PeopleSoft Enterprise interacts) packages all the changes and sends the changes to the server in one package. If any of the individual updates fail, a generic error is returned, which does not pinpoint the actual error. With the interactive mode set to TRUE, every field update is sent to the server individually. This has a substantial impact on performance, but it does provide specific error information if the update fails (for example, if an invalid value is used for setting a field).<br /><br /> The `interactiveMode` provides maximum performance and provides error reporting at the field update level. To use this feature properly, it is recommended that you make normal calls with `interactiveMode` set to FALSE. There should be no impact on performance. If an error is returned, the same call can be retried with the `interactiveMode` flag set to TRUE. When the call fails, the server returns a more precise error message.|  
  
### Remarks  
 When you call this function, the properties of the record corresponding to the keys are replaced by the input parameter properties. All collections with the original records are deleted and replaced by those in the input parameter. The sizes of these collections do not have to matchbecause the procedure within `UpdateEx` is to delete all existing collection items and then insert the given ones.  
  
 If the properties of the component interface contain effective dated items, the properties parameter must contain all future effective-dated items because the original list is replaced. This provides the mechanism for adding and deleting future effective-dated items; however, if the properties also contain past effective-dated items, an error is returned because past effective-dated items cannot be modified. If the current effective-dated item is also included, it is ignored. This permits the client to call `Get()` with the `getHistoryItems` parameter set to False, and modify any future effective-dated items or add new future effective-dated items, and pass in the structure as parameter for the `UpdateEx()` function.  
  
 If the component interface does not have a key, as in the case where only one instance can exist, the `UpdateEx()` method has the form:  
  
```  
UpdateEx(correctionMode, interactiveMode, properties)  
```  
  
> [!NOTE]
>  The BizTalk Adapter for PeopleSoft Enterprise `UpdateEx()` method is provided if the PeopleSoft `Get` and `Save` functions in the component interface are enabled.  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)