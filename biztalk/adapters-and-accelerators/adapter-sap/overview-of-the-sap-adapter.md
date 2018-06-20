---
title: "Overview of the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, overview"
ms.assetid: 2d078b13-d41f-476f-bfb4-82be4d35a769
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the SAP adapter
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes the SAP system as a WCF service. Adapter clients can perform operations on the SAP system by exchanging SOAP messages with the adapter. The adapter consumes the WCF message and makes appropriate calls to the SAP system to perform the operation. The adapter returns the response from the SAP system back to the client in the form of SOAP messages.  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces metadata of SAP artifacts (RFC, BAPI, IDOC) that describes the structure of a SOAP message in the form of WSDL. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution. For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the Unicode RFC library, librfc32u.dll, to communicate with the SAP system, in addition to using other supporting DLLs. For a complete list of SAP DLLs that the adapter requires, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide. The installation guide is typically installed at \<installation drive:\>\Program Files\\[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents. You can use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to communicate with the SAP system in the following ways:  
  
- By developing BizTalk applications. See [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md) for more information.  
  
- By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model. See [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).
  
- By using the WCF channel model. See [Develop SAP applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).
  
## In This Section  
  
-   [How Does the Adapter Connect to an SAP System?](https://msdn.microsoft.com/library/cc185540.aspx)  
  
-   [How Does the Adapter Surface SAP Metadata?](https://msdn.microsoft.com/library/dd788039.aspx)  
  
-   [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/dd788159.aspx)  
  
-   [Other Features Supported by the Adapter](https://msdn.microsoft.com/library/dd788022.aspx)  
  
## See Also  
 [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)