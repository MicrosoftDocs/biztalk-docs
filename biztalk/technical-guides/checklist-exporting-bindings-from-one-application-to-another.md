---
title: "Checklist: Exporting Bindings from One Application to Another | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 152924e6-da64-4db9-a852-bdb4e79687fb
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Exporting Bindings from One Application to Another
This topic describes the steps involved in transferring the bindings of one application to another application in either a development or production environment. This process is similar to the process of deploying an application using an .msi file. However, when you deploy an application using an .msi file, the process will automatically create the application. When you transfer the bindings from one application to another, on the other hand, the destination application must already exist.  
  
|Steps|Reference|  
|-----------|---------------|  
|Ensure that you have the appropriate permissions to perform the export operation.|[Permissions for Managing an Application](../technical-guides/permissions-for-managing-an-application.md)|  
|Create a destination application to import the application bindings into.|-   [Creating an Application](../technical-guides/creating-an-application.md)<br />-   "Creating a BizTalk Application" section of [Best Practices for Deploying an Application](../technical-guides/best-practices-for-deploying-an-application.md)|  
|Export the bindings of a source application into a binding file.|-   [How to Export Bindings to a Binding File](../technical-guides/how-to-export-bindings-to-a-binding-file.md)<br />-   "Exporting a BizTalk Application" section of [Best Practices for Deploying an Application](../technical-guides/best-practices-for-deploying-an-application.md)<br />-   "Exporting a BizTalk Application" section of [Known Issues with Deploying an Application](../technical-guides/known-issues-with-deploying-an-application.md).|  
|Import the bindings in a binding file to the destination application.|-   [How to Import Bindings from a Binding File](../technical-guides/how-to-import-bindings-from-a-binding-file.md)<br />-   "Importing a BizTalk Application" section of [Best Practices for Deploying an Application](../technical-guides/best-practices-for-deploying-an-application.md)<br />-   "Importing a BizTalk Application" section of [Known Issues with Deploying an Application](../technical-guides/known-issues-with-deploying-an-application.md).|