---
title: "Messages Represented as XLANGMessage | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aadca870-2f93-4be3-8733-a0cd3815add7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Messages Represented as XLANGMessage
An **XLANGMessage** object represents a message instance declared with an XLANG service. This object is obtained by passing a reference to a message as a parameter in a method invocation. An **XLANGPart** object represents a message part contained in a message instance within an XLANG service. This object is obtained either by passing a part reference in a method invocation where the receiving parameter type is **XLANGPart** or by enumerating on a passed reference of **XLANGMessage**.  
  
 An orchestration message variable may be passed to a user component and received as an **XLANGMessage** object. The **XLANGMessage** object allows accessing the parts and accessing message properties.The user may "hold on" to an **XLANGMessage** and thereby extend its lifetime beyond the declared scope. Subsequently, an **XLANGMessage** may be retuned from a method and assigned to a message variable in an orchestration.  
  
## Constructing an XLANGMessage  
 When constructing an **XLANGMessage** with a stream, the stream type must either implement **IStreamFactory** or be a **MemoryStream**. The following code sample shows how to construct an **XLANGMessage**:  
  
```  
public class FileStreamFactory : IStreamFactory  
{  
    string _fname;  
  
    public FileStreamFactory(string fname)  
    {  
        _fname = fname;  
    }  
  
    public Stream CreateStream()  
    {  
        return new FileStream  
        (  
            _fname,  
            FileMode.Open,  
            FileAccess.Read,  
            FileShare.Read  
        );  
    }  
}  
  
public static void AssignStreamFactoryToPart(XLANGMessage msg)  
{  
    IStreamFactory sf = new FileStreamFactory( @”c:\data.xml” );  
    msg[0].LoadFrom( sf );  
}  
```  
  
 There may be times when you want to create a new message without transforming a source message. You can do this by using a variable of type **System.Xml.XmlDocument** and loading or otherwise constructing appropriate content. In the following example, XML is loaded from a string by using the **LoadXml** method of **XmlDocument**:  
  
```  
XmlVariable.LoadXml("<ns0:Root PONumber="047745351122111" xmlns:ns0="http://BTSHTTPSend.SimpleSchema"><MyChildRecord SubAttr1="Simple Attribute " /></ns0:Root>");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
 The following example loads XML from a file by using the **Load** method of **XmlDocument**:  
  
```  
XmlVariable.Load("C:\MyData.xml");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
> [!NOTE]
>  If you want to construct larger messages, use one of the streaming methods demonstrated in the previous section or consider using the **Transform** shape in Orchestration Designer.  
  
## Considerations When Using XLANGMessage and XLANGPart  
 When using **XLANGMessage** and **XLANGPart** in user code, consider the following:  
  
-   Do not pass a message part as an **XLANGPart** argument or return a value of type **XLANGPart**. You should pass **XLANGPart** as the type of the part. For example:  
  
    ```  
    Message String msg;  
    Class.Test(msg);  
    // or you can do the following  
    Messagetype mt  
    {  
         String part;  
    };  
    Message mt msg;  
    Class.Test(msg,part);  
  
    ```  
  
     You can also pass the message itself as an **XLANGMessage** and use the **XLANGMessage** subscript operators to access the part inside the function call. However, you should not put an **XLANGPart** in a collection whose lifetime extends past the lifetime of the function call. Instead, you should put the **XLANGMessage** in the collection. For example:  
  
    ```  
    Void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          XLANGPart xlp = xlm[0];  
          String sval = (String) xlp.RetrieveAs(typeof(string));  
         }  
         finally  
         {  
          Xlm.Dispose();  
         }  
    }  
    ```  
  
-   Do not define an orchestration parameter as **XLANGMessage** or **XLANGPart**. If you want to pass a message, then use a message type parameter to pass the message. If you want to pass a part, then pass the message instead and then use the part. If you only want the part value, then use the part type to pass the part.  
  
-   Do not return an **XLANGMessage** parameter for a method call. If you return an **XLANGMessage** parameter that is passed in, and then you cannot call the **Dispose** method on the parameter inside the method call, it intuitively violates lifetime assumptions and it also throws an exception. When passing a message through an **XLANGMessage** parameter to user code, you reference the message to a special context that does not normally have messages referenced to it. The lifetime of this context is the lifetime of the orchestration instance. This is because BizTalk Server does not know whether the user code will hold onto the message.  
  
     When an orchestration instance exits, any messages created in that instance are no longer valid, so the lifetime of such a collection should be less than or equal to that of the instance lifetime. However, if you want to release a message reference in a loop when the message was passed through an **XLANGMessage** argument that has the same lifetime as the orchestration instance, then you can call **XLANGMessage.Dispose** to free up the reference. Moreover, if inside the user code method, the **XLANGMessage** parameter is only used locally and the lifetime of the parameter is contained in that of the function call, you can also call **XLANGMessage.Dispose** to free up the reference to the root context and give the corresponding message back the normal lifetime behavior. For example:  
  
    ```  
    void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          //XLANGMessage is only used locally  
         }  
         finally  
         {  
          xlm.Dispose();  
         }  
    }  
    ```  
  
     If you place the xlm in a collection, then the class itself must have a **Dispose** method for cleanup. For example:  
  
    ```  
    Public class A  
    {  
         Hashtable h = new Hashtable();  
         Public Test(XLANGMessage xlm)  
         {  
          h[xlm] = 1;  
         }  
         //You can have more methods here  
         Public Dispose()  
         {  
          foreach (XLANGMessage xlm in h.Keys)  
           Xlm.Dispose();  
         }  
    }  
    ```  
  
     You would call **A.Dispose** when you are finished with the collection of **XLANGMessages**.  
  
## See Also  
 [Messages Represented as XSD Schemas](../core/messages-represented-as-xsd-schemas.md)   
 [Messages Represented as .NET Classes](../core/messages-represented-as-net-classes.md)   
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)