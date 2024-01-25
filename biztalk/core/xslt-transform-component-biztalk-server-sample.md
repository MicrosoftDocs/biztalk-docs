---
description: "Learn more about: XSLT Transform Component (BizTalk Server Sample)"
title: "XSLT Transform Component (BizTalk Server Sample)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# XSLT Transform Component (BizTalk Server Sample)
The XSLT Transform Component sample demonstrates how to write a custom pipeline component to transform an XML message using XSLT.  
  
## What This Sample Does  
 The sample accomplishes the transformation with the following steps:  
  
1.  An XML document is retrieved from a folder.  
  
2.  The pipeline transforms the XML document into the HTML body of an e-mail message using Transform.xsl.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\Pipelines\XslTransformComponent\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|C# assembly file.|  
|Cleanup.bat|Sample cleanup file.|  
|Confirmation.xsd|Sample schema file.|  
|DocInstance.xml|Sample .xml file to transform.|  
|SendHtmlMessage.btproj|BizTalk project.|  
|Setup.bat|Configuration batch file.|  
|Xml2HtmlSendPipeline.btp|BizTalk Server pipeline file.|  
|XslTransform.csproj|C# project.|  
|XslTransformComponent.sln|Sample solution file.|  
|XslTransformComponentBinding.XML|XML binding file.|  
|XslTransformer.cs|C# source code.|  
|Transform.xsl|XSLT file used to transform DocInstance.xml.|  
  
## Building and Initializing This Sample  
 Use the following procedure to build and initialize the XSLT Transform Component sample.  
  
#### To build and initialize this sample  
  
1.  In a command window, change directory (**cd)** to the following folder:  
  
     *\<Samples Path\>*\Pipelines\XslTransformComponent  
  
2.  Run the file Setup.bat, which performs the following actions:  
  
    -   Creates the input (\In) and output (\Out) folders used in the sample.  
  
    -   Generates a new key file.  
  
    -   Builds and deploys the XSLT Transform Component pipeline.  
  
    -   Copies the built pipeline component to the \<Installation Path\>\Pipeline Components folder.  
  
    -   Creates the send and receive ports.  
  
    > [!NOTE]
    >  You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.  
  
    > [!NOTE]
    >  To undo changes made by Setup.bat, you must first stop and restart the host instance from the BizTalk Server Administration MMC console. Next, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running This Sample  
 Use the following procedure to run the XSLT Transform Component sample.  
  
#### To run this sample  
  
1.  Copy DocInstance.xml to the \In folder.  
  
2.  Examine the results in the \Out folder (the output filename is guid.htm).  
  
## Configuring This Sample Using SMTP  
 Use the following procedure to configure the XSLT Transform Component sample to work with an SMTP server.  
  
#### To configure this sample using SMTP  
  
1.  Reconfigure the XSLT Transform Component send port to use an SMTP transport type.  
  
2.  Configure the SMTP setting by changing the address (URI) parameters to match your SMTP configuration.  
  
## Running This Sample with Output to an SMTP Port  
 Use the following procedure to run the XSLT Transform Component sample with output to an SMTP port.  
  
#### To run this sample with output to an SMTP port  
  
1.  Copy DocInstance.xml to the \In folder.  
  
2.  Examine the results in the mail client for the recipient that SMTP is configured to send to.  
  
## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)
