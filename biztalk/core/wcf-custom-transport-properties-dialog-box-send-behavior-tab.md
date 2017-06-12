---
title: "WCF-Custom Transport Properties Dialog Box, Send, Behavior Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.send.behavior"
helpviewer_keywords: 
  - "WCF-Custom adapters, properties"
  - "WCF-Custom adapters, behaviors"
  - "properties, WCF-Custom adapters"
  - "behavior extensions [WCF-Custom adapters]"
ms.assetid: 4e860c1a-d283-48d8-9a7f-c322dfaa374b
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Send, Behavior Tab
You can use the **Behavior** tab to configure the endpoint behavior for this send port. An endpoint behavior is a set of the behavior extension elements that modify or extend service or client functionality. For example, the **callbackTimeOuts** behavior extension element specifies the interval of time within which transactions must complete or be automatically terminated. You can also import and export these settings through the **Import/Export** tab.  
  
> [!NOTE]
>  BizTalk Server does not support all the types of the behavior extension elements that you can configure on the **Behavior** tab.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Behavior**|Display the behavior extension elements configured for this send port. Use the **Select Behavior Extension** dialog box to add or remove the behavior extension elements. To open the dialog box, right-click **EndpointBehavior** in the **Behavior** tree view, and then click **Add extension**. **Note:**  You cannot edit collection type properties such as **ScopedCertificates**. You must import a configuration file on the **Import/Export** tab to configure these properties. For more information about how to specify **ScopedCertificates** in a configuration file, see the WCF product documentation. <br /><br /> The default value is **EndpointBehavior**.|  
|**Select Behavior Extension**|Select a behavior extension element to add to the endpoint behavior. To open this dialog box, right-click **EndpointBehavior** in the **Behavior** tree view, and then click **Add extension**. **Note:**  Behavior extension elements already added to the endpoint behavior are not shown in the **Select Behavior Extension** dialog box.|  
|**Reset all**|Restore the defaults for the **Behavior** tree view and the **Configuration** list view. To run this command, right-click **EndpointBehavior** in the **Behavior** tree view, and then click **Reset all**.|  
|**Remove extension**|Remove the behavior extension selected in the **Behavior** tree view. To run this command, right-click a behavior element in the **Behavior** tree view, and then click **Remove extension**.|  
|**Move extension up**|Move up the order of the behavior extension element selected in the **Behavior** tree view. To run this command, right-click a behavior element in the **Behavior** tree view, and then click **Move extension up**.|  
|**Move extension down**|Move down the order of the behavior extension element selected in the **Behavior** tree view. To run this command, right-click a behavior element in the **Behavior** tree view, and then click **Move extension down**.|  
|**Configuration**|Display the attributes and their values for the behavior element selected in the **Behavior** tree view. You can also modify the attribute values using this list view.|  
|**Restore Defaults**|Restore the defaults for the **Behavior** tree view and the **Configuration** list view.|  
  
## See Also  
 [The \<behaviors> element](http://go.microsoft.com/fwlink/?LinkID=75851)   
 [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)