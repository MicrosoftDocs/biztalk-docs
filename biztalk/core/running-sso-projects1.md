---
title: "Running SSO Projects1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO projects"
  - "running SSO projects"
  - "samples, SSO projects"
ms.assetid: f8da1874-7495-47cd-a3a3-881f722c80a2
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running SSO Projects
You can run the sample  from Internet Explorer.  
  
## Running a Sample from Internet Explorer  
  
#### To run the sample from the Internet Explorer  
  
1. Open your browser.  
  
2. Use the following syntax:  
  
   ```  
   http://localhost/SSODemo/BTSHTTPReceive.dll?[Insert XML Instance body]   
   ```  
  
    For example:  
  
    http://localhost/SSODemo/BTSHTTPReceive.dll?<ns0:method_list_method%20xmlns:ns0="http://microsoft.com/exposed/object/object1"><ns0:method_list_method><ns1:method_list%20xmlns:ns1="http://microsoft.com/exposed/object"><ns1:comp_code></ns1:comp_code><ns1:comp_name></ns1:comp_name></ns1:object_1></ns0:method_list></ns0:method_list_method>  
  
    In this case you do not have to provide the credentials.  
  
## See Also  
 [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)