---
title: "Arbitrary XPath Property Handler (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], examples"
  - "examples, pipeline components [custom]"
ms.assetid: 4eb26c38-5ece-42b0-a28e-73214df1dc41
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Arbitrary XPath Property Handler (BizTalk Server Sample)
The Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample) demonstrates how to write a custom pipeline component to promote specific properties on an XML document that is submitted to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You can use functionality contained in the sample to create custom regular, assembler, and disassembler components to evaluate XPath expressions.  
  
## What This Sample Does  
 The sample includes a purchase order (PO) XML document to process, DocInstance.xml. The sample uses the following steps to process DocInstance.xml:  
  
1. DocInstance.xml is retrieved by a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive port and processed by a custom pipeline component called Arbitrary XPath Property Handler.  
  
2. The arbitrary XPath property handler component promotes all \<Price\> and \<Quantity\> elements with an arbitrary XPath expression as defined in the PO schema. The XPath expression also contains the position construct for use with ambiguous child elements of the PO document root element.  
  
3. The arbitrary XPath property handler component determines the message type and promotes it into the message context.  
  
4. The component then sends the XML document with the promoted elements to an orchestration for further processing.  
  
5. The orchestration accesses the promoted elements in the PO document and calculates the total number of items in the PO.  
  
6. The orchestration creates a new PO document that contains the information from the original PO as well as the updated total.  
  
7. The new PO document is written to a file in the \Output directory.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\Pipelines\ArbitraryXPathPropertyHandler  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|ArbitraryXPathPropertyHandler.sln|Custom pipeline component solution file.|  
|ArbitraryXPathPropertyHandler.resX|Resource file.|  
|ArbitraryXPathPropertyHandlerComp.cs|Main component implementation.|  
|AssemblyInfo.cs|Assembly information.|  
|Cleanup.bat|Sample cleanup file.|  
|PromotingMap.cs|Property promotion as native CLR types map implementation.|  
|PropertyAttributes.cs|Custom attributes, property descriptor, and ICustomTypePropertyDescriptor implementation.|  
|SchemaMap.cs|Schema mapping from message type to IDocumentSpec to resolve schema ambiguity.|  
|Setup.bat|Build and setup sample pipeline component.|  
|VirtualStream.cs|Virtual stream implementation.|  
|SeekableReadOnlyStream.cs|Seekable read-only stream implementation.|  
|ArbitraryXPathSample.sln|Sample orchestration solution file.|  
|CalculateTotalAmount.odx|Sample orchestration.|  
|PODocument.xsd|Purchase order schema.|  
|DocInstance.xml|Sample purchase order instance.|  
  
## Building and Initializing This Sample  
 This sample is designed to run in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] running on the same machine. If your environment does not match this configuration, you must modify the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample) to point to the correct SQL Server computer.  
  
> [!IMPORTANT]
>  Setup.bat assumes your Microsoft Windows installation directory is C:\Windows. If your Windows installation is in another directory, you must modify the ArbitraryXPathPropertyHandler.csproj file to reflect the location of the Microsoft.BizTalk.Component.Utilities assembly in the global assembly cache. In the Reference element, change \<SYSTEMROOT\> to the location where Windows is installed (for example, C:\WINNT\\).  
  
```  
<Reference  
  Name = "Microsoft.BizTalk.Component.Utilities"  
  AssemblyName = "Microsoft.BizTalk.Component.Utilities"  
  HintPath = "<SYSTEMROOT>\assembly\GAC\Microsoft.BizTalk.Component.Utilities\3.0.1.0__31bf3856ad364e35\Microsoft.BizTalk.Component.Utilities.dll"  
/>  
```  
  
 Use the following procedure to build and initialize the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample).  
  
#### To build and initialize this sample  
  
1. In a command window, change directories (**cd**) to the following folder:  
  
    *\<Samples Path\>*\Pipelines\ArbitraryXPathPropertyHandler  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Builds the Arbitrary XPath Property Handler pipeline component.  
  
   - Copies built pipeline component to the *\<Installation Path\>*\Pipeline Components directory.  
  
   - Creates the send and receive ports.  
  
   - Creates the input and output directories used in the sample.  
  
   - Installs the sample [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration ArbitraryXPathSample.  
  
   - Binds the ports to the sample orchestration.  
  
   - Starts the orchestration.  
  
   > [!NOTE]
   >  No errors should be reported during the build and initialization. If any errors occur, make sure that you have all necessary software installed and that Microsoft build tools are available on the path.  
   > 
   > [!NOTE]
   >  To undo changes made by Setup.bat, you must first stop and restart the host instance from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. Next, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running This Sample  
 Use the following procedure to run the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample).  
  
#### To run this sample  
  
1.  Copy the purchase order (PO) file DocInstance.xml to the \Input directory. The PO file is picked up by a receive port, which sends the XML data to the Arbitrary XPath Property Handler pipeline component.  
  
2.  View the contents in the \Output directory. Notice that a new file is created that contains all the information from the DocInstance.xml file that you copied to the \Input directory. The difference in the file is that now the \<TotalAmount\> element has been populated with the total amount for the PO.  
  
## Comments  
 Canonical XPath expressions are simple expressions such as "/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/\*[local-name()='element-name']/@\*[local-name='attribute-name']".  
  
 An arbitrary XPath expression can be as complex as "//element-name//*[local-name()='element-name' and position()=2]". If fact, you will receive a run-time error stating that non-canonical XPath expressions are not supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] if your schema has a non-canonical XPath used in the XPath body or an XPath property. A solution to support arbitrary XPath expressions is to create custom disassembler and assembler components that support an arbitrary XPath body as well as arbitrary XPath property expressions.  
  
 This sample uses the following sequence of steps in the custom pipeline component when **IComponent.Execute** is implemented:  
  
1.  Creates a virtual seekable stream over the input message body part stream. (Because the input message can be large and the stream can be non-seekable, it should have a small memory footprint and be able to change stream positions.)  
  
2.  Creates a new outgoing message and a new body part for it, assigns a virtual stream to the new body part, clones body part properties, and clones message context.  
  
3.  Gets a schema for the input message or based on schemas specified during design time.  
  
4.  Loads the stream into an instance of **System.Xml.XmlDocument**.  
  
5.  Walks through promoted properties and distinguished fields and promotes or writes them to the message context of the outgoing message.  
  
6.  Returns the outgoing message.  
  
7.  Writes the outgoing message to a file.  
  
## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)