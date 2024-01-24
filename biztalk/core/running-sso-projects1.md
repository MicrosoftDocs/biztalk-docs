---
description: "Learn how to run a Single Sign-On (SSO) project from Internet Explorer."
title: "Running SSO Projects1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# How to Run SSO Projects

You can run the sample from Internet Explorer.  
  
## Running a Sample from Internet Explorer  
  
1. Open your browser.  
  
2. Use the following syntax:  
  
    ```html  
    http://localhost/SSODemo/BTSHTTPReceive.dll?[Insert XML Instance body]   
    ```  
  
    For example, enter the following syntax:

    ```html 
    http://localhost/SSODemo/BTSHTTPReceive.dll?<ns0:method_list_method%20xmlns:ns0="http://microsoft.com/exposed/object/object1"><ns0:method_list_method><ns1:method_list%20xmlns:ns1="http://microsoft.com/exposed/object"><ns1:comp_code></ns1:comp_code><ns1:comp_name></ns1:comp_name></ns1:object_1></ns0:method_list></ns0:method_list_method>  
    ```

    In this case you do not have to provide the credentials.  
  
## See Also
  
[Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)
