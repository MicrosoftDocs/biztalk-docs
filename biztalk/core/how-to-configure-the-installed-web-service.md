---
title: "How to Configure the Installed Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services, configuring"
  - "deploying, Web services"
  - "Web services, deploying"
ms.assetid: 5a281daa-9e1c-47b0-9002-66ea18ed6caf
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Installed Web Service
After you install the Web service files, you must configure BizTalk Server to receive messages from the Web service.  
  
### To configure the Web service  
  
1.  In BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then right-click the application that you want to configure the Web Service.  
  
2.  Point to **Import**, and then click **Bindings**.  
  
3.  Select the BindingInfo.xml file in the distribution folder, and then click **OK**.  
  
4.  Start your orchestrations and enable receive locations.  
  
## See Also  
 [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md)   
 [Deploying Published Web Services on a Non-Visual Studio Computer](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)