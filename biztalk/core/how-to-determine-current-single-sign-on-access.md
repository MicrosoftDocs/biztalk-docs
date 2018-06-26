---
title: "How to Determine Current Single Sign-On Access | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cab68dfc-27cd-4f7c-a0df-20c670306358
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Determine Current Single Sign-On Access
One of the first tasks you might need to perform for a user is to determine what affiliated applications have already been set up for the current user. You can perform this query with a call to ISSOMapper.GetApplications.  
  
### To query the Single Sign-On database for the applications available to the current user  
  
1. Create a new instance of `ISSOMapper`.  
  
    In general, `ISSOMapper` is an interface designed to retrieve information from Single Sign-On (SSO). You will most likely use `ISSOMapper` in many similar queries.  
  
2. Retrieve all applications that are affiliated with the current user by calling GetApplications.  
  
    GetApplications automatically returns only the affiliated applications of the current user.  
  
   The following code example demonstrates how to query the Single Sign-On database.  
  
```  
private static string[] Applications=null;  
. . .  
public static string[] GetCurrentUserApplications()  
{  
   if(Applications==null)  
   {  
      string[] descs;  
      string[] contacts;  
      ISSOMapper mapper=new ISSOMapper();  
      mapper.GetApplications(out Applications, out descs, out contacts);  
   }  
   return Applications;  
}  
```  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)