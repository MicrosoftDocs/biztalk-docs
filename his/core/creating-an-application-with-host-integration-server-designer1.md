---
title: "Creating an Application with Host Integration Server Designer1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa0b06f6-92d2-4dca-83b9-5e30d56e270d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Creating an Application with Host Integration Server Designer
Using the tools for Host Integration Server (HIS) Designer in Visual Studio, you can create an application that uses Transaction Integrator (TI) to communicate with a remote mainframe.  
  
1. Create a new project for your application.  
  
2. Add a library to your project that uses Transaction Integrator.  
  
3. If available, import a Host File.  
  
    A host file is a file that describes the interfaces your application will be programming towards on the remote server. Using HIS Designer, you can create a .dll that describes these interfaces.  
  
4. If necessary, use HIS Designer to make any changes or additions to the interfaces.  
  
5. Write your application.  
  
    Your application is simply a standard application that includes a reference to the deployed .dll.  
  
6. Test and modify your code.  
  
    If necessary, you many need to undeploy the assembly in order to update the interfaces.  
  
   One you are finished testing your application, you can move your application to a staging or production server. If you want to use the BizTalk Adapter for Host Applications, you can add your assemblies to a BizTalk Server export package.  
  
## In This Section  
 [How to Create a New Host Integration Server Designer Project](../core/how-to-create-a-new-host-integration-server-designer-project1.md)  
  
 [How to Add a Library to a Transaction Integrator Project](../core/how-to-add-a-library-to-a-transaction-integrator-project2.md)  
  
 [How to Import a Host File into a Transaction Integrator Project](../core/how-to-import-a-host-file-into-a-transaction-integrator-project2.md)  
  
 [How to Modify and Update a Transaction Integrator Interface](../core/how-to-modify-and-update-a-transaction-integrator-interface2.md)  
  
 [How to Deploy a Host File Interface](../core/how-to-deploy-a-host-file-interface1.md)  
  
 [How to Code a Transaction Integrator Application](../core/how-to-code-a-transaction-integrator-application2.md)  
  
 [How to Test and Modify a Transaction Integrator Application](../core/how-to-test-and-modify-a-transaction-integrator-application2.md)  
  
## See Also  
 [Host Integration Server Designer UI](./host-integration-server-designer-ui1.md)