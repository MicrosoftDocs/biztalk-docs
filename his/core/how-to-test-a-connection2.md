---
description: "Learn more about: How to Test a Connection"
title: "Test a Connection | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2245a24e-2a0f-4b07-a3ac-ed979c20e2c5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Test a Connection
After you create the appropriate connection string and store it in a file, you can programmatically test the validity of your connection with a call to  `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.TestConnection%2A`.  
  
## Test a connection  
  
1.  Create or retrieve the connection string on which you run the sample query.  
  
     For more information about creating and retrieving connection strings, see [Creating a Connection String](../core/creating-a-connection-string1.md) and [How to Retrieve Data](../core/how-to-retrieve-data2.md).  
  
2.  Test the connection with a call to `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.TestConnection%2A`.  
  
     If successful, `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.TestConnection%2A` returns the class and version number of the server. Otherwise, the method returns null. Note that you may be required to enter the user name and password. In this case, the **Password** dialog box appears.  
  
## See Also  
 [Performing Administrative Tasks](../core/performing-administrative-tasks1.md)
