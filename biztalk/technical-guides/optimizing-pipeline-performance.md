---
title: "Optimizing Pipeline Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5137747-0dcf-4c96-90a7-01afb92f56a6
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing Pipeline Performance
This topic describes guidelines for optimizing performance of pipelines in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.  
  
## Best practices for optimizing performance of BizTalk Server pipelines  
  
1. Because pipeline components have a significant impact on performance (for example, a pass-through pipeline component performs up to 30 percent better than an XML assembler/disassembler pipeline component), make sure that any custom pipeline components perform optimally before implementing them in your deployment. Minimize the number of pipeline components in your custom pipelines if you want to maximize the overall performance of your BizTalk application.  
  
2. You also can improve overall performance by reducing the message persistence frequency in your pipeline component and by coding your component to minimize redundancy. Every custom assembly and in particular artifacts that could potentially disrupt performance, like custom tracking components, should be tested separately under heavy load condition to observe their behavior when the system is working at full capacity and to find any possible bottlenecks.  
  
3. If you need to read the inbound message inside a pipeline component, avoid loading the entire document into memory using an **XmlDocument** object. The amount of space required by an instance of the **XmlDocument** class to load and create an in-memory representation of a XML document is up to 10 times the actual message size. In order to read a message, you should use an **XmlTextReader** object along with an instance of the following classes:  
  
   -   **VirtualStream (Microsoft.BizTalk.Streaming.dll)** - The source code for this class is located in two locations under the Pipelines SDK as follows: SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler and SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.  
  
   -   **ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**.  
  
   -   **SeekAbleReadOnlyStream** - The source code for this class is located in two locations under the Pipelines SDK as follows: SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler and SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.  
  
