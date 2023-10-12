---
description: "Learn more about: EnterServiceName"
title: "EnterServiceName1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EnterServiceName
The **EnterServiceName** function presents the user with an algorithmically determined service name for a component and allows the user to change it before returning the final value. This function ensures that the new service name is unique in the Service Control Architecture before accepting it.  
  
## Parameters  
 *Argument 0*  
 Title of the product the user should be queried about.  
  
 *Argument 1*  
 Default service name prefix.  
  
 *Argument 2*  
 Index for this instance of the product. The algorithm uses this index to determine the default name.  
  
## Return Values  
 *Return 0*  
 Status of the operation:  
  
- STATUS_SUCCESSFUL: Operation succeeded.  
  
- STATUS_NOSUCHLANGUAGE: The language specified is not supported.  
  
- STATUS_USERCANCEL: User pressed the **Cancel** button.  
  
  *Return 1*  
  Service name that the user entered.
