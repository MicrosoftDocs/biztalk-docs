---
description: "Learn more about: Overview of BizTalk Adapter for Siebel eBusiness Applications"
title: "Overview of BizTalk Adapter for Siebel eBusiness Applications"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Overview of BizTalk Adapter for Siebel eBusiness Applications
The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes the Siebel system as a WCF service. Adapter clients can perform operations on the Siebel system by exchanging SOAP messages with the adapter. The adapter consumes the WCF message and makes appropriate calls to the Siebel system to perform the operation. The adapter returns the response from the Siebel system back to the client in the form of SOAP messages.  
  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces metadata of Siebel artifacts (business components, business services) that describes the structure of a SOAP message in the form of WSDL. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution.  
  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses the Siebel COM Data Control to access the Siebel system. The Siebel COM Data Control comes bundled with the Siebel Web client. Hence, make sure you have the Siebel Web client installed on the same computer as the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. You can use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to communicate with the Siebel system in the following ways:  
  
-   By developing BizTalk applications. See [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md).
  
-   By using the WCF service model. See [Develop Siebel Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).  
  
-   By using the WCF channel model. See Develop Oracle Database Applications by Using the WCF Channel Model[enter link description here](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
## In This Section  
  
-   [How Does the Adapter Connect to a Siebel System?](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)  
  
-   [How Does the Adapter Surface Siebel Metadata?](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)  
  
-   [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [Other Features Supported by the Adapter](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx) 
  
## See Also  
 [Understand BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)
