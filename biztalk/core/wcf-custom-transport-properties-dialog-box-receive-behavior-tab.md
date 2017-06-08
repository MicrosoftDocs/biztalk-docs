---
title: "WCF-Custom Transport Properties Dialog Box, Receive, Behavior Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.receive.behavior"
helpviewer_keywords: 
  - "WCF-Custom adapters, properties"
  - "WCF-Custom adapters, behaviors"
  - "properties, WCF-Custom adapters"
  - "behavior extensions [WCF-Custom adapters]"
ms.assetid: 518172d2-4213-493b-8f7c-f1ef78c25732
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Receive, Behavior Tab
Use the **Behavior** tab to configure the endpoint and service behaviors for this receive location. An endpoint behavior is a set of behavior extension elements that modify or extend service or client functionality. For example, the **callbackTimeOuts** behavior extension element specifies the interval of time for the client callback within which transactions must complete or be automatically terminated. A service behavior is a set of behavior extension elements that modify or extend service functionality. For example, the **serviceTimeOuts** behavior extension element specifies the interval of time for a service within which transactions must complete or be automatically aborted. You can also import and export these settings through the **Import/Export** tab.  
  
> [!NOTE]
>  Service behaviors affect only service-related aspects, and endpoint behaviors affect only endpoint-related properties.  
  
> [!NOTE]
>  BizTalk Server does not support all the types of the behavior extension elements that you can configure on the **Behavior** tab.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Behavior**|Display the service and endpoint behavior and their behavior extension elements configured for this receive location. Use the **Select Behavior Extension** dialog box to add or remove the behavior extension elements for each behavior. To open the dialog box, right-click **EndpointBehavior** or **ServiceBehavior** in the **Behavior** tree view, and then click **Add extension**. **Note:**  You cannot edit collection type properties such as **ScopedCertificates**, **AuthorizationPolicies**, and **KnownCertificates**. You must import a configuration file on the **Import/Export** tab to configure these properties. For more information about how to specify **ScopedCertificates**, **AuthorizationPolicies**, and **KownCertificates** in a configuration file, see the WCF product documentation. <br /><br /> The default values are **EndpointBehavior** and **ServiceBehavior**. **Note:**  In order for the impersonation scenario to work in the WCF-Custom receive adapter, you must add the **serviceAuthorization** extension under the **ServiceBehavior** and then set the **ImpersonateCallerForAllOperations** to **true** as well as select the **Issue Single Sign-On ticket** option under the **Other** tab in the **WCF-Custom Transport Properties** dialog.|  
|**Select Behavior Extension**|Select a behavior extension element to add to the behavior selected in the **Behavior** tree view. To open this dialog box, right-click **ServiceBehavior** or **EndpointBehavior** in the **Behavior** tree view, and then click **Add extension**. **Note:**  Behavior extension elements already added to the behavior are not shown in the **Select Behavior Extension** dialog box.|  
|**Reset all**|Restore the defaults for the behavior selected in the **Behavior** tree view, and the behavior's extension elements in the **Configuration** list view. To run this command, right-click **ServiceBehavior** or **EndpointBehavior** in the **Behavior** tree view, and then click **Reset all**.|  
|**Remove extension**|Remove the behavior extension element selected in the **Behavior** tree view. To run this command, right-click a behavior element in the **Behavior** tree view, and then click **Remove extension**.|  
|**Move extension up**|Move up the order of the behavior extension element selected in the **Behavior** tree view. To run this command, right-click a behavior element in the **Behavior** tree view, and then click **Move extension up**.|  
|**Move extension down**|Move down the order of the behavior extension element selected in the **Behavior** tree view. To run this command, right-click a behavior element in the **Behavior** tree view, and then click **Move extension down**.|  
|**Configuration**|Display the attributes and their values for the behavior element selected in the **Behavior** tree view. You can also modify the attribute values using this list view.|  
|**Restore Defaults**|Restore the defaults for the **Behavior** tree view and the **Configuration** list view.|  
  
## See Also  
 [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)   
 [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)   
 [The \<behaviors> element](http://go.microsoft.com/fwlink/?LinkID=75851)