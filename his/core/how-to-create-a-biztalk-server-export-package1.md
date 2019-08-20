---
title: "How to Create a BizTalk Server Export Package1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f31fb1b4-92f4-47ba-bb38-71ee45937a99
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Create a BizTalk Server Export Package
After you finish testing your BizTalk application in your development environment, you can put the associated dependencies into an export package. After you create the export package, you can then move your BizTalk application to a staging or live server.  
  
> [!NOTE]
>  The process for creating an export package for a BizTalk application that uses the BizTalk Adapter for Host Applications is identical to creating any other export package that uses an adapter.  
  
### To create an export package for an application that uses the BizTalk Adapter for Host Applications  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Server 2006**, and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Server 2006 Administration**, expand the BizTalk group, and then expand **Applications**.  
  
3.  Right-click the application that you want to export, point to **Export**, and then click **MSI file**.  
  
4.  On the **Welcome to the Export MSI File Wizard** page, click **Next**.  
  
5.  On the **Select Resources** page, select the artifacts to export into the .msi file, and then click **Next**.  
  
6.  If you are prompted, on the **Specify IIS Hosts** page, type the server name of the computer hosting the virtual directory that you want to include, and then click **Next**.  
  
     You will be prompted to specify the server only if the virtual directory has not been previously added to the BizTalk Management database, such as when it was added to the application or was imported in an application.  
  
7.  On the **Dependencies** page, review the dependencies for the application, and then click **Next**.  
  
8.  On the **Destination** page, in **Destination application name**, type the application name.  
  
9. In **MSI file to generate**, type the full path for the .msi file, and then click **Export**.  
  
10. On the **Summary** page, note the location of the log file for this operation, and then click **Finish**.  
  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications2.md)   
 [How to Export the Schema](../core/how-to-export-the-schema1.md)   
 [How to Deploy the BizTalk Server Application](../core/how-to-deploy-the-biztalk-server-application2.md)