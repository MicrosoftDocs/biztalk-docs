---
title: "DeleteOnly Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeleteOnly method"
ms.assetid: 99e1d7af-1450-439b-882f-de677e593bee
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DeleteOnly Method
Allows you to delete items in a collection.  
  
## Syntax  
  
```  
DeleteOnly(key1, key2, ..., keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`key`|Is a set of parameters that must be supplied. This set of keys must exist in the server database, or an error occurs. These keys correspond to the set of Get Keys as defined for the particular component interface.|  
|`correctionMode`|A Boolean flag. When set to true, allows deletion of past effective-dated items in a collection. Specifically, it allows the deletion of items that have EFFDT prior to the current effective date. Without this flag set to TRUE, any modification to these items results in an error returned from PeopleSoft server. **Note:**  The `correctionMode` argument is only exposed for those component interfaces that contain effective-dated items. Otherwise it is not shown as part of the argument.|  
|`interactiveMode`|Used for error handling.<br /><br /> When accessing properties in a component interface, the BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft-provided APIs, which read and write individual fields in the component interface; however, these changes are not propagated to the PeopleSoft server one at a time. Instead, the psjoa.jar (with which the BizTalk Adapter for PeopleSoft Enterprise interacts) packages all the changes and sends the changes to the server in one package. If any of the individual updates fail, a generic error is returned, which does not pinpoint the actual error. With the interactive mode set to TRUE, every field update is sent to the server individually. This has a substantial impact on performance, but it does provide specific error information if the update fails (for example, if an invalid value is used for setting a field).<br /><br /> The `interactiveMode` parameter provides maximum performance and provides error reporting at the field-update level. To use this feature properly, it is recommended that you make normal calls with `interactiveMode` set to FALSE. There should be no impact on performance. If an error is returned, the same call can be retried with the interactiveMode flag set to TRUE. When the call fails, the server returns a more precise error message.|  
|`properties`|Contains a subset of the structure that exists on the server. All items that are leaves are deleted.|  
  
## Remarks  
 The properties have the same data type as the `CreateEx` or `UpdateEx` methods of this component interface; however, only the key values are important. The non-key values are ignored. The key values must match those on the server, otherwise an exception is raised.  
  
 The following demonstrates the use of the key values. If a collection contains the items:  
  
- item0  
  
- item1  
  
- item2  
  
- item3  
  
  You can delete item1 and item3 by providing the keys of item1 and item3 in the properties:  
  
- item1  
  
- item3  
  
  After the call, the server has the remaining items in the collection:  
  
- item0  
  
- item2  
  
  The second example shows the items containing other collections:  
  
- item0  
  
  -   item0a  
  
- item1  
  
  -   item1a  
  
  -   item1b  
  
  -   item1c  
  
- item2  
  
  -   item2a  
  
  -   item2b  
  
  You can delete item1b and all of item2 by giving the keys to item1b and item2:  
  
- item1  
  
  -   item1b  
  
- item2  
  
  By providing an empty sub-collection for item2, you turn it into a leaf and that entire sub-branch is deleted. After the call, the server has the remaining items:  
  
- item0  
  
  -   item0a  
  
- item1  
  
  -   item1a  
  
  -   item1c  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)