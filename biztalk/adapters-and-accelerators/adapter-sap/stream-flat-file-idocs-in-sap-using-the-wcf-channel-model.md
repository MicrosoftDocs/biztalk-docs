---
description: "Learn more about: Stream Flat-File IDOCs in SAP using the WCF Channel Model"
title: "Stream Flat-File IDOCs in SAP using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF channel model, streaming flat-file IDOCs"
ms.assetid: 5010e215-d8d0-47c8-93a6-20cfdeff2951
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Stream Flat-File IDOCs in SAP using the WCF Channel Model
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports node-value streaming for the SendIdoc and ReceiveIdoc operations. These operations are used to send and receive flat-file (string) IDOCs to and from the adapter. In both of these operations, the data for the entire IDOC is contained in a string under a single node (\<idocData\>). For large IDOCs, streaming the IDOC data between the adapter and your code may save significant memory resources.  
  
 For background information about how the adapter supports streaming, see [Streaming and the SAP Adapter](../../adapters-and-accelerators/adapter-sap/streaming-and-the-sap-adapter.md). You should read this topic before proceeding.  
  
 The sections in this topic describe how to implement node-value streaming for the SendIdoc and ReceiveIdoc operations when you use the WCF channel model.  
  
## Streaming Outbound Flat-File IDOCs to the Adapter  
 The adapter supports node-value streaming on the request message for the SendIdoc operation.  
  
 To support node-value streaming on SendIdoc operations in the WCF channel model, you must:  
  
1.  Implement a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the IDOC data (performing node-value streaming on the IDOC data).  
  
2.  Create the **System.ServiceModel.Message** used to invoke the operation by supplying the message body with this **BodyWriter** using an appropriate overload of the **Message.Create** method.  
  
### Implementing a BodyWriter  
 The following example shows an implementation of a **BodyWriter** that performs node-value streaming.  
  
```  
/// <summary>  
/// This class overrides the OnWriteBodyContents function to do node-value streaming  
/// </summary>  
class StreamingBodyWriter : BodyWriter, IDisposable  
{  
    XmlReader m_reader = null;  
  
    int m_chunkSize;  
    /// <summary>  
    /// Initializes the body writer  
    /// </summary>  
    /// <param name="reader">Reader for input</param>  
    /// <param name="chunkSize">The chunksize in which the data is passed to adapter</param>  
    public StreamingBodyWriter(XmlReader reader, int chunkSize)  
        : base(false)  
    {  
        m_reader = reader;  
        if (chunkSize <= 0)  
            throw new ApplicationException("ChunkSize should be a positive value");  
        m_chunkSize = chunkSize;  
    }  
  
    protected override void OnWriteBodyContents(XmlDictionaryWriter writer)  
    {  
        if (m_reader == null)  
            throw new ApplicationException("Reader cannot be null");  
  
        while (m_reader.Read())  
        {  
            switch (m_reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    writer.WriteStartElement(m_reader.LocalName, m_reader.NamespaceURI);  
                    break;  
                case XmlNodeType.Text:  
                    #region Streaming Code  
                    char[] tempBuffer = new char[m_chunkSize];  
                    int length = 0;  
                    while ((length = m_reader.ReadValueChunk(tempBuffer, 0, m_chunkSize)) > 0)  
                    {  
                        writer.WriteString(new String(tempBuffer, 0, length));  
                    }  
                    #endregion  
                    break;  
                case XmlNodeType.EndElement:  
                    writer.WriteEndElement();  
                    break;  
            }  
        }  
  
    }  
  
    #region IDisposable Members  
  
    public void Dispose()  
    {  
        if (m_reader != null)  
        {  
            m_reader.Close();  
            m_reader = null;  
        }  
    }  
  
    #endregion  
}  
```  
  
### Creating a Message by using a BodyWriter  
 The following example shows how to create a SendIdoc request message using the **BodyWriter** in the preceding example. The message data is read from a file.  
  
```  
XmlReader readerIn = XmlReader.Create ("sendidoc.xml");  
// StreamingBodyWrtier class is responsible for streaming  
StreamingBodyWriter stBW = new StreamingBodyWriter(readerIn, chunkSize);  
  
Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.SAP/2007/03/Idoc/SendIdoc",   
    stBW);  
  
```  
  
## Streaming Inbound Flat-File IDOCs from the Adapter  
 You receive a flat-file IDOCs in the inbound ReceiveIdoc operation. The adapter supports node-value streaming on the request message for the ReceiveIdoc operation.  
  
 To support node-value streaming on ReceiveIdoc operations in the WCF channel model, you must:  
  
