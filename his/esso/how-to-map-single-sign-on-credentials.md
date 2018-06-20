---
title: "How to Map Single Sign-On Credentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13f70953-1ff5-4cb3-869b-544de8a1985e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Map Single Sign-On Credentials
When you know that you have affiliated applications in your Enterprise Single Sign-On database, you can map the credentials for a user to that application. Mapping the credentials of the current user to an affiliated application requires that you use a combination of the `ISSOMapper` and `ISSOMapping` interfaces.  
  
### To map between an affiliated application and user credentials  
  
1. Create new instances of `ISSOMapper` and `ISSOMapping`.  
  
2. Set the `ISSOMapping` properties to the relevant values.  
  
    The relevant properties for `ISSOMapping` are the Microsoft Windows domain name of the user, the Windows user name, the name of the affiliated application, and the external user name.  
  
3. Create the mapping with a call to ISSOMapping.Create.  
  
    Calling `ISSOMapping.Create` propagates the local copy of the mapping out to the Enterprise Single Sign-On server.  
  
4. Set the credentials on the mapping with a call to `ISSOMapper.SetExternalCredentials`.  
  
5. Enable the mapping with a call to `ISSOMapping.Enable`.  
  
   The following example shows how to add mapping between a specified Enterprise Single Sign-On application and a user.  
  
```  
public static bool AddMapping(string application, string user, string XU, string XP)  
{  
   try  
   {  
      // Set mapping.  
      ISSOMapper mapper=new ISSOMapper();  
      ISSOMapping mapping=new ISSOMapping();  
     string username=user.Substring(user.IndexOf('\\')+1);  
      string userdomain=user.Substring(0, user.IndexOf('\\'));  
      mapping.WindowsDomainName=userdomain;  
      mapping.WindowsUserName=username;  
      mapping.ApplicationName=application;  
      mapping.ExternalUserName=XU;  
      mapping.Create(0);  
      // Set credentials.  
      string[] credentials=new string[]{XP};  
      mapper.SetExternalCredentials(application, XU, ref credentials);  
      mapping.Enable(0);  
   }  
   catch  
   {  
      return false;  
   }  
   return true;  
      }  
```  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)