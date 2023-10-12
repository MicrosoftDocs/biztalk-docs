---
description: "Learn more about: Overview of the SAP adapter"
title: "Overview of the SAP adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Overview of the SAP adapter
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes the SAP system as a WCF service. Adapter clients can perform operations on the SAP system by exchanging SOAP messages with the adapter. The adapter consumes the WCF message and makes appropriate calls to the SAP system to perform the operation. The adapter returns the response from the SAP system back to the client in the form of SOAP messages.  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces metadata of SAP artifacts (RFC, BAPI, IDOC) that describes the structure of a SOAP message in the form of WSDL. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution. For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the Unicode RFC library, librfc32u.dll, to communicate with the SAP system, in addition to using other supporting DLLs. For a complete list of SAP DLLs that the adapter requires, see the [BizTalk Adapter Pack installation guide](../../adapters-and-accelerators/biztalk-adapter-pack.md#install-bap). You can use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to communicate with the SAP system in the following ways:  
  
- By developing BizTalk applications. See [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md) for more information.  
  
- By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model. See [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).
  
- By using the WCF channel model. See [Develop SAP applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).
  
## In This Section  
  
-   [How Does the Adapter Connect to an SAP System?](https://msdn.microsoft.com/library/cc185540.aspx)  
  
-   [How Does the Adapter Surface SAP Metadata?](./browse-search-and-get-sap-metadata.md)  
  
-   [What Operations Can be Performed Using the Adapter?](../adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
-   [Other Features Supported by the Adapter](../adapter-oracle-database/features-for-oracle-database-adapter-clients.md)  
  
## See Also  
 [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)