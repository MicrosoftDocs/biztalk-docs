---
title: "How to Create an Assembly for the Managed Data Provider for Host Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c588e376-b08e-4527-a3e0-6325be2f62ba
caps.latest.revision: 4
---
# How to Create an Assembly for the Managed Data Provider for Host Files
After you have finished defining a remote environment for your application, you can use Visual Studio to create the application assembly. Host Integration Server provides a variety of wizards and tools to help you in this process:  
  
1.  Create a Host File project.  
  
2.  Add one or more .NET client libraries to the project that will contain your application.  
  
3.  Create the interfaces for your application using Host Integration Server Designer.  
  
     HIS Designer enables you to create interfaces that represent data and methods native to your host environment. By programming towards these interfaces, you can pass information and commands through Host Integration Server and onto the mainframe.  
  
 After you create the assembly, you can deploy your assembly to your local computer and test the interfaces against your code.  
  
### To create an application assembly that uses the Managed Provider for Host Files  
  
1.  Start Visual Studio.  
  
2.  Click **File**, then **New**, and then click **Project**.  
  
3.  In the **New Project** dialog box, in the **Project types:** pane, click Host Integration Projects.  
  
4.  In the **Templates** pane, click **Host File Project**.  
  
5.  In the **Name** field, type the name of your project.  
  
6.  In the **Location** field, type the location to save your project, and then click **OK**.  
  
### To add an assembly to your project  
  
1.  Click **Project**, and then click **Add .NET Client Library**.  
  
     The Managed Provider for Host Files supports .NET only.  
  
2.  On the **Add New Item** dialog box, in the **Templates** pane, confirm that .NET Client Library is highlighted.  
  
3.  In the **Name:** field, type the name of the assembly, and then click **Add**.  
  
4.  On the **Welcome to the .NET Client Library Wizard** page, click **Next**.  
  
5.  On the **Completing the .NET Client Library Wizard** page, confirm that the displayed settings are correct, and then click **Create**.  
  
### To define interfaces using the HIS Designer  
  
1.  If you do not have a Host Definition file (.hcd) file available, you can use the **Import COBOL Wizard** or the **Import RPG Wizard** to define your interfaces.  
  
     For more information, see [How to Import COBOL into a TI Component](../core/how-to-import-cobol-into-a-ti-component1.md).  
  
2.  If you have a previous .NET client library that you want to base your new object on, you can use the Import Library tool to import the library into your project.  
  
     For more information, see [How to Import a TI Component](../core/how-to-import-a-ti-component1.md).  
  
3.  If you want to manually create or modify the interface definitions, you can do so using the console tree of HIS Designer.  
  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications1.md)