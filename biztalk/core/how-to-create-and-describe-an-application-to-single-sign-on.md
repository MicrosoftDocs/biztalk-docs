---
title: "How to Create and Describe an Application to Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d717885-b132-4ba0-a93b-03377ac5eb97
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create and Describe an Application to Single Sign-On
A common administrative task that you might need to perform is adding an affiliate application into the Enterprise Single Sign-On (SSO) database. Adding an affiliate application to the Enterprise SSO database enables you to associate users and credentials with the affiliated application.  
  
> [!NOTE]
>  Creating an affiliated application requires membership in the "SSO Affiliate Administrator" account or above.  
  
### To create and describe an application in the SSO database  
  
1. Create a new `ISSOAdmin` object.  
  
2. Create a new application with a call to `ISSOAdmin.CreateApplication`.  
  
3. Add the relevant fields describing the application with a call to `ISSOAdmin.CreateFieldInfo`.  
  
    During this step, you tell the database that an application has users and associated passwords.  
  
4. Push the newly created description out to the server with a call to `ISSOAdmin.UpdateApplication` or `ISSOAdmin2.UpdateApplication2`.  
  
    The difference between the two methods is that `UpdateApplication2` uses an `IPropertyBag` as the way to describe the application updates, while `UpdateApplication` has multiple parameters.  
  
5. Purge the local cache for the changes you made by calling `ISSOAdmin.PurgeCacheForApplication`.  
  
    Purging the local cache is a security measure that prevents having the names and passwords that you describe in step 3 to exist in an unsecured location.  
  
   The following example shows how to create an application and add field information.  
  
```  
public static bool AddApplication(string name, string admins, string users)  
    {  
       try  
       {  
          ISSOAdmin admin=new ISSOAdmin();  
          // Create application.  
          admin.CreateApplication(name, "SSO Sample Application", "administrator@ssoaffiliateapplication.com", users, admins, SSOFlag.SSO_WINDOWS_TO_EXTERNAL | SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, 2);  
          // Add fields.  
          admin.CreateFieldInfo(name, "User Id", SSOFlag.SSO_FLAG_NONE);  
          admin.CreateFieldInfo(name, "Password", SSOFlag.SSO_FLAG_FIELD_INFO_MASK);  
          // Enable application.  
          admin.UpdateApplication(name, null, null, null, null, SSOFlag.SSO_FLAG_ENABLED, SSOFlag.SSO_FLAG_ENABLED);  
          // Purge changes.  
          admin.PurgeCacheForApplication(name);  
       }  
       catch  
       {  
          return false;  
       }  
       return true;  
    }  
```  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)