---
description: "Learn more about: Messages Represented as XSD Schemas"
title: "Messages Represented as XSD Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Messages Represented as XSD Schemas
A template XML instance of the XSD message type is defined at design time and then stored on disk. At run time, a .NET component picks up the XML from disk and returns it as an XmlDocument. The orchestration code can assign this XmlDocument result to the message instance declared in the orchestration.  
  
 The **Message Assignment** shape has a single line of code:  
  
```  
MsgOut = CreateMsgHelper.Helper.GetXmlDocumentTemplate();  
```  
  
 The Helper Component that creates the XmlDocument has a single static method:  
  
```  
private static XmlDocument _template = null;  
private static object _sync = new object();  
private static String LOCATION = @"C:\MyTemplateLocation\MyMsgTemplate.xml";  
  
public static XmlDocument GetXmlDocumentTemplate()  
{  
   XmlDocument doc = _template;  
   if (doc == null)  
   {  
      // Load the doc template from disk.  
      doc = new XmlDocument();  
      XmlTextReader reader = new XmlTextReader(LOCATION);  
      doc.Load(reader);  
  
      // Synchronize assignment to _template.  
      lock (_sync)  
      {  
         XmlDocument doc2 = _template;  
         if (doc2 == null)  
         {  
            _template = doc;  
         }  
         else  
         {  
            // Another thread beat us to it.  
            doc = doc2;  
         }  
      }  
   }  
  
   // Need to explicitly create a clone so that we are not  
   // referencing the same object statically held by this class.  
   doc = (XmlDocument) doc.CloneNode(true);  
   return doc;  
}  
```  
  
## See Also  
 [Messages Represented as .NET Classes](../core/messages-represented-as-net-classes.md)   
 [Messages Represented as XLANGMessage](../core/messages-represented-as-xlangmessage.md)   
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)
