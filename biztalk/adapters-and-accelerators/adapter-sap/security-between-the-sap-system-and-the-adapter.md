---
title: "Security between the SAP system and the adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Secure Network Communications"
  - "SNC"
  - "security, user name password credentials"
  - "security, for inbound scenarios"
  - "security considerations, between SAP system and adapter"
  - "user name password credentials"
ms.assetid: fa21df0b-a364-4a52-8c38-49c5ee6267cc
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security between the SAP system and the adapter
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports either SAP Secure Network Communications (SNC) or user name password credentials to help secure communication between it and the SAP server. User name password credentials only provide authorization for the connection to the SAP system; they do not provide any security on the data exchanged over the connection. You cannot use both SNC and user name password credentials simultaneously.  
  
## SAP Secure Network Communications  
 Secure Network Communications (SNC) is a software layer in the SAP system architecture that can help provide application-level security on data exchanged between the SAP client and a SAP application server.  
  
 SNC provides the following advantages:  
  
- SNC targets application-level, end-to-end security. SNC helps secure all communications between two SNC-protected components (for example, between the SAPgui and an SAP System application server).  
  
- You can implement additional security features that the SAP System does not directly provide (for example, Single Sign-On or the use of smart cards for authentication).  
  
- You can customize your SNC implementation. You can use the security product of your choice and choose the algorithms you want to use.  
  
- You can change the security product at any time without affecting SAP System business applications.  
  
  To use SNC, you must configure both the SAP server and the client running the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- Configure Secure Network Communications (SNC) on the SAP server. Refer to the SAP documentation for guidance.  
  
- On the computer having the SAP client DLLs and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installed, you must also have the SNC related DLLs. For more information about these DLLs, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] [software prerequisites](../../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md).  
  
- To configure the adapter to use SNC, you must set the UseSnc parameter in the SAP connection URI. For more information about the SAP connection URI, see [Configure the connection URI for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md). Also, you must set the **SncLibrary** and the **SncPartnerName** binding properties. For more information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## User Name Password Credentials  
 You can supply user name password credentials to the adapter in the connection URI. The adapter uses these credentials to authenticate the user on the SAP system when it opens the connection. These credentials provide a level of authorization for the connection to the SAP system; however, they do not provide message-level or transport-level authentication (or authorization) for data traveling across the network.  
  
 For this reason, you must provide a security mechanism to help ensure appropriate levels of authorization, authentication, data privacy, and data integrity for data exchanges between the adapter and the SAP system.  
  
> [!IMPORTANT]
>  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces the **AcceptCredentialsInUri** binding property. This property determines whether SAP system credentials are permitted in the connection URI. By default, **AcceptCredentialsInUri** is false and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] throws an exception if credentials are included in the URI. For more information, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 One possible mechanism for helping to provide more security across the network is Internet Protocol Security (IPsec). IPsec is a framework of open standards for protecting communications over Internet Protocol (IP) networks.  
  
 The user name and password are specified as clear text in the connection URI. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] provides a number of methods through which you can more securely supply these credentials.  
  
-   For information about how to more securely provide SAP system credentials in BizTalk solutions, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).  
  
-   For information about how to more securely provide SAP system credentials in programming solutions, see [Secure programming with the SAP adapter](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md).  
  
## Security Concerns for Inbound Scenarios  
 Any listener that has access to a SAP program ID can potentially receive all SAP artifacts (RFCs, IDOCs, and tRFCs) sent to that program ID. If more than one listener is registered to the program ID, SAP will randomly assign artifacts that arrive at that program ID to one of the listeners. You should, therefore, guarantee that only listeners that you want to receive messages by using a specific program ID have access to that program ID. Furthermore, because SAP randomly sends artifacts to listeners attached to a program ID, it is a best practice to dedicate program IDs to a single listener.  
  
## See Also  
[Best practices to secure the SAP adapter](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)