---
title: "HTTPRequestResponse | Microsoft Docs"
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
ms.assetid: 81c66f61-d86c-49cf-8d24-21c67c68bc5a
caps.latest.revision: 35
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTPRequestResponse
The HTTPRequestResponse sample demonstrates how to use the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Internet Server Application Programming Interface (ISAPI) filter to allow an ASP.NET application to communicate with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.  

## What This Sample Does  
 In this sample, the ASP.NET application submits a request to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISAPI filter. The orchestration then consumes this message and returns it to the ASP.NET application using a synchronous response. You achieve the integration between the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration and the ASP.NET application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISAPI filter.  

 In this sample, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and an ASP.NET application exchange purchase order (PO) and PO acknowledgement messages using the following sequence of steps:  

1. An ASP.NET application, using an HTTP request, submits an XML PO message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

2. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives the XML PO message and constructs an XML PO acknowledgement message, and then sends that message back to the ASP.NET application in the HTTP response.  

   The ASP.NET application receives the XML PO acknowledgement response and refreshes the Web form with status information extracted from the response.  

## Where to Find This Sample  
 *\<Samples Path\>*\AdaptersUsage\HTTPRequestResponse\  

 The following table shows the files in this sample and describes their purpose.  


|                                                                                                     File(s)                                                                                                      |                                                                                             Description                                                                                             |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                   Cleanup.bat                                                                                                    |  Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.   |
|                                                                               HTTPRequestResponse.btproj, HTTPRequestResponse.sln                                                                                |                            Provides project and source files for the BizTalk project that receives the HTTP request, processes the PO message, and issues the response.                             |
|                                                                                          HTTPRequestResponseBinding.xml                                                                                          |                                                                           Provides automated setup such as port binding.                                                                            |
|                                                                                             POAck.xsd, POSchema.xsd                                                                                              |                                                            Provides schemas for the PO acknowledgement and PO .xml files, respectively.                                                             |
|                                                                                            POReceiveOrchestration.odx                                                                                            |         Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that receives the PO, processes it, and issues the PO acknowledgement.          |
|                                                                                                    Setup.bat                                                                                                     |                                                                                 Builds and initializes this sample.                                                                                 |
| In the \RequestResponse folder:<br /><br /> AssemblyInfo.cs, default.aspx, default.aspx.cs, Global.asax, Global.asax.cs, RequestResponse.csproj, RequestResponse.csproj.webinfo, RequestResponse.sln, Web.config | Contains files that constitute the ASP.NET application that serves as a driver for this sample, including project and solution files, ASPX files, Microsoft Visual C# .NET source files, and so on. |

## Building and Initializing This Sample  
 Use the following procedure to build and initialize the HTTPRequestResponse sample.  

#### To build and initialize this sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\AdaptersUsage\HTTPRequestResponse  

2. Run the file Setup.bat, which performs the following actions:  

   - Compiles and configures the ASP.NET application used to drive this sample.  

     > [!NOTE]
     >  While creating application pool in IIS Manager, set the **DefaultAppPool** .NET Framework version to **.Net Framework v4.0**.  

   - Compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration used in this sample.  

   - Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  

   - Creates and binds the necessary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ports.  

   - Starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.  

     > [!IMPORTANT]
     >  You must change the sample code that implements the Web application (Default.aspx.cs) to reflect your environment:  
     >   
     >  http://\<*server name*\>/\<*virtual dir*\>/BTSHTTPReceive.dll where `<servername>` is the name of the Web server you are posting to, and `<`*virtual dir*`>` is the virtual directory where this file resides.  

     > [!NOTE]
     >  You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.  

     > [!NOTE]
     >  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe). Use this key pair to sign the resulting assemblies. You must also manually remove the references to default.aspx.resx and Global.asax.resx from the file RequestResponse.csproj before attempting to build that project.  

     > [!NOTE]
     >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

     > [!NOTE]
     >  You must configure and enable IIS to use the HTTP receive adapter. For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  

3. The setup.bat file configures the virtual directory for this sample to run in the IIS application pool associated with the default web site.  To configure the virtual directory for this sample to run under the context of a user in the **BizTalk Isolated Host Users** and **IIS_IURS** user groups, you should configure the virtual directory to run in a new IIS application pool. Configure the virtual directory to run in a new IIS application pool by completing the following steps:  

   > [!NOTE]
   >  If you have already created a new application pool for another SDK sample then you can proceed to the last step below.  

   1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  

   2.  In the **Internet Information Services (IIS) Manager**, navigate to the **Application Pools** folder.  

   3.  Right-click the **Application Pools** folder and click **New**, **Application Pool...**  

   4.  Enter a name for the **Application Pool ID:** such as BizTalkSDKSamples, verify that the **Use default settings for new application pool** option is selected and click **OK** to create the new application pool.  

   5.  Right-click the new application pool and then click **Properties**.  

   6.  Click the **Identity** tab of the properties dialog box and change the identity under which this application pool runs to a user that is a member of the **BizTalk Isolated Host Users** user group.  This user should also be a member of the local **IIS_IURS** user group.  

   7.  Configure the virtual directory for this SDK sample to run under the new application pool. The **Application pool** setting is available on the **Virtual Directory** tab of the Virtual Directory properties dialog box. The virtual directory created for this sample is HttpRequestResponseSample.  

## Running This Sample  
 Use the following procedure to run the HTTPRequestResponse sample.  

#### To run this sample  

1.  In Internet Explorer, navigate to http://localhost/RequestResponse/.  

2.  Complete the necessary fields in the Web form, and then click **Place Order** to submit your order.  

3.  Observe the status of your order when the Web form refreshes after receiving a response.  

## Comments  
 The **BTSHTTPReceiveISAPI** extension used in this sample is configured to work on a single computer default installation. To extend this sample for additional configurations, see [HTTP Adapter](../core/http-adapter.md).  

 You can extend this sample to applications that are required to submit data to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] through a Web form, or through HTTP in general. By extending the ASP.NET application portion of this sample, you can query for more information and perform other preprocessing before submitting the data to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

## See Also  
 [HTTP Adapter Samples](../core/http-adapter-samples.md)