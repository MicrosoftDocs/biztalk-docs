---
description: "Learn more about: How to Create a Transaction Integrator Project and Interface Definition"
title: "How to Create a Transaction Integrator Project and Interface Definition1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create a Transaction Integrator Project and Interface Definition
When you are creating an application for the BizTalk Adapter for Host Applications, you first create a Visual Studio solution to contain your projects, and then you create a Transaction Integrator (TI) project. Using the TI project, you will create an interface definition of the host application. Later, you will use the interface definition, together with an associated .xml schema, to describe the interface to your BizTalk application.  
  
### To create a TI project in Visual Studio  
  
1.  In your Visual Studio solution, click **File**, point to **Add**, and then click **New Project**.  
  
2.  In the **Add New Project** dialog box, in the **Project types** pane, click **Host Integration Projects**.  
  
3.  In the **Templates** pane, click **Transaction Integrator Project**.  
  
4.  Enter the name of your TI project in the **Name** field, enter the location to save the project in the **Location** field, and then click **OK**.  
  
### To add a .NET client library to the TI project  
  
1.  In Solution Explorer, right-click the name of your TI project, point to **Add**, and then click **Add .NET Client Library**.  
  
2.  In the **Add New Item** dialog box, confirm that .**NET Client Library** is selected in the **Templates** pane.  
  
3.  Type the name of the client library in the **Name** field, and then click **OK**.  
  
4.  On the **.NET Client Library WizardWelcome** page, click **Next**.  
  
5.  On the **Library** page, in the **Type Restrictions** field, select **BAHA**.  
  
6.  Enter the relevant name, version number, and description, and then click **Next**.  
  
7.  On the **Remote Environment** page, enter the relevant information that describes the remote environment, click **Next**, and then click **Create**.  
  
     If you do not know this information, you should speak to your mainframe systems developer.  
  
### To construct the interface definition  
  
1.  In Host Integration Server Designer, right-click the node of the .NET client library, point to **Import**, and then click **Host Definition**.  
  
2.  Use the Import COBOL Wizard to import a host definition file.  
  
     By importing the host definition file into the .NET client library, HIS Designer also creates an XML schema data (XSD) file. This XSD file contains the interface definition you will use later in your BizTalk application. For more information about using the Import COBOL Wizard, see [Import COBOL Wizard](../core/import-cobol-wizard2.md).  
  
3.  You may view the XSD file by clicking the **XSD Definition** tab in HIS Designer.  
  
4.  Click **File**, and then click **Save All**.  
  
     The XSD file should be saved in the standard location for the project. Note that you will need this location in the next step, when you add the XSD file to your BizTalk project. For more information, see [How to Create a BizTalk Project](../core/how-to-create-a-biztalk-project2.md).  
  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications2.md)   
 [How to Create a Visual Studio Solution](../core/how-to-create-a-visual-studio-solution1.md)   
 [How to Create a BizTalk Project](../core/how-to-create-a-biztalk-project2.md)
