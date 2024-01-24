---
description: "Learn more about: How to Use Expressions to Perform Message Assignments"
title: "How to Use Expressions to Perform Message Assignments"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use Expressions to Perform Message Assignments
You can use expressions to manipulate messages in various ways in your orchestration.  
  
## Referring to message fields  
 You can refer to a distinguished field in a message by appending the field name to the message name as follows:  
  
```  
MyMsg.Amount  
```  
  
 In this example, MyMsg is the message, and Amount is a field that has been identified as a distinguished field for the message type that MyMsg is based on.  
  
## Assigning to messages and message parts  
 You can assign a message directly to another message, or a message part to a message part:  
  
```  
MyMsg=IncomingMsg;  
MyMsg.Invoice=IncomingMsg.Invoice;  
```  
  
 In this example, Invoice is a message part based on a schema.  
  
 If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message by assigning the first to the second in a Construct Message shape, and modify the property on the new message within the same Construct Message shape.  
  
> [!NOTE]
>  You cannot refer or assign to message fields, such as MyMsg.Invoice.MyField, unless they have been promoted; you can only refer or assign to entire messages, message parts, promoted message properties, or distinguished fields.  
  
## Adding message parts  
 You can add additional parts to an existing multipart message by using the **XLANGs.BaseTypes.XLANGMessage.AddPart** method. To do so, do the following:  
  
-   Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes**.  
  
-   Implement a public class similar to the following:  
  
    ```  
    public class MyAddPartHelper  
    {  
         public static void AddPart(XLANGMessage msg, object part, String partName)  
         {  
              msg.AddPart(part, partName);  
         }  
    }  
    ```  
  
     There are three overloaded methods for **Microsoft.XLANGs.BaseTypes.AddPart**:  
  
    ```  
    public void AddPart(object part, String partName);  
    public void AddPart(XLANGPart part);  
    public void AddPart(XLANGPart part, String partName);  
    ```  
  
-   In your BizTalk project, add a reference to the public class and call the **AddPart** method from the **Expression** shape in your orchestration as follows:  
  
    ```  
    MyAddPartHelper.AddPart(myMessage, myStringObject, “StringObject1”);  
    ```  
  
> [!NOTE]
>  You cannot add non-serializable objects or custom formatted objects as message parts. All static parts must be initialized before adding additional parts using the **AddPart** method. You can add arbitrary parts to a message only inside its message construct statement. Adding additional parts outside of the message construct statement is not supported.  
  
## Retrieving message parts  
 You can retrieve a message part from an existing multipart message by using the **RetrieveAs** method from **Microsoft.XLANGs.BaseTypes**. To do so, do the following:  
  
-   Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes**.  
  
-   Implement a public class similar to the following:  
  
    ```  
    Public class MyAddPartHelper  
    {  
         public static Object GetPart(XLANGMessage msg, string sName, Type t)  
         {  
              XLANGPart p =  msg[sName];  
              return p.RetrieveAs(t);  
         }  
         public static Object GetPart(XLANGMessage msg, int partIndex, Type t)  
         {  
               XLANGPart p = msg[partIndex];  
               return p.RetrieveAs(t);  
          }  
    }  
    ```  
  
    > [!NOTE]
    >  The **RetrieveAs** method supports retrieving message parts by name and by index.  
  
-   In your BizTalk project, add a reference to the public class and call the **GetPart** method from the **Expression** shape in your orchestration as follows:  
  
    ```  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, "StringObject1" , typeof(System.String));  
    //sPart is a type of System.String  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, 1, typeof(System.String));  
    //Retriving the message part with index = 1  
    ```  
  
## Message part context property access  
 A message part has context separate from the message context. You can construct message part context properties through the schema editor when you set the **Property Schema Base** property for the associated element to **PartContextPropertyBase.**  
  
 The access is similar to message properties, through an expression like:  
  
```  
Msg.PartName(myPartContextProperty)  
```  
  
 For example:  
  
```  
Str=Msg.PartName(myPartContextProperty); //assumes myPartContextProperty is of type string  
```  
  
## XLANGMessage context property access  
 If you would like to access message properties from the **XLANGMessage** interface from your code, you can pass the message as a parameter of type **Microsoft.XLANGs.BaseTypes.XLANGMessage** to a method from an Expression shape, and then use the **Microsoft.XLANGs.BaseTypes.XLANGMessage** methods **SetPropertyValue** and **GetPropertyValue** to achieve this. To do so, do the following:  
  
-   Create a C# project and add a reference to **Microsoft.XLANGs.BaseTypes** and **Microsoft.BizTalk.GlobalPropertySchemas**.  
  
-   Access the context property using the code similar to the below:  
  
    ```  
    MyMsg.GetPropertyValue(typeof(BTS.MessageID));  
    MyMsg.SetPropertyValue(typeof(MIME.IsMultipartRelated), true);  
    ```  
  
> [!NOTE]
>  If you would like to get or set your own custom context properties, you need to add a reference to your property schema project or add a reference to the assembly contains the property schemas in your C# project.  
  
## Assigning to message properties  
 You can assign a value to a message property:  
  
```  
MyMessage(MySchemaNamespace.MyProperty)=True;  
```  
  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you can refer to and assign values to the MIME properties of a multi-part message:  
  
```  
Message_Out.MessagePart_1(MIME.FileName)="document.doc";  
```  
  
> [!NOTE]
>  A BizTalk message consists of message context and message parts. You must first initialize the message parts before you can get or set any message context property; otherwise, you will receive error during the XLANG compile time.  
  
## See Also  
 [Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md)   
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)   
