---
title: "One-Way Messaging Scenarios for the Dynamic Resolution Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38237840-e957-4298-84c9-700ec72f2bc5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# One-Way Messaging Scenarios for the Dynamic Resolution Sample
This topic shows how you can run the one-way messaging scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Dynamic Resolution sample.  

 **To run the one-way messaging scenarios for the Dynamic Resolution sample**  

1. Before you run this sample for the first time, make sure that the receive location URL points to the appropriate directory. Specify the source subfolder \Source\Samples\DynamicResolution\Test\Filedrop\In for the DynamicResolution_FILE receive location. Additionally, make sure that the dynamic send port named DynamicResolutionOneWay exists.  

   > [!NOTE]
   >  The Dynamic Resolution sample uses the dynamic resolution mechanism to send messages to the output folder, FTP site, or MQSeries queue. This is why a static send port is not defined for this sample. The Dynamic Resolution component retrieves the output URL from the Resolution and Adapter Provider Framework when called by the ESBReceiveXml pipeline, which is configured within the DynamicResolution_FILE receive location.  

2. If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.  

3. Decide which example you want to execute. All one-way messaging examples (except the one that uses the XPATH Resolver) use the file NAOrderDoc.xml located in the \Source\Samples\DynamicResolution\Test\Data folder as input to the receive location named DynamicResolution_FILE. There are seven one-way messaging examples, each represented by a unique binding file. The following tables list these examples, with their associated binding files and descriptions.  

   |File Inbound to File Outbound Using the STATIC Resolver|  
   |-------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |File Inbound to File Outbound Using the UDDI Resolver|  
   |-----------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |File Inbound to File Outbound Using UDDI Resolver via UDDI Service Key|  
   |----------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_SERVICEKEY_ Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   > [!NOTE]
   >  For the preceding example, you must change the service key in the binding file to one that exists on the target UDDI server.  

   |File Inbound to FTP Outbound Using the STATIC Resolver|  
   |------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC_Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |File Inbound to FTP Outbound Using the STATIC Resolver and ENDPOINTCONFIG Parameter|  
   |-----------------------------------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC__ ENDPOINTCONFIG_Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  
   |Passes additional name/values pairs for the adapter provider to set.|  

   |File Inbound to MQS Outbound Using the STATIC Resolver|  
   |------------------------------------------------------------|  
   |Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_MQS_STATIC_Bindings.xml to set the receive location and send port properties.|  
   |Sets the maps statically at the receive port.|  
   |Uses the ESB Dispatcher at the receive location for endpoint resolution.|  

   |                                                                             File Inbound to FILE Outbound Using the XPATH Resolver                                                                             |
   |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                        Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_XPATH_STATIC_Bindings.xml to set the receive location and send port properties.                        |
   |                                                                                 Sets the maps statically at the receive port.                                                                                  |
   |                                                                    Uses the ESB Dispatcher at the receive location for endpoint resolution.                                                                    |
   | Uses information within the message to determine the appropriate endpoint. The test files you can use with this example are NAOrderDoc_XPATH_FILE.xml, NAOrderDoc_XPATH_FTP.xml, and NAOrderDoc_XPATH_MQS.xml. |


4. Import the binding file for the messaging example you want to execute into the GlobalBank.ESB application.  

5. In Windows Explorer, open the folder \Source\Samples\DynamicResolution\Test\Data and copy the appropriate input file into the folder \Source\Samples\DynamicResolution\Test\Filedrop\In. The file you use depends on the example you decided to execute:  

   -   For the XPATH example, use one of the following files: NAOrderDoc_XPATH_FILE.xml, NAOrderDoc_XPATH_FTP.xml, or NAOrderDoc_XPATH_MQS.xml.  

   -   For all other examples, use the file NAOrderDoc.xml.  

6. Look in the appropriate location for the delivered message. The location depends on the binding file you used. The following are examples:  

   -   The File Inbound to FTP Outbound example delivers the message to the FTP virtual directory named Out that you created when you installed the sample.  

   -   The File Inbound to FILE Outbound example delivers the message to the \DynamicResolution\Test\Filedrop\Out subfolder.  

   -   The File Inbound to MQS Outbound example delivers the message to the TEST.OUT queue that you created when you installed the sample.  

   -   The File Inbound to FILE Outbound using the XPATH Resolver example delivers the message to the location specified in the message. The sample documents contain the destination location and transport type (the transport type is appended to the message file name; for example, the NAOrderDoc_XPATH_FTP.xml message contains the FTP transport type specification).  

   To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).