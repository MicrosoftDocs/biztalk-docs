---
description: "Learn more about: Sending an AS2 Message over a FILE Send Port"
title: "Sending an AS2 Message over a FILE Send Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Sending an AS2 Message over a FILE Send Port
AS2 messages are normally sent over an HTTP adapter. You can, however, send AS2 messages over a FILE adapter if you create custom components. This topic describes how such a solution would work and provides sample code for the solution.  
  
 When AS2 messages are sent over HTTP, the AS2 Encoder in the send pipeline populates the `HTTP.UserHttpHeaders` context property with the HTTP (and AS2) headers required for sending the message. It takes these headers either from the existing `HTTP.UserHttpHeaders` context property, from separate context properties, or from agreement properties (in that order of precedence). The HTTP adapter in the send port will write the headers to the message, and send the message over HTTP.  
  
 If you use a FILE adapter instead of an HTTP adapter in the send port, the header values in the `HTTP.UserHttpHeaders` context property will not be written to the message. You have to create a custom pipeline component to prepend the headers in `HTTP.UserHttpHeaders` to the message. The message can then be dropped into a folder by the FILE adapter, and will be an AS2 message that includes the required HTTP headers.  
  
 You may also need to create a custom component to ensure that all the AS2 headers are included in the `HTTP.UserHttpHeaders` context property. You can create either a custom orchestration, or a custom pipeline component before the AS2Encoder, to set the context properties that the AS2 Encoder uses to build `HTTP.UserHttpHeaders`.  
  
## Writing Headers to an AS2 Message  
 To generate an AS2 message using a FILE adapter, rather than an HTTP adapter, add a custom pipeline component after the AS2 Encoder in a custom AS2 send pipeline. Include code in the custom pipeline component that writes the headers from the `HTTP.UserHttpHeaders` context property into the message. An example is the following sample code:  
  
```  
public IBaseMessage Execute(IPipelineContext pContext, IBaseMessage pInMsg)  
        {  
            IPipelineContext pipelineContext = pContext;  
            IBaseMessage baseMessage = pInMsg;  
  
            //Prepend Headers  
            MemoryStream ms = new MemoryStream();  
            string strName = "UserHttpHeaders";  
            string strValue = (string)baseMessage.Context.Read(strName,  
              "http://schemas.microsoft.com/BizTalk/2003/  
              http-properties");  
  
            //Leave an empty line between the headers and the body  
            strValue += "\r\n";  
            ms.Write(Encoding.ASCII.GetBytes(strValue), 0,   
               Encoding.ASCII.GetByteCount(strValue));  
  
            //Append Body  
            Stream sr = baseMessage.BodyPart.Data;  
  
            //Read the body of the message and append it to the memory   
              stream containing the headers  
            int size = 1024;  
            byte[] buffer = new byte[size];  
            while (0 != (size = sr.Read(buffer, 0, buffer.Length)))  
            {  
                ms.Write(buffer, 0, size);  
            }  
  
            //Set the body of the message to the new memory stream  
            baseMessage.BodyPart.Data = ms;  
  
            //Rewind the stream  
            ms.Seek(0, SeekOrigin.Begin);  
  
            return baseMessage;  
        }  
```  
  
## Promoting AS2 Header Context Properties  
 You can promote AS2 header properties into the context of a message using either a custom orchestration or a custom pipeline component.  
  
 To promote AS2 header properties using a custom pipeline component, add a custom pipeline component before the AS2 Encoder in a custom AS2 send pipeline. You can use code from the sample code shown above for writing headers from `HTTP.UserHttpHeaders` into the message, with the exception that you would replace the Read method with a Promote method, providing the name, value, and namespace of the context property to be promoted.  
  
 To promote AS2 header properties using a custom orchestration, create an orchestration with a FILE receive port, a Construct Message shape, and a FILE send port. To the Construct Message shape, add code setting the promoted properties that contain the AS2 headers. You must add a reference to `Microsoft.BizTalk.HttpTransport.dll` in the custom orchestration.  
  
 The namespaces for HTTP headers is `http://schemas.microsoft.com/BizTalk/2003/http-properties` for non-AS2 HTTP headers and `http://schemas.microsoft.com/BizTalk/2003/as2-properties` for AS2 headers.  
  
 The following sample code shows how to promote AS2 header properties in the Construct Message shape of an orchestration. This code promotes AS2 headers for an MDN.  
  
```  
Message_2=new System.Xml.XmlDocument();  
Message_2=Message_1;  
Message_2(EdiIntAS.IsAS2PayloadMessage)=false;  
Message_2(EdiIntAS.IsAS2AsynchronousMdn)=true;  
Message_2(EdiIntAS.IsAS2MdnResponseMessage)=true;  
Message_2(EdiIntAS.SendMDN)=true;  
Message_2(EdiIntAS.IsAS2MessageSigned)=false;  
Message_2(EdiIntAS.AS2To)="Party1";  
Message_2(EdiIntAS.AS2From)="Home";  
Message_2(EdiIntAS.MessageId)="123456";  
Message_2(EdiIntAS.OriginalMessageId)="2123456";  
Message_2(HTTP.UserHttpHeaders)="Message1-Id: xyz\r\nMyHeader: MyValue";  
```  
  
## See Also  
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)