1.  Implement a **System.Xml.XmlDictionaryWriter** that is capable of streaming the IDOC data (performing node-value streaming on the IDOC data).  
  
2.  Consume the **Message** by invoking its **WriteBodyContents** method with this **XmlDictionaryWriter**.  
  
### Implementing an XmlDictionaryWriter  
 The following example shows an implementation of an **XmlDictionaryWriter** that performs node-value streaming.  
  
```  
using System;  
using System.Xml;  
using System.Text;  
  
class FileXmlWriter : XmlDictionaryWriter  
{  
    XmlTextWriter xts;  
  
    public FileXmlWriter(string file)  
    {  
        xts = new XmlTextWriter(file, Encoding.UTF8);  
    }  
  
    public override void WriteBase64(byte[] buffer, int index, int count)  
    {  
        xts.WriteBase64(buffer, index, count);  
    }  
  
    public override void WriteCData(string text)  
    {  
        xts.WriteCData(text);  
    }  
  
    public override void WriteCharEntity(char ch)  
    {  
        xts.WriteCharEntity(ch);  
    }  
  
    public override void WriteChars(char[] buffer, int index, int count)  
    {  
        xts.WriteChars(buffer, index, count);  
    }  
  
    public override void WriteComment(string text)  
    {  
        xts.WriteComment(text);  
    }  
  
    public override void WriteDocType(string name, string pubid, string sysid, string subset)  
    {  
        xts.WriteDocType(name, pubid, sysid, subset);  
    }  
  
    public override void WriteEndAttribute()  
    {  
        xts.WriteEndAttribute();  
    }  
  
    public override void WriteEndDocument()  
    {  
        xts.WriteEndDocument();  
    }  
  
    public override void WriteEndElement()  
    {  
        xts.WriteEndElement();  
    }  
  
    public override void WriteEntityRef(string name)  
    {  
        xts.WriteEntityRef(name);  
    }  
  
    public override void WriteFullEndElement()  
    {  
        xts.WriteFullEndElement();  
    }  
  
    public override void WriteProcessingInstruction(string name, string text)  
    {  
        xts.WriteProcessingInstruction(name, text);  
    }  
  
    public override void WriteRaw(string data)  
    {  
        xts.WriteRaw(data);  
    }  
  
    public override void WriteRaw(char[] buffer, int index, int count)  
    {  
        xts.WriteRaw(buffer, index, count);  
    }  
  
    public override void WriteStartAttribute(string prefix, string localName, string ns)  
    {  
        xts.WriteStartAttribute(prefix, localName, ns);  
    }  
  
    public override void WriteStartDocument(bool standalone)  
    {  
        xts.WriteStartDocument(standalone);  
    }  
  
    public override void WriteStartDocument()  
    {  
        xts.WriteStartDocument();  
    }  
  
    public override void WriteStartElement(string prefix, string localName, string ns)  
    {  
        xts.WriteStartElement(localName);  
    }  
  
    public override void WriteString(string text)  
    {  
        xts.WriteString(text);  
    }  
  
    public override void WriteSurrogateCharEntity(char lowChar, char highChar)  
    {  
        xts.WriteSurrogateCharEntity(lowChar, highChar);  
    }  
  
    public override void WriteWhitespace(string ws)  
    {  
        xts.WriteWhitespace(ws);  
    }  
  
    public override void Close()  
    {  
        xts.Close();  
    }  
  
    public override void Flush()  
    {  
        xts.Flush();  
    }  
  
    public override string LookupPrefix(string ns)  
    {  
        return xts.LookupPrefix(ns);  
    }  
  
    public override WriteState WriteState  
    {  
        get { return xts.WriteState; }  
    }  
  
}  
```  
  
### Consuming a Message by Using an XmlDictionaryWriter  
 The following example shows how to consume a ReceiveIdoc request message using the **FileXmlWriter** implemented in the preceding example. (The **FileWriter** class was created by sub-classing **XmlDictionaryWriter**.) The example uses an **IReplyChannel** channel to receive the ReceiveIdoc operation. The details of the channel creation have been omitted. The ReceiveIdoc request message is written to a file.  
  
```  
// Receive the ReceiveIdoc request message from the adapter.  
RequestContext rc = channel.ReceiveRequest();  
Message inputMsg = rc.RequestMessage;  
  
// Stream the request message to received_idoc.xml using the custom XmlDictionaryWriter.  
FileXmlWriter fileXmlWriter = new FileXmlWriter("received_idoc.xml");  
inputMsg.WriteBodyContents(fileXmlWriter);  
fileXmlWriter.Flush();  
fileXmlWriter.Close();  
  
```  
  
## See Also  
[Develop applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