4. Use the PassThruReceive and the PassThruTransmit standard pipelines whenever possible. They do not contain any pipeline component and do not perform any processing of the message. For this reason, they ensure maximum performance in receiving or sending messages. You can use a PassThruReceive pipeline on a receive location if you need to publish a binary document to the BizTalk MessageBox and a PassThruTransmit pipeline on a send port if you need to send out a binary message. You can also use the PassThruTransmit pipeline on a physical send port bound to an orchestration if the message has been formatted and is ready to be transmitted. You will need to use a different approach if you need to accomplish one of the following actions:  
  
   - Promote properties on the context of an inbound XML or Flat File message.  
  
   - Apply a map inside a receive location.  
  
   - Apply a map in an orchestration that subscribes to a message.  
  
   - Apply a map on a send port that subscribes to a message.  
  
     To accomplish one of these actions, you must probe and discover the document type inside the receive pipeline and assign the (namespace#root-name) value to the MessageType context property. This operation is typically accomplished by a disassembler component such as the Xml Disassembler component (XmlDasmComp) or the Flat File disassembler component (FFDasmComp). In this case, you need to use a standard (for instance, XmlReceive pipeline) or a custom pipeline that contains a standard or a custom disassembler component.  
  
5. Acquire resources as late as possible and release them as early as possible. For example, if you need to access data on a database, open the connection as late as possible and close it as soon as possible. Use the C# using statement to implicitly release disposable objects or the finally block of a try-catch-finally statement to explicitly dispose your objects. Instrument your source code to make your components simple to debug.  
  
6. Eliminate any components from your pipelines that are not strictly required to speed up message processing.  
  
7. Inside a receive pipeline, you should promote items to the message context only if you need them for message routing (Orchestrations, Send Ports) or demotion of message context properties (Send Ports).  
  
8. If you need to include metadata with a message, and you don't use the metadata for routing or demotion purposes, use the **IBaseMessageContext.Write** method instead of the **IBaseMessageContext.Promote** method.  
  
9. If you need to extract information from a message using an XPath expression, avoid loading the entire document into memory using an **XmlDocument** object just to use the **SelectNodes** or **SelectSingleNode** methods. Alternatively, use the techniques described in [Optimizing Memory Usage with Streaming](../technical-guides/optimizing-memory-usage-with-streaming.md).  
  
## Use streaming to minimize the memory footprint required when loading messages in pipelines  
 The following techniques describe how to minimize the memory footprint of a message when loading the message into a pipeline.  
  
### Use ReadOnlySeekableStream and VirtualStream to process a message from a pipeline component  
 It is considered a best practice to avoid loading the entire message into memory inside pipeline components. A preferable approach is to wrap the inbound stream with a custom stream implementation, and then as read requests are made, the custom stream implementation reads the underlying, wrapped stream and processes the data as it is read (in a pure streaming manner). This can be very hard to implement and may not be possible, depending on what needs to be done with the stream. In this case, use the **ReadOnlySeekableStream** and **VirtualStream** classes exposed by the Microsoft.BizTalk.Streaming.dll. An implementation of these is also provided in [Arbitrary XPath Property Handler (BizTalk Server Sample)](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) in the BizTalk SDK.**ReadOnlySeekableStream** ensures that the cursor can be repositioned to the beginning of the stream. The **VirtualStream** will use a MemoryStream internally, unless the size is over a specified threshold, in which case it will write the stream to the file system. Use of these two streams in combination (using **VirtualStream** as persistent storage for the **ReadOnlySeekableStream**) provides both “seekability” and “overflow to file system” capabilities. This accommodates the processing of large messages without loading the entire message into memory. The following code could be used in a pipeline component to implement this functionality.  
  
```  
int bufferSize = 0x280;  
int thresholdSize = 0x100000;  
Stream vStream = new VirtualStream(bufferSize, thresholdSize);  
Stream seekStream = new ReadOnlySeekableStream(inboundStream, vStream, bufferSize);  
```  
  
 This code provides an “overflow threshold” by exposing bufferSize and thresholdSize variables on each receive location or send port configuration. This overflow threshold can then be adjusted by developers or administrators for different message types and different configurations (such as 32-bit vs. 64-bit).  
  
### Using XPathReader and XPathCollection to extract a given IBaseMessage object from within a custom pipeline component.  
 If specific values need to be pulled from an XML document, instead of using the **SelectNodes** and **SelectSingleNode** methods exposed by the XmlDocument class, use an instance of the XPathReader class provided by the Microsoft.BizTalk.XPathReader.dll assembly as illustrated in the following code example.  
  
> [!NOTE]  
>  For smaller messages especially, using an XmlDocument with SelectNodes or SelectSingleNode may provide better performance than using XPathReader, but XPathReader allows you to keep a flat memory profile for your application.  
  
 This example shows how to use the XPathReader and XPathCollection to extract a given **IBaseMessage** object from within a custom pipeline component.  
  
```  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage message)  
{  
    try  
    {  
        ...  
        IBaseMessageContext messageContext = message.Context;  
        if (string.IsNullOrEmpty(xPath) && string.IsNullOrEmpty(propertyValue))  
        {  
            throw new ArgumentException(...);  
        }  
        IBaseMessagePart bodyPart = message.BodyPart;  
        Stream inboundStream = bodyPart.GetOriginalDataStream();  
        VirtualStream virtualStream = new VirtualStream(bufferSize, thresholdSize);  
        ReadOnlySeekableStream readOnlySeekableStream = new ReadOnlySeekableStream(inboundStream, virtualStream, bufferSize);  
        XmlTextReader xmlTextReader = new XmlTextReader(readOnlySeekableStream);  
        XPathCollection xPathCollection = new XPathCollection();  
        XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
        xPathCollection.Add(xPath);  
        bool ok = false;  
        while (xPathReader.ReadUntilMatch())  
        {  
            if (xPathReader.Match(0) && !ok)  
            {  
                propertyValue = xPathReader.ReadString();  
                messageContext.Promote(propertyName, propertyNamespace, propertyValue);  
                ok = true;  
            }  
        }  
        readOnlySeekableStream.Position = 0;  
        bodyPart.Data = readOnlySeekableStream;  
    }  
    catch (Exception ex)  
    {  
        if (message != null)  
        {  
            message.SetErrorInfo(ex);  
        }  
        ...  
        throw ex;  
    }  
    return message;  
}  
```  
  
## Use XMLReader and XMLWriter with XMLTranslatorStream to process a message from a pipeline component  
 Another method for implementing a custom pipeline component which uses a streaming approach is to use the .NET **XmlReader** and **XmlWriter** classes in conjunction with the **XmlTranslatorStream** class provided by BizTalk Server. For example, the **NamespaceTranslatorStream** class contained in the Microsoft.BizTalk.Pipeline.Components assembly inherits from **XmlTranslatorStream** and can be used to replace an old namespace with a new one in the XML document contained in the stream. In order to use this functionality inside a custom a pipeline component, you can wrap the original data stream of the message body part with a new instance of the **NamespaceTranslatorStream** class and return the latter. In this way the inbound message is not read or processed inside the pipeline component, but only when the stream is read by a subsequent component in the same pipeline or is finally consumed by the Message Agent before publishing the document to the BizTalk Server MessageBox.  
  
 The following example illustrates how to use this functionality.  
  
```  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage message)  
{  
   IBaseMessage outboundMessage = message;  
   try  
   {  
      if (context == null)  
      {  
         throw new ArgumentException(Resources.ContextIsNullMessage);  
      }  
      if (message == null)  
      {  
         throw new ArgumentException(Resources.InboundMessageIsNullMessage);  
      }  
  
      IBaseMessagePart bodyPart = message.BodyPart;  
      Stream stream = new NamespaceTranslatorStream(context,   
                                                    bodyPart.GetOriginalDataStream(),   
                                                    oldNamespace,   
                                                    newNamespace);  
      context.ResourceTracker.AddResource(stream);  
      bodyPart.Data = stream;  
   }  
   catch (Exception ex)  
   {  
      if (message != null)  
      {  
         message.SetErrorInfo(ex);  
      }  
  
      throw ex;  
   }  
   return outboundMessage;  
}  
```  
  
## Using ResourceTracker in Custom Pipeline Components  
 A pipeline component should manage the lifetime of the objects it creates and perform garbage collection as soon as these objects are no longer required.  If the pipeline component wants the lifetime of the objects to last until the end of pipeline execution, then you must add such objects to the resource tracker that your pipeline may fetch from the pipeline context.  
  
 The resource tracker is used for the following types of objects:  
  
- Stream objects  
  
- COM objects  
  
- IDisposable objects  
  
  The message engine ensures that all the native resources that are added to the resource tracker are released at an appropriate time, that is after the pipeline is completely executed, regardless of whether it was successful or failed. The lifetime of the Resource Tracker instance and the objects that it is tracking is managed by the pipeline context object. The pipeline context is made available to all types of pipeline components through an object that implements the IPipelineContext interface.  
  
  For example, the following code snippet is a sample that illustrates how to use ResourceTracker property in custom pipeline components. To use ResourceTracker property, the code snippet uses the following parameter `IPipelineContext.ResourceTracker.AddResource`. In this parameter:  
  
- IPipelineContext interface defines the methods used to access all document processing-specific interfaces.  
  
- ResourceTracker property references IPipelineContext and is used to keep track of objects that will be explicitly disposed at the end of pipeline processing.  
  
- ResourceTracker.AddResource method is used to keep track of COM objects, Disposable objects and Streams, and should always be used inside a custom pipeline component to explicitly close (streams), dispose (IDisposable objects) or release (COM objects) these types of resources when a message is published to the BizTalk MessageBox.  
  
```  
public IBaseMessage Execute(IPipelineContext pContext, IBaseMessage pInMsg)  
  
{  
      IBaseMessage outMessage = pContext.GetMessageFactory().CreateMessage();  
  
      IBaseMessagePart outMsgBodyPart = pContext.GetMessageFactory().CreateMessagePart();  
  
      outMsgBodyPart.Charset = Encoding.UTF8.WebName;   
  
      outMsgBodyPart.ContentType = "text/xml";  
  
//Code to load message content in the MemoryStream object//  
  
      MemoryStream messageData = new MemoryStream();  
  
   //The MemoryStream needs to be closed after the whole pipeline has executed, thus adding it into ResourceTracker//  
  
      pContext.ResourceTracker.AddResource(messageData);  
  
//Custom pipeline code to load message data into xmlPayload//  
  
      XmlDocument xmlPayLoad = new XmlDocument();  
  
      xmlPayLoad.Save(messageData);  
  
      messageData.Seek(0, SeekOrigin.Begin);  
  
//The new stream is assigned to the message part’s data//  
  
      outMsgBodyPart.Data = messageData;  
  
// Pipeline component logic here//  
  
      return outMessage;  
  
}  
```  
  
## Comparison of loading messages into pipelines using an in-memory approach and using a streaming approach  
 The following information was taken from Nic Barden’s blog, [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228). This table provides a summarized comparison of loading messages into pipelines using an in-memory approach and using a streaming approach.  
  
|Comparison of...|Streaming|In memory|  
|----------------------|---------------|---------------|  
|Memory usage per message|Low, regardless of message size|High (varies depending on message size)|  
|Common classes used to process XML data|Built in and custom derivations of:<br /><br /> XmlTranslatorStream, XmlReader and XmlWriter|XmlDocument, XPathDocument, MemoryStream and VirtualStream|  
|Documentation|Poor – many un-supported and un-documented BizTalk classes|Very good - .NET Framework classes|  
|Location of “Processing Logic” code|-   “Wire up” readers and streams via Execute method.<br />-   Actual execution occurs in the readers and streams as the data is read.|Directly from the Execute method of the pipeline component.|  
|Data|Re-created at each wrapping layer as data is read through it.|Read in, modified and written out at each component prior to next component being called.|  
  
## See Also  
 [Optimizing BizTalk Server Applications](../technical-guides/optimizing-biztalk-server-applications.md)