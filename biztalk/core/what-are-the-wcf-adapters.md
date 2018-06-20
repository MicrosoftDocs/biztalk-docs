---
title: "What Are the WCF Adapters? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18ca8535-3386-4018-8b5b-d32bdb9ebf70
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Are the WCF Adapters?
There are two Windows Communication Foundation (WCF) adapters—a receive adapter and a send adapter. You use the WCF receive adapter to receive WCF service requests. The WCF receive adapter receives a request, creates a BizTalk Message object, and promotes the associated properties to the message context. You use the WCF send adapter to call a WCF service. The WCF send adapter calls the WCF services through the typeless contracts.  

> [!NOTE]
>  The WCF adapters do not support consuming Remote Procedure Call (RPC)-style Web services because the message parts in RPC-style Web services are referring to the message types rather than the message elements where WCF adapters are using elements for the message parts. We recommend that you add the RPC-style Web services through Add Web Reference wizard for consuming the Web services in BizTalk projects.  

## Web Services Standards Support  
 WCF adapters provide the support for WS-* standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction. WS-ReliableMessaging is not supported in this release of the WCF adapters. For a list of specifications supported by WCF, see [http://go.microsoft.com/fwlink/?LinkId=88314](http://go.microsoft.com/fwlink/?LinkId=88314).  

### WS-Addressing  
 WCF adapters rely on the WS-Addressing standard support that is provided by WCF. The following features are available in WCF adapters:  

-   Configuration of the send port endpoint address obtained during the metadata exchange request.  

-   Configuration of the addressing headers for the send port endpoint address.  

-   Configuration of the addressing headers for the endpoint exposed in the BizTalk receive location.  

### WS-Security  
 WCF adapters rely on the security standards support that is provided by WCF. The following standards are supported in WCF adapters:  

-   Web Services Security: SOAP Message Security (WS-Security) 1.0 and 1.1  

-   Web Services Secure Conversation Language (WS-SecureConversation)  

-   Web Services Trust Language (WS-Trust)  

-   Web Services Security X.509 Certificate Token Profile  

-   Web Services Security Username Token Profile 1.0  

-   Web Services Security Kerberos Token Profile 1.0  

#### Service Authentication Types  
 The following WCF service authentication types are supported:  

-   None  

-   Windows  

-   Certificate  

#### Client Authentication Types  
 The following WCF client authentication types are supported:  

-   Anonymous  

-   UserName  

-   Windows  

-   Certificate  

#### Security Modes  
 The following security modes are supported:  

-   Transport  

-   Message  

-   Mixed (transport-level security and message-level authentication)  

### WS-AtomicTransaction  
 The WCF-WsHttp, WCF-NetTcp, and WCF-NetMsmq adapters support the WS-AtomicTransaction protocol. This support allows the following scenarios:  

-   Transactional submission of messages to the MessageBox database.  

-   Transactional transmission of messages from the MessageBox to a transactional destination.  

> [!NOTE]
>  The transactional scope is limited by the MessageBox. For example, a BizTalk orchestration cannot participate in a client’s transaction. Similarly, a destination endpoint cannot participate in a transaction that is initiated by a BizTalk orchestration.  

#### Transactional Submission  
 For the WCF-WsHttp and WCF-NetTcp adapters, transactional submission to BizTalk Server is enabled by selecting the **Enable transactions** check box in the receive location transport properties dialog box. For the WCF-NetMsmq adapter, the **Transactional** check box is selected by default. If the message queues from which you are pulling messages are not marked as transactional, you need to clear this check box; otherwise, you will receive an error message.  

 If the transaction functionality is enabled, messages are submitted to the MessageBox database by using clients’ transactions. If a client attempts to submit the messages outside the transactional scope, the adapter will return an exception back to the client. However, no messages will be suspended. If the transaction functionality is disabled, messages are submitted to the MessageBox without using clients’ transactions. If a client attempts to submit messages inside the transactional scope, the adapter will return an exception back to the client, and no messages will be suspended.  

#### Transactions and Receive Location Type  
 Transactional submission is available only for one-way receive locations. If a client attempts to submit messages in a transactional scope for a two-way receive location, an exception will be returned back to the client, and no messages will be suspended.  

#### Transactional Transmission  
 For the WCF-WsHttp and WCF-NetTcp adapters, transactional transmission from BizTalk Server is enabled by selecting the **Enable transactions** check box in the send port transport properties dialog box. For the WCF-NetMsmq adapter, the **Transactional** check box is selected by default. If the message queues to which you are sending messages are not marked as transactional, you need to clear this check box; otherwise, you will receive an error message.  

 If the transaction functionality is enabled, messages are transmitted and deleted from the MessageBox database under transaction. If the destination service has performed any work after receiving the message, and the message is not deleted from the MessageBox, then the transaction will be aborted and all transaction work on the service will be rolled back. If the transaction functionality is disabled, messages are transmitted and deleted from the MessageBox without using transactions.  

## Single Sign-On Support  
 You can impersonate and acquire the Enterprise Single Sign-On (SSO) ticket for using SSO with WCF adapters. For more information about how to use SSO with WCF adapters, see [Single Sign-On Support for the WCF Adapters](../core/single-sign-on-support-for-the-wcf-adapters.md).  

 The following table summarizes the scenarios that are not supported when using SSO support with the WCF receive adapters.  

|Security mode|Credential|  
|-------------------|----------------|  
|None|None|  
|Transport|None|  
|Message|None|  
|TransportWithMessageCredentials|None|  
|TransportCredentialOnly|None|  

## WCF Extensibility  
 You can extend the functionality of WCF by developing the following extensions and using them with the WCF-Custom and WCF-CustomIsolated adapters:  

-   Custom bindings  

-   Custom binding elements  

### Custom Bindings  
 Custom bindings are developed by packaging individual binding elements into a container that exposes a subset of the configuration properties for a particular usage scenario. You need to register the binding extension by installing the assembly into the global assembly cache (GAC) and then adding the extension element to the machine configuration file. To use the custom bindings, you need to set up the binding on every server in the BizTalk group. After the binding is installed, it will be visible to the WCF-Custom and WCF-CustomIsolated adapters. The WCF-Custom and WCF-CustomIsolated adapters will get the binding configuration properties by using reflection on the binding configuration elements.  

### Custom Binding Elements  
 Custom binding elements are developed by adding or modifying certain transport channel components. For example, a custom decompression component is packaged as a binding element, or a UDP transport is represented as a binding element. These binding elements can be used inside the WCF adapters. You can define a channel stack that uses the custom binding element in combination with other out-of-box or custom binding elements. You need to register the binding element extension by installing the assembly into the GAC and then adding the extension element to the machine configuration file. To use the custom bindings, you need to set up the binding on every server in the BizTalk group. To use the custom binding elements, you can select the **CustomBinding** binding type and then add, modify, or rearrange the binding elements in a desired order.  

## In This Section  

-   [WCF Receive Adapter](../core/wcf-receive-adapter.md)  

-   [WCF Send Adapter](../core/wcf-send-adapter.md)  

## See Also  
- [WCF Adapters](../core/wcf-adapters.md)   
- **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
