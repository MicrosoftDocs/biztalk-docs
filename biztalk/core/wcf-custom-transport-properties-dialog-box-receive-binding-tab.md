---
title: "WCF-Custom Transport Properties Dialog Box, Receive, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.receive.binding"
helpviewer_keywords: 
  - "bindings, WCF-Custom adapters"
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
  - "WCF-Custom adapters, bindings"
ms.assetid: 68c748ba-3bc5-4582-8284-1cb941ef0940
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Receive, Binding Tab
Use the **Binding** tab to configure different types of predefined or custom bindings for Windows Communication Foundation (WCF). You can also import and export these settings through the **Import/Export** tab.  
  
> [!NOTE]
>  BizTalk Server does not support all the types of the binding extension elements that you can configure on the **Binding** tab.  
  
## Predefined Binding  
 Predefined bindings hide the complexity of the WCF messaging stack. Applications using predefined bindings do not require full control over the stack. The attributes exposed on each predefined binding are the ones most appropriate for the usage scenario the binding addresses. It is not possible to add elements or attributes to a predefined binding. To do so, you should implement a custom binding.  
  
> [!NOTE]
>  The WCF-CustomIsolated adapter supports only the predefined bindings that Microsoft Internet Information Services (IIS) can host: **wsHttpBinding**, **basicHttpBinding**, **wsFederationHttpBinding**, and **wsDualHttpBinding**.  
  
> [!NOTE]
>  The WCF-CustomIsolated adapter does not support the predefined bindings for the metadata exchange protocol such as **mexHttpBinding** and **mexHttpsBinding**.  
  
## Custom Binding  
 Custom bindings provide full control over the WCF messaging stack. An individual binding defines the message stack by specifying the binding extension elements for the stack elements in the order they appear on the stack. Each binding extension element defines and configures one element of the stack. There must be one and only one `transport` binding extension element in each custom binding. Without this element, the messaging stack is incomplete.  
  
> [!NOTE]
>  The WCF-CustomIsolated adapter supports only the transport binding extension elements that the IIS can host: **httpTransport** and **httpsTransport**.  
  
 The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message. The recommended order of stack elements is the following:  
  
1.  Transactions (optional)  
  
2.  Reliable Messaging (optional)  
  
3.  Security (optional)  
  
4.  Transport  
  
5.  Encoder (optional)  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Binding Type**|Specify the binding for this receive location. Bindings are objects used to specify the communication details required to connect to the endpoint of a WCF service. Each endpoint in a WCF service requires a binding to be well-specified. Valid values include the following:<br /><br /> -   **basicHttpBinding**<br />-   **basicHttpContextBinding**<br />-   **customBinding**<br />-   **mexHttpBinding**<br />-   **mexHttpsBinding**<br />-   **mexNamedPipeBinding**<br />-   **mexTcpBinding**<br />-   **netMsmqBinding**<br />-   **netNamedPipeBinding**<br />-   **netPeerTcpBinding**<br />-   **netTcpBinding**<br />-   **netTcpContextBinding**<br />-   **webHttpBinding**<br />-   **ws2007FederationHttpBinding**<br />-   **ws2007HttpBinding**<br />-   **wsDualHttpBinding**<br />-   **wsFederationHttpBinding**<br />-   **wsHttpBinding**<br /><br /> The default is an empty string.|  
|**Binding**|Display the predefined binding elements if you select a predefined binding in the **Binding Type** property. When the **Binding Type** property is set to **customBinding**, you can edit binding extension elements through the **Select Binding Element Extension** dialog box. For more information about the available binding extension elements and the order in which they appear, see the preceding section, "Custom Bindings." **Note:**  You cannot edit collection type properties such as **ClaimTypeRequirements**. You must import a configuration file on the **Import/Export** tab to configure these properties. For more information about how to specify **ClaimTypeRequirements** in a configuration file, see the WCF product documentation. <br /><br /> The default is an empty string.|  
|**Select Binding Element Extension**|Select a binding extension element to add to the custom binding. To open the **Select Binding Element Extension** dialog box, right-click **CustomBindingElement** in the **Binding** tree view, and then click **Add extension**. **Note:**  Binding extension elements already added to the custom binding are not shown in the **Select Binding Element Extension** dialog box.|  
|**Reset all**|Restore the defaults for the **Binding** tree view and the **Configuration** list view when the **Binding Type** property is set to **customBinding**. To run this command, right-click **CustomBindingElement** in the **Binding** tree view, and then click **Reset all**.|  
|**Remove extension**|Remove the binding extension selected in the **Binding** tree view when the **Binding Type** property is set to **customBinding**. To run this command, right-click a binding element in the **Binding** tree view, and then click **Remove extension**.|  
|**Move extension up**|Move up the order of the binding extension element selected in the **Binding** tree view when the **Binding Type** property is set to **customBinding**. To run this command, right-click a binding element in the **Binding** tree view, and then click **Move extension up**.|  
|**Move extension down**|Move down the order of the binding extension element selected in the **Binding** tree view when the **Binding Type** property is set to **customBinding**. To run this command, right-click a binding element in the **Binding** tree view, and then click **Move extension down**.|  
|**Configuration**|Display the attributes and their values for the binding element selected in the **Binding** tree view. You can also modify the attribute values using this list view.|  
|**Restore Defaults**|Restore the defaults for the **Binding** tree view and the **Configuration** list view.|  
  
## See Also  
 [The \<binding> element](http://go.microsoft.com/fwlink/?LinkID=75753)   
 [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)   
 [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)