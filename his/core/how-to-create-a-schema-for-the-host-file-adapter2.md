---
title: "How to Create a Schema for the Host File Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03f7d0c3-039c-454b-bd10-a569f5d2fc3f
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Schema for the Host File Adapter
You can use the Host File Schema Generation Wizard to create the XSD schemas for the BizTalk Adapter for Host Files. After you create the schema, you are ready to continue configuration on the BizTalk Server side.  
  
### To generate the Host File schema  
  
1.  Open your BizTalk Server Visual Studio project.  
  
2.  Right-click the project, point to **Add**, and then select **Add Generated Items**.  
  
3.  In the **Add Generated Items** dialog box, select **Add Adapter Metadata**.  
  
     This starts the Add Adapter Wizard.  
  
4.  On the **Select Adapter** page, select **Host File**, and then click **Next**.  
  
     This starts the Host File Adapter Schema Generation Wizard.  
  
5.  On the **Database Information** page, browse to an existing connection string or create a new one.  
  
     This can be Initial Catalog, Package Collection, (TCP Address and Port) or (APPC Local LU, Remote LU, and Mode), (User Name and Password), or (Integrated Security). Maximum length is 1024.  
  
6.  On the **Schema Information** page, define the default namespace, root elements, and port type that you want to use in the schema.  
  
     If you select **Receive port**, only a request document root element name is needed. If you select **Send port**, request and response document root element names are required.  
  
7.  On the **Statement Type Information** page, select the type of database command to be issued.  
  
     If you selected send ports on the previous page, you can choose to issue an updategram, stored procedure, or SELECT statement. If you selected receive ports, this step is unnecessary.  
  
8.  On the **Statement Information** page, enter the details about the host file.  
  
     Depending on the information entered on earlier pages, the following properties will be available. If you selected send port:  
  
    -   **Send Updategram** If you chose to use a send port and updategrams, you can select the updategram operation here, and also the table and columns that will be present in the updategram.  
  
    -   **Send System Command** If you chose to use a send port and issue a stored procedure, you can select a stored procedure from the current connection’s catalog. You do not have to enter values for all parameters on this page.  
  
    -   **Send Select Statement** If you chose to use a send port with an SQL Select statement, you can either select or browse to the statement here.  
  
     If you selected receive port:  
  
    -   **Receive Select Statement** If you chose to use a receive port with an SQL statement, you can either select or browse to the statement here.  
  
    -   **Send Updategram** If you chose to use a send port and updategrams, you can select the updategram operation here, and also the table and columns that will be present in the updategram.  
  
    -   **Send Stored Procedure** If you chose to use a send port and issue a stored procedure, you can select a stored procedure from the current connection’s catalog. You do not have to enter values for all parameters on this page.  
  
    -   **Send Select Statement** If you chose to use a send port with an SQL Select statement, you can either select or browse to the statement here.  
  
9. On the **Completing the Host File Transport Schema Generation Wizard** page, click **Finish**.  
  
## See Also  
 [BizTalk Adapter for Host Files Configuration](../core/biztalk-adapter-for-host-files-configuration1.md)   
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)   
 [Managed Data Provider for Host Files](../core/managed-data-provider-for-host-files1.md)