---
description: "Learn more about: Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model"
title: "Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "running a SQLEXECUTE statement, using a channel"
  - "how to, run a SQLEXECUTE statement by using a channel"
  - "WCF channel model, running a SQLEXECUTE statement"
ms.assetid: e1af11ef-3f44-4726-99ca-d6961d79e651
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model
This section shows how to perform a SQLEXECUTE operation on an Oracle database over a channel. You must specify both a message and a message action on the SOAP message. For more information about the SQLEXECUTE operation, see [Run SQLEXECUTE operation in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).  
  
## The SQLEXECUTE Message  
 The following XML shows a SQLEXECUTE message that returns the next value of an Oracle SEQUENCE.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- New Action: http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE -->  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
    <SQLSTATEMENT>SELECT tid_seq.nextval id FROM dual</SQLSTATEMENT>  
</SQLEXECUTE>  
```  
  
 The SQLEXECUTE can specify a parameter schema element and a parameter block that contains multiple sets of parameter data. The message shown is for a single invocation of the specified SQL statement so the elements that specify the parameter schema and parameter block are omitted from the message body. For information about the message schema for the SQLEXECUTE operation, see [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).  
  
## Specifying the SQLEXECUTE Action  
 You must specify an action for the message. The following code excerpt shows how to specify the action for the SQLEXECUTE message.  
  
```  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
```  
  
## Sending the SQLEXECUTE Message  
 The following code excerpt demonstrates how to invoke a SQLEXECUTE operation on an Oracle database over a channel.  
  
```  
// Create Endpoint  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
  
// Create Binding  
OracleDBBinding binding = new OracleDBBinding();  
  
// Create Channel Factory  
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
// Create Request Channel  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
  
// Send Request  
System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create("SQLExecute.xml");  
  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
Message messageOut = channel.Request(messageIn);  
  
// Get Response XML  
XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
// Get tid_seq SEQUENCE  
string id = null;  
XmlDocument doc = new XmlDocument();  
doc.Load(readerOut);  
XmlNodeList list = doc.GetElementsByTagName("ColumnValue");  
if (list.Count > 0) id = list[0].InnerXml;  
```  
  
> [!NOTE]
>  The SQLEXECUTE operation always returns a weakly-typed result set.  
  
## See Also  
 [Develop Oracle Database applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
 [Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)
