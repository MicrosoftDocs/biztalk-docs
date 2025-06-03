---
description: "Learn more about: Using Pipeline Interfaces"
title: "Using Pipeline Interfaces"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Using Pipeline Interfaces
A pipeline component is a .NET or COM component that implements a set of predefined interfaces for interaction with the BizTalk Messaging Engine. Depending on the functionality of the component, different interfaces must be implemented. This topic discusses these interfaces and some of their methods.  
  
> [!WARNING]
>  If you are building a custom pipeline component using COM, you must configure your component to use the Multi-Threaded Apartment (MTA) model. If you do not, invocation of your component will fail with an E_NOINTERFACE error.  
  
## IPipelineContext  
 All pipeline components can use **IPipelineContext** methods to access all document processing-specific interfaces. The **IPipelineContext** interface provides the following functionalities:  
  
-   Allows components to retrieve the ambient pipeline and stage settings.  
  
-   Allows components to retrieve message and message factories. With these factories, components can create various objects required for the execution of the component.  
  
-   Allows components to retrieve the document specifications. A document specification is an XSD schema plus additional annotations.  
  
## IBaseComponent  
 All pipeline components need to implement this interface to provide basic information about the component.  
  
## IComponent  
 All pipeline components except assemblers and disassemblers implement this interface to get messages from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine for processing and to pass processed messages back to the engine.  
  
 **Execute.** Method called by the engine to pass the input message to the component and retrieve the processed message from the component.  
  
## IPropertyBag, IPersistPropertyBag  
 Pipeline components need to implement **IPersistPropertyBag** to receive its configuration information. This interface and **IPropertyBag** are the standard interfaces. For more information about these interfaces, refer to the Microsoft .NET Framework Software Development Kit (SDK) documentation.  
  
## IDisassemblerComponent  
 A disassembling component is a pipeline component that receives one message on input and produces zero or more messages on output. Disassembling components are used to split interchanges of messages into individual documents. A disassembler component must implement the methods of the **IDisassemblerComponent** interface to get messages from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing and to pass disassembled documents back to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
|Method|Description|  
|------------|-----------------|  
|**Disassemble**|Performs the disassembling of the incoming document **pInMsg**.|  
|**GetNext**|Gets the next message from the message set that resulted from disassembler execution. Returns **NULL** if there are no more messages.|  
  
 If you are writing a disassembler component that will support Recoverable Interchange Processing, you must do the following:  
  
1.  Make the input streams seekable by wrapping them in a VirtualStream().  
  
2.  In GetNext(), have logic to determine when a message is bad. If a message is bad, set BTS.MessageDestination = "SuspendQueue" and return the message in GetNext().  
  
3.  If the message is good, set BTS.SuspendMessageOnRoutingFailure = True and return the message in GetNext().  
  
## IAssemblerComponent  
 An assembling component is a pipeline component that receives several messages on input and produces one message on output. Assembling components are used to collect individual documents into the message interchange batch.  
  
> [!NOTE]
>  In this release of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assembling functionality is not used, so [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] always passes one document to the component input.  
  
 An assembler component implements the **IAssemblerComponent** methods that are called by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine at run time.  
  
|Method|Description|  
|------------|-----------------|  
|**AddDocument**|Adds the document **pInMsg** to the list of messages that will be included in the interchange.|  
|**Assemble**|Builds the interchange from the messages that were added by the previous method. Returns a pointer to the assembled message.|  
  
## IProbeMessage  
 Any pipeline component (general, assembling, or disassembling) can implement **IProbeMessage** if it requires message probing functionality. A probing component is used in the pipeline stages that have **FirstMatch** execution mode. In such stages, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] gives the message to the component, and the **Probe** method examines the beginning of the message to determine if the component recognizes the format of the message.  
  
|Method|Description|  
|------------|-----------------|  
|**Probe**|This method takes **pInMsg** message, and returns **True** if the format is recognized or **False** otherwise.|  
  
## INamedItem  
 This is a helper interface for accessing document schemas from managed and unmanaged code.  
  
## INamedItemList  
 This is a helper interface for accessing document schemas from managed and unmanaged code.  
  
## IDocumentSpec  
 Pipeline components can use methods of the **IDocumentSpec** interface to perform document-specific actions, such as moving content properties to context and back, accessing document schemas, and so on.  
  
|Method|Description|  
|------------|-----------------|  
|**DocType**|Returns the type of the current document.|  
|**DocSpecName**|Returns the specification name of the current document.|  
|**GetSchemaCollection**|Returns the list of document schemas for the current document.|  
|**GetBodyPath**|Returns the XPath to the node in the document where the body part begins.|  
|**GetDistinguishedPropertyAnnotationEnumerator**|Returns a dictionary enumerator of all distinguished field property annotations.|  
|**GetPropertyAnnotationEnumerator**|Returns an enumerator of all property annotations.|  
  
## IComponentUI  
 Pipeline components must implement this interface to be used within the Pipeline Designer environment.  
  
|Method|Description|  
|------------|-----------------|  
|**Icon**|Provides the icon that is associated with this component.|  
|**Validate**|Pipeline Designer calls this method before pipeline compilation to verify that all the configuration properties are set correctly.|  
  
 The **Icon** property returns an **IntPtr**. The following C# example shows how to return an **IntPtr**.  
  
```csharp  
static   ResourceManager resManager = new ResourceManager("ResourceManager", Assembly.GetExecutingAssembly());  
...  
[Browsable(false)]  
public IntPtr Icon  
{  
   get  
   {  
      return ((Bitmap)resManager.GetObject("MyIcon")).GetHicon();  
   }  
}  
```  
  
 For more information, see **IComponentUI Interface (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## See Also  
 [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md)   
 [CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md)
