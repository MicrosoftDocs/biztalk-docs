---
title: "Updating an Existing Configuration with a Binding File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "binding files, updating"
  - "binding files, rules"
  - "artifacts, binding files"
  - "binding files, unbinding"
  - "binding files, customizing"
  - "artifacts, updating"
ms.assetid: 11580e59-7147-42d0-a976-f6b5e6933d24
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Updating an Existing Configuration with a Binding File
Information in a binding file supersedes existing configuration information. If the name of an artifact in a binding file matches the name of an artifact in your existing configuration, the artifact in the binding file will update the artifact in your existing configuration when you import the binding file.  
  
 When updating existing artifacts with binding file artifacts, certain rules are followed. This topic discusses the rules that are followed when updating artifacts in an existing configuration with artifacts in a binding file.  
  
 This section assumes that valid values are present in the binding file when the file is imported and does not discuss any scenario where a binding file contains invalid values.  
  
## Rules followed by BizTalk Server when updating a configuration with a binding file  
 BizTalk Server follows certain rules when updating existing artifacts with matching artifacts in a binding file. In general, the following rules are applied:  
  
- Text boxes and check boxes that are exposed when configuring an artifact via the BizTalk Server user interface (such as the BizTalk Server Administration console or BizTalk Explorer), must either be set to a specific value or be empty. Values supplied for artifacts in a binding file will set the user interface value for the updated item accordingly.  
  
- Drop-down boxes that are exposed when configuring an artifact via the BizTalk Server user interface must either be set to a specific value or be set to "None". Values supplied for artifacts in a binding file will set the user interface value for the updated item accordingly.  
  
- Datagrid views that are exposed when configuring an artifact via the BizTalk Server user interface are updated with lists from the corresponding item in the binding file. The list associated with a datagrid view is always overwritten by the list in the binding file unless the datagrid view list is tied to a port or a receive location. In this case the list in the binding file is merged with the existing datagrid view list.  
  
- Artifacts in the binding file are identified by a primary key value. The value associated with the primary key for an artifact can never be set to null in the user interface and so all artifacts in a binding file must have their primary key value set. If the value associated with the primary key for an artifact in the binding file matches the value associated with the primary key for an existing configuration artifact then these artifacts are considered to be identical or matching. If the binding file artifact and the existing artifact are identical then the existing artifact is updated with the binding file artifact as described in the table below. If an artifact in the binding file contains a unique primary key value then a new artifact is created in the BizTalk Server configuration when the binding file is imported.  
  
  The following table describes expected behavior if you are updating existing configuration artifacts with matching artifacts by importing a binding file.  
  
|Artifact type|Property|Possible occurrences of specified property|User interface field|Impact of importing matching artifact from binding file.|  
|-------------------|--------------|------------------------------------------------|--------------------------|--------------------------------------------------------------|  
|**Party**|Name|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Primary key|  
||Aliases|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Overwrite the list of aliases with the list of aliases in the binding file.|  
||Send Ports|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Merge the existing list of ports for this party with the list of ports for this party in the binding file.|  
||Certificate Common Name and Thumbprint|Min Occurs: 0<br /><br /> Max Occurs: 1<br /><br /> (per property)|Text box|Overwrite these values with the values specified in binding file. If these values do not exist in the binding file then set to null.|  
|**Orchestration**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Host|Min Occurs: 0<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in binding file. If this value does not exist in the binding file then set to null.|  
||Inbound ports and outbound ports|Min Occurs: 0<br /><br /> Max Occurs: *|Drop down|Bind a logical port to an existing physical port. The physical port can exist in the following locations:<br /><br /> -   In the group.<br />-   In the application.<br />-   In the binding file.<br /><br /> Optionally set the port to **None**. If set to **None** then the logical port is not bound to any resource.|  
||Tracking properties check boxes|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (per property)|Check box|Overwrite these values with the values specified in the binding file.|  
|**Send Port Group**|Name|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Primary key|  
||Send ports|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Merge the existing list of ports for this send port group with the list of ports for this send port group specified in the binding file.|  
||Filters|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Overwrite the existing list of filters for this send port group with the list of filters for this send port group specified in the binding file.|  
|**Send Port**|Name|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Primary key|  
||Transport - Type|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Transport - Send handler|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Send pipeline|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Retry Count, Retry interval, and Priority|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (Per property)|Scroll box|Overwrite these values with the values specified in the binding file.|  
||Ordered delivery|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Enable routing for failed messages|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Enable Service window|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Service window Start time and service window Stop time|Min Occurs: 1<br /><br /> Max Occurs: 1|Scroll box|Overwrite these values with the values specified in the binding file.|  
||Maps|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Overwrite the existing list of maps for this send port with the list of maps for this send port specified in the binding file.|  
||Filter|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Overwrite the existing list of filters for this send port with the list of filters for this send port specified in the binding file.|  
||Certificate Common Name|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Certificate Thumbprint|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Tracking|Min Occurs: 0<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Backup Transport Type|Min Occurs: 0<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Backup Transport URI|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file. Only valid if the backup transport Type is set.|  
||Backup Transport Send handler|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file. Only valid if the backup transport Type is set.|  
||Backup Transport Retry count|Min Occurs: 1<br /><br /> Max Occurs: 1|Scroll box|Overwrite this value with the value specified in the binding file. Only valid if the backup transport Type is set.|  
||Backup Transport Retry interval|Min Occurs: 1<br /><br /> Max Occurs: 1|Scroll box|Overwrite this value with the value specified in the binding file. Only valid if the backup transport Type is set.|  
||Backup Transport Enable service window|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file. Only valid if the backup transport Type is set.|  
||Backup Transport Service window Start time and service window Stop time|Min Occurs: 1<br /><br /> Max Occurs: 1|Scroll box|Overwrite these values with the values specified in the binding file. Only valid if the backup transport Type is set and the Enable service window value is set.|  
|**Receive Port**|Name|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Primary key|  
||Authentication Settings (radio buttons)|Min Occurs: 1<br /><br /> Max Occurs: 1|Radio button|Overwrite this value with the value specified in the binding file.|  
||Enable Failed Message Routing|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Description|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Receive Locations|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Overwrite the existing list of receive locations for this receive port with the list of receive locations for this receive port specified in the binding file. If all of the receive locations in the binding file already exist in the group then import fails.|  
||Maps|Min Occurs: 0<br /><br /> Max Occurs: *|Data grid|Overwrite the existing list of maps for this receive port with the list of maps for this receive port specified in the binding file.|  
||Tracking - Track Message Bodies and Track Message Properties|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (per checkbox)|Check box|Overwrite these values with the values specified in the binding file.|  
|**Receive Location**|Name|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Primary Key|  
||Transport type|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Receive Handler|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Pipeline|Min Occurs: 1<br /><br /> Max Occurs: 1|Drop down|Overwrite this value with the value specified in the binding file.|  
||Description|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Schedule Start date and Stop date check boxes and drop-down boxes.|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box and drop down box.|Overwrite these values with the values specified in the binding file. Date values are imported even if the check box values are not enabled.|  
||Enable service window check box|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Service window Start time and service window Stop time|Min Occurs: 1<br /><br /> Max Occurs: 1|Scroll box|Overwrite these values with the values specified in the binding file. Only valid if the Enable service window value is set.|  
|**Schema**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Tracking - Always track all properties|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file.|  
||Tracking - Select all message properties|Min Occurs: 1<br /><br /> Max Occurs: 1|Check box|Overwrite this value with the value specified in the binding file. If this value is enabled than all message properties that can be checked are also enabled.|  
||Tracking – individual properties|Min Occurs: 0<br /><br /> Max Occurs: *|Check boxes|Overwrite the existing list of tracked properties for this schema with the list of tracked properties for this schema specified in the binding file.<br /><br /> If a binding file is imported which refers to tracked properties that are not available for the existing schema an error is generated.|  
|**Map**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
|**Pipeline**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|Text box|Overwrite this value with the value specified in the binding file.|  
||Track Events|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (per checkbox)|Check box|Overwrite these values with the values specified in the binding file.|  
||Track Message Bodies|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (per checkbox)|Check box|Overwrite these values with the values specified in the binding file.|  
|**Policy**|Not applicable. Policies are not exportable to a binding file.|Not applicable|Not applicable|Not applicable|  
|**Role Link**|Not applicable. Role links are not exportable to a binding file.|Not applicable|Not applicable|Not applicable|  
  
## Unbinding behavior when updating existing artifacts with matching artifacts in a binding file  
 Binding file artifacts are typically configured to reference other artifacts, for example a receive port is typically configured to reference a receive location. In this scenario, the receive port is the parent artifact and the receive location is the child artifact. The receive port is **explicitly** configured to reference the receive location and the receive location then **implicitly** references the receive port. If incompletely configured parent artifacts in a binding file exist, for example a receive port that is not configured with a receive location, then they will be incompletely configured after the binding file is imported regardless of their state in the existing configuration. So for example, if you have an existing receive port myRP configured with receive location myRL and the identical receive port myRP in the binding file is **not** configured with receive location myRL, then the binding file entry takes precedence. For this example receive port myRP will not be configured with a receive location after importing the binding file so you will have effectively **unbound** myRL from myRP.  
  
 This rule only applies when importing artifacts that make explicit references and not when importing artifacts with implicit references. So if you imported a map that implicitly references (is explicitly referenced by) 10 other artifacts you would not have to be concerned that the map would be un-bound from the implicitly referenced artifacts.  
  
## See Also  
 [Customizing Binding Files](../core/customizing-binding-files.md)