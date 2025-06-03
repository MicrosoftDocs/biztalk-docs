---
description: "Learn more about: Invoke a Function in Oracle Database using the WCF Channel Model"
title: "Invoke a Function in Oracle Database using the WCF Channel Model"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Invoke a Function in Oracle Database using the WCF Channel Model
This section demonstrates how to execute a function in an Oracle database using the channel created in [Create a Channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).  
  
## Executing a Function Using the Channel  
 You can execute a function on an Oracle database by passing an XML message to [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]. The input XML resembles the following:  
  
```  
<CREATE_ACCOUNT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG" xmlns:ns0="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT">  
  <REC xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
    <ns0:ID>1</ns0:ID>  
    <ns0:NAME>Scott</ns0:NAME>  
    <ns0:BANKNAME>CitiBank</ns0:BANKNAME>  
    <ns0:BRANCH>NY</ns0:BRANCH>  
    <ns0:ENABLED>Y</ns0:ENABLED>  
  </REC>  
</CREATE_ACCOUNT>  
```  
  
 The following code excerpt demonstrates how to execute a function in an Oracle database using a channel.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Xml;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
using Microsoft.ServiceModel.Adapters;  
using Microsoft.Adapters.OracleDB;  
  
namespace OraclePackageChannel  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create Endpoint  
            EndpointAddress address = new EndpointAddress("oracledb:// ADAPTER");  
  
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
            System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create("Create_Account.xml");  
  
            Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT", readerIn);  
            Message messageOut = channel.Request(messageIn);  
  
            // Get Response XML  
            XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
            // Get Employee ID  
            XmlDocument doc = new XmlDocument();  
            doc.Load(readerOut);  
            doc.Save("d:\\out.xml");  
  
            messageOut.Close();  
            channel.Close();  
        }  
    }  
}  
```  
  
## See Also  
 [Develop Oracle Database Applications by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)   
 [Run an Insert Operation in Oracle Database Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)   
 [Run a SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)
