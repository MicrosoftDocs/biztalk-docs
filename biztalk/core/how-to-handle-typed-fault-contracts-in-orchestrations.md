---
title: "How to Handle Typed Fault Contracts in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "typed fault contracts [orchestrations]"
  - "WCF services, orchestrations"
  - "orchestrations, typed fault contracts"
  - "orchestrations, WCF services"
ms.assetid: 5a1a7d22-b0ff-4d09-bebf-4995229784b0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Handle Typed Fault Contracts in Orchestrations
This topic describes how to handle typed fault contracts when consuming WCF services from within orchestrations. To handle typed fault exceptions in orchestrations, the WCF services that you are consuming must have the **FaultContractAttribute** applied to the service operations; therefore, the faults can be thrown by using **FaultException**\<T\> where T can be any valid data contract or serializable type from the WCF services.  
  
## Procedures  
  
#### To handle typed fault contracts in orchestrations  
  
1. In your Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, in Solution Explorer, right-click your project, click **Add**, and then click **Add Generated Items**.  
  
2. In the **Add Generated Items - \<**<em>Project name</em>**\>** dialog box, in the **Templates** section, select **Consume WCF Service**, and then click **Add**.  
  
3. On the **Welcome to the BizTalk WCF Service Consuming Wizard** page, click **Next**.  
  
4. On the **Metadata source** page, select **Metadata Exchange (MEX) endpoint**, and then click **Next**.  
  
5. On the **Metadata Endpoint** page, specify the URL for the running service that provides metadata for download through WS-Metadata Exchange or Http-Get—for example, http://localhost:8005. To get the metadata document from the URL, click **Get**. If the running service requires a user credential with the basic authentication scheme, click **Edit** to open the **BizTalk WCF Service Consuming Wizard** dialog box in which you can supply the user name and password to use when accessing the running service. Click **Next**.  
  
6. On the **Import WCF Service Metadata Summary** page, review your settings. You can click **Back** to make any changes. Then click **Import** to create the BizTalk artifacts and types to be used for consuming the WCF service.  
  
7. On the **Completing the BizTalk WCF Service Consuming Wizard** page, click **Finish**.  
  
8. Suppose that the WCF service that you are consuming throws the following fault exception:  
  
   ```  
   throw new FaultException<MyOperationException>(divideException);  
   ```  
  
    The fault operation on the send port expects a message of type **MyOperationException**, but the WCF response message contains the whole fault body. Therefore, you need to extract the **MyOperationException** part from the message by configuring the **Inbound BizTalk message body** option in the transport properties dialog box. For example,  
  
   -   Select **Path -- content located by body path**.  
  
   -   Set the Body path expression to the following:  
  
       ```  
       /*[local-name()='Fault']/*[local-name()='Detail']/* | /*[local-name()='DivideResponse']  
       ```  
  
   -   Select **Xml** from the **Node encoding** drop-down list.  
  
9. In the orchestration, you will need to add a scope and two exception handlers. One exception handler is for the Fault operation, similar to **MyOperationException** shown in the preceding example; the other exception handler is for catching generic **SOAPExceptions**.  
  
## See Also  
 [How to Throw Fault Exceptions from Orchestrations Published as WCF Services](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)   
 [How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)