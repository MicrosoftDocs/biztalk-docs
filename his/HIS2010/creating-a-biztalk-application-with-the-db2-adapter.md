---
title: "Creating a BizTalk Application with the DB2 Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 663a068d-4978-4fa6-952b-e292e50f36db
caps.latest.revision: 3
---
# Creating a BizTalk Application with the DB2 Adapter
After you create the schema, ports, and receive locations for the BizTalk Adapter for DB2, you can start coding your BizTalk application.  
  
### To create a BizTalk application using the DB2 Adapter  
  
1.  Create a BizTalk project to hold your BizTalk application.  
  
2.  Use the schema that you created in [How to Create a Schema for the DB2 Adapter](../HIS2010/how-to-create-a-schema-for-the-db2-adapter1.md) to describe the DB2 database to the BizTalk application.  
  
3.  Use the send port that you created in [How to Create a Send Port for the DB2 Adapter](../HIS2010/how-to-create-a-send-port-for-the-db2-adapter1.md) to send data to the DB2 database.  
  
4.  If necessary, use the receive port and location that you created in [How to Create a Receive Port and a Receive Location for the DB2 Adapter](../HIS2010/how-to-create-a-receive-port-and-a-receive-location-for-the-db2-adapter1.md) to receive data from the DB2 database.  
  
5.  Add any additional orchestrations, components, or code, as necessary.  
  
6.  Test your application.  
  
7.  After you finish testing your application, create an .msi package to move your application to a staging or live server.  
  
## See Also  
 [BizTalk Adapter for DB2 Configuration](../HIS2010/biztalk-adapter-for-db2-configuration2.md)   
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)