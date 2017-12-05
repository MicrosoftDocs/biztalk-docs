---
title: "How to Create a Metadata Assembly for the Host File Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18ec0919-6d80-4354-97dd-f9dfe5798fff
caps.latest.revision: 4
---
# How to Create a Metadata Assembly for the Host File Adapter
After you install the adapter, you can create a metadata assembly that describes your remote system to BizTalk Server.  
  
### To create a metadata assembly  
  
1.  Create a Host File project and application in Visual Studio.  
  
     Part of the process of creating a Host File application in Visual Studio is describing the layout of the host file system. This process creates both a metadata assembly and a schema. The metadata assembly is a programmatic representation of the remote host file system, whereas the schema is an XML representation of the host file system. You will use the metadata assembly to describe the host file system to BizTalk Server.  
  
     For more information about how to create a Host File application in Visual Studio, see [Creating an Application with the Managed Data Provider for Host Files](../HIS2010/creating-an-application-with-the-managed-data-provider-for-host-files1.md).  
  
## See Also  
 [BizTalk Adapter for Host Files Configuration](../HIS2010/biztalk-adapter-for-host-files-configuration2.md)   
 [Managed Data Provider for Host Files](../HIS2010/managed-data-provider-for-host-files1.md)   
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)