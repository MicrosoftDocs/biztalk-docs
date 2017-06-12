---
title: "Configure Application Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.application.configure"
ms.assetid: c4ec8bdf-fad6-4f55-bc2a-63418b322bd6
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure Application Dialog Box
Use the **Configure Application** dialog box to bind logical ports and role links to physical ports and parties, configure the host under which these execute, and configure send and receive ports, send port groups, and receive port locations. Artifacts in this dialog box must be completely configured or the application will not start.  
  
## Orchestrations Tab  
 The Orchestrations tab contains a node for each orchestration in the project. Click each orchestration name to view and configure related properties. Applications that are CBR or Messaging applications only do not display an **Orchestrations** tab because no orchestrations are included in the application. The information displayed for each orchestration is identical to the information on the **Bindings** tab in the **Orchestration Properties** window.  
  
### \<Orchestration Name>  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host**|From the drop-down list, select a host on which to enlist the application.|  
|**Bindings - Inbound Logical Ports**|Displays the name of a logical inbound port. Logical ports are found on the port surfaces in orchestrations.|  
|**Bindings - Receive Ports**|From the drop-down list, select the physical receive port that you want to bind to the corresponding inbound logical port.|  
|**Bindings - Outbound Logical Ports**|Displays the name of a logical outbound port. Logical ports are found on the port surfaces in orchestrations.|  
|**Bindings - Send Ports/Send Port Groups**|From the drop-down list, select the send port or send port group that you want to bind to the corresponding outbound logical port.|  
  
## Messaging Tab  
  
### Send Ports and Send Port Groups  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**New**|Click to create a new send port or send port group. Options for send ports are identical to the options available when you right-click the **Send Ports** node in the Administrative Console tree and point to **New**.|  
|**Properties**|Click to display the properties window for the selected send port or send port group. If you select a send port, the **Send Port Properties** window appears, where you can configure the port. If you select a send port group, the **Send Port Groups Properties** window appears, where you can configure the send port group.|  
|**Name**|Displays the name of the physical send ports bound to the orchestration.|  
|**Filter**|Displays the filter expression applied to the send port. Filters are set up in the **Send Port Properties** window.|  
|**URI**|Displays the URI for the selected port.|  
  
## Receive Ports and Locations  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**New**|Click to create a new receive port. Options for new receive ports are identical to the options available when you right-click the **Receive Ports** node in the Administrative Console tree and point to **New**.|  
|**Properties**|Click to display the properties window for the selected item. If you have selected a receive port, the **Receive Port Properties** window appears, where you can configure the port. If you have selected a receive port location, the **Receive Locations Properties** window appears, where you can configure the receive location. To select a receive port, click the boldface text to the right of **Receive port**.|  
|**Name**|Displays the name of the receive location associated with a receive port.|  
|**URI**|Displays the URI for the selected receive location.|  
  
## Role Links Tab  
  
### \<Role Link Name>  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enlist**|Click to display the **Enlist Parties** dialog box, where you can select a party to participate in the interchange defined by the role.|  
|**Unenlist**|Click to remove the selected party from participating in the interchange.|  
|**Bind**|Click to establish a connection between the role link and the physical ports.|  
|**Party**|Displays the name of the party or parties that you have enlisted to this role.|  
  
## See Also  
 [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md)