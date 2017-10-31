---
title: "How to Create a BizTalk Application for the Host File Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 865c7f0f-5a4d-4466-aebc-6b814fdcdf85
caps.latest.revision: 3
---
# How to Create a BizTalk Application for the Host File Adapter
After you create the schema, you can code your BizTalk application. Your application will use the metadata assembly that you created in Visual Studio, in addition to the schema and ports that you created in previous steps.  
  
### To create a BizTalk application using the Host File Adapter  
  
1.  Create a BizTalk project to hold your BizTalk application.  
  
2.  Use the schema that you created in [How to Create a Schema for the Host File Adapter](../core/how-to-create-a-schema-for-the-host-file-adapter.md) to describe the Host File system to the BizTalk application.  
  
3.  Use the send port that you created in [How to Create a Send Port for the Host File Adapter](../core/how-to-create-a-send-port-for-the-host-file-adapter.md) to send data to the host file system.  
  
4.  If necessary, use the receive port and location that you created in [How to Create a Receive Port and a Receive Location for the Host File Adapter](../core/how-to-create-a-receive-port-and-a-receive-location-for-the-host-file-adapter.md)  
  
5.  Add any additional orchestrations, components, or code, as necessary.  
  
6.  Test your application.  
  
7.  After you finish testing your application, create an .msi package to move your application to a staging or live server.  
  
     When you are creating a BizTalk Server .msi package, make sure that you include the host file metadata assembly that you created in [How to Create a Metadata Assembly for the Host File Adapter](../core/how-to-create-a-metadata-assembly-for-the-host-file-adapter.md).  
  
## See Also  
 [BizTalk Adapter for Host Files Configuration](../core/biztalk-adapter-for-host-files-configuration.md)