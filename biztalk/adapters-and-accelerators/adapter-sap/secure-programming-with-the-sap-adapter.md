---
title: "Secure programming with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, considerations when programming on the adapter"
  - "security, secure data exchange"
  - "security, setting credentials in code"
ms.assetid: bd5da271-90f1-4a64-9138-a51048a16648
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Secure programming with the SAP adapter
## How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?  
 When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you must supply a user name and password for the SAP system. You should only do this from the **Security** tab on the **Configure Adapter** dialog box. By entering the SAP credentials from the **Security** tab instead of directly into the **Uri** field, you ensure the following:  
  
- The credentials will not be displayed in the **Uri** field of the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dialog box where anyone with access to your computer screen can read them.  
  
- The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.  
  
  For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the SAP system, see [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)  
  
## What Are Best Practices for Setting Credentials in Code?  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service. By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.  
  
 Because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses. It is, however, considered good practice to do so.  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] encourages the use of the **ClientCredentials** class through the **AcceptCredentialsInUri** binding property. This property specifies whether the adapter will accept the user name and password for the SAP system in the connection URI. **AcceptCredentialsInUri** defaults to **false**, which means that the adapter will throw an exception if the connection URI contains credentials. You can set **AcceptCredentialsInUri** to **true** to supply credentials in the connection URI. In fact, you must do this in certain cases; for example, when you specify a connection URI for a service host endpoint or for an **IReplyChannel** in inbound scenarios.  
  
 The following example shows how to use the **ClientCredentials** class to set credentials for the SAP system on a WCF client.  
  
```  
SAPBinding binding = new SAPBinding();  
  
// Set endpoint address  
EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
// Create client and set credentials  
RfcClient rfcClient = new RfcClient(binding, endpointAddress);  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
```  
  
## How Can I Provide for More Secure Data Exchange Across Process Boundaries?  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is hosted in-process with the application or service that consumes it. Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment. [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] provides many options for helping to secure messages sent between clients and services. For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx). For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).  
  
## See Also  
[Best practices to secure the SAP adapter](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   