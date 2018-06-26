---
title: "Two-Way Messaging Scenarios for the Dynamic Resolution Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e89792f1-c725-46c4-946c-23211e2f892a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Two-Way Messaging Scenarios for the Dynamic Resolution Sample
This topic shows how you can run the two-way messaging scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Dynamic Resolution sample.  

 **To run the two-way messaging scenarios for the Dynamic Resolution sample**  

1. Before you run this sample for the first time, make sure that the receive location URL points to the appropriate Web service. Specify the Web service URL /ESB.NorthAmericanServices/CustomerOrder.asmx for the DynamicResolutionReqResp_SOAP receive location. Also, make sure that the dynamic send port named DynamicResolutionSolicitResp exists.  

   > [!NOTE]
   >  The Dynamic Resolution sample uses dynamic resolution to send messages to, and receive responses from, the Canadian Web service (http://localhost/ESB.CanadianServices/SubmitPOService.asmx). This is why a static send port is not defined for this sample. The dynamic resolution component retrieves the outbound URL from the Resolution and Adapter Provider Framework called by the ESBReceiveXml pipeline, which is configured within the DynamicResolutionReqResp_SOAP receive location. In some of the two-way messaging examples, the ESBMapSend pipeline resolves and executes Microsoft BizTalk maps.  

2. If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.  

3. Decide which example you want to execute. All two-way messaging scenarios use the ESB.NorthAmericanServices Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx to publish the request message to BizTalk, which uses the receive location named DynamicResolutionReqResp_SOAP. There are 10 two-way messaging examples, each represented by a unique binding file. The following tables list these examples, with their associated binding files and descriptions.  

   |SOAP Inbound to SOAP Outbound (submitOrder Action) Using the BRE Resolver|  
   |---------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Bindings.xml to set the receive location and send port properties.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |SOAP Inbound to SOAP Outbound (submitOrder Action) Using the BRE Resolver for Endpoint and Transformation Resolution|  
   |----------------------------------------------------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Routing_AND_ Transform_Bindings.xml to set the receive location and send port properties.|  
   |Uses the ESB Dispatcher component on the outbound send port pipeline and the outbound receive location pipeline to dynamically resolve and execute the map.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |SOAP Inbound to SOAP Outbound (submitOrder Action) Using the STATIC Resolver|  
   |------------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_STATIC_Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |SOAP Inbound to SOAP Outbound (submitOrder Action) Using the UDDI Resolver Against the Microsoft UDDI Server|  
   |--------------------------------------------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_MSFTREGISTRY_ Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   > [!NOTE]
   >  For the preceding example, you must change the service key in the binding file to one that exists on the target UDDI server.  

   |SOAP Inbound to SOAP Outbound (submitOrder Action) Using the UDDI Resolver Against the SOA Software UDDI Server|  
   |-----------------------------------------------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_SOAREGISTRY_ Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |                                                            SOAP Inbound to SOAP Outbound (submitOrder Action) Using the XPATH Resolver                                                            |
   |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                 Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_XPATH_Bindings.xml to set the receive location and send port properties.                  |
   |                                                                           Sets the maps statically at the receive port.                                                                           |
   |                                                             Uses the ESB Dispatcher at the receive location for endpoint resolution.                                                              |
   | The message contains the endpoint configuration ID=<http://localhost/ESB.CanadianServices/SubmitPOService.asmx> and customerName=<http://globalbank.esb.dynamicresolution.com/canadianservices/>. |

   |SOAP Inbound to SOAP Outbound (submitPurchase Action) Using the BRE Resolver Endpoint and Transformation Resolution|  
   |---------------------------------------------------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_BRE_Routing_ AND_Transform_Bindings.xml to set the receive location and send port properties.|  
   |Uses the ESB Dispatcher component on the outbound send port pipeline and the outbound receive location pipeline to dynamically resolve and execute the map.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  
   |The BRE Resolver changes the **Action** from **submitOrder** to **submitPurchase**.|  

   |                                              SOAP Inbound to SOAP Outbound (submitPurchase Action) Using the STATIC Resolver                                               |
   |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_STATIC_ Bindings.xml to set the receive location and send port properties. |
   |                                                               Sets the maps statically at the receive port.                                                                |
   |                                                  Uses the ESB Dispatcher at the receive location for endpoint resolution.                                                  |
   |                                           The STATIC Resolver changes the **Action** from **submitOrder** to **submitPurchase**.                                           |


4. Import the binding file for the messaging example you want to execute into the GlobalBank.ESB application.  

5. Call the NorthAmerican Web service using Microsoft InfoPath, the .NET Web Service Studio, or any other appropriate mechanism. Make sure that you include all parameters required by the operation.  

6. Look for the returned message response. If you specified the **submitOrder** action, the text "Submit Order" will precede the value of the **ID** field in the returned message. If you specified the **submitPurchase** action, the text "Submit Purchase" will precede the value of the **ID** field in the returned message.  

   To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).