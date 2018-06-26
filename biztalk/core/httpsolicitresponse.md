---
title: "HTTPSolicitResponse | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP adapters, examples"
  - "examples, HTTP adapters"
ms.assetid: b149544e-3279-4ac9-b31f-fff3e41ec8e7
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTPSolicitResponse
The HTTPSolicitResponse sample demonstrates how to create a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that leverages an ASP.NET application to help process orchestration data. In this sample, the orchestration makes use of a request/response port to send a message to the ASP.NET application and to retrieve the response. You achieve the integration between the BizTalk Server orchestration and the ASP.NET application by using the HTTP adapter. For more information, see [HTTP Adapter](../core/http-adapter.md).  
  
## What This Sample Does  
 This sample consists of a BizTalk Server orchestration that receives a request containing two numbers to be multiplied, and satisfies that request using the following sequence of steps:  
  
1.  The BizTalk Server orchestration retrieves an .xml input file from a specific folder.  
  
2.  The orchestration uses an HTTP request to forward the XML from the file to a multiplier ASP.NET application.  
  
3.  The multiplier ASP.NET application responds to the HTTP request by performing the multiplication and returning the result as XML in the HTTP response.  
  
4.  The orchestration receives the result as XML in an HTTP response, and writes that result to an .xml file in a specific folder.  
  
## Where to Find This Sample  
 \<*Samples Path*\>\AdaptersUsage\HTTPSolicitResponse  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Cleanup.bat|Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|HttpSolicitResponse.btproj, HttpSolicitResponse.sln|Provides project and source files for the BizTalk project that contains the orchestration that uses the multiplier ASP.NET application, the associated schemas, and so on.|  
|HttpSolicitResponseBinding.xml|Provides for automated setup such as port binding.|  
|MultiplyRequest.xsd, MultiplyResponse.xsd|Provides schemas for the multiplication request and response XML messages, respectively.|  
|MultiplyTwoIntegers.odx|Provides a BizTalk Server orchestration that receives an .xml file requesting a multiplication operation, forwards the request to the multiplier ASP.NET application, and writes its response to a file.|  
|request_in.xml|Sample input file.|  
|Setup.bat|Builds and initializes this sample.|  
|In the \Multiplier folder:<br /><br /> Multiplier.aspx, Multiplier.aspx.cs, Multiplier.sln|Contains files that constitute the ASP.NET application that implements the multiplier service, including project and solution files, ASPX files, Microsoft Visual C# .NET source files, and so on.|  
  
## Building and Initializing the Sample  
 Use the following procedure to build and initialize the HTTPSolicitResponse sample.  
  
> [!NOTE]
>  This sample doesn't work if the name of the receive location contains any uppercase characters.  
  
#### To build and initialize the sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\AdaptersUsage\HTTPSolicitResponse  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Creates the input and output folders for this sample:  
  
      \<*Samples Path*\>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput  
  
      \<*Samples Path*\>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput  
  
   - Compiles and configures the multiplier ASP.NET application used by this sample.  
  
     > [!NOTE]
     >  While creating application pool in IIS Manager, set the **DefaultAppPool** .NET Framework version to **.Net Framework v4.0**.  
  
   - Compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration used in this sample.  
  
   - Creates and binds the necessary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and ports.  
  
     > [!NOTE]
     >  This sample displays the following warnings when creating and binding the ports:  
  
     > [!NOTE]
     >  `Warning: Receive handler not specified for receive location "HttpSolicitResponseReceiveLocation"; updating with first receive handler with matching transport type.`  
  
     > [!NOTE]
     >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.HttpSolicitResponse.MultiplyTwoIntegers"; updating with first available host.`  
  
   - Enables the receive location, and starts the send port.  
  
     > [!NOTE]
     >  The orchestration in this sample uses a two-way port for the HTTP interaction with the ASP.NET application.  
  
     > [!NOTE]
     >  You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.  
  
     > [!NOTE]
     >  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe). Use this key pair to sign the resulting assemblies.  
  
     > [!NOTE]
     >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running the Sample  
 Use the following procedure to run the HTTPSolicitResponse sample.  
  
#### To run the sample  
  
1.  Paste a copy of the file request_in.xml into the folder HttpSolicitResponseInput.  
  
2.  Observe the .xml file created in the folder HttpSolicitResponseOutput. The name of this .xml file is based on the message ID GUID. This file contains the XML-formatted result of the multiplication operation.  
  
    > [!NOTE]
    >  You can change the operand values in the input file to perform a different multiplication operation.  
  
## Comments  
 You can adapt this sample to communicate with a different external system that exposes an HTTP interface.  
  
 The files MultiplyRequest.xsd and MultiplyResponse.xsd are the XML schemas that define the format of the input and output data for the multiplier ASP.NET application. The orchestration uses these files to define the request and response message types.  
  
## See Also  
 [HTTP Adapter Samples](../core/http-adapter-samples.md)