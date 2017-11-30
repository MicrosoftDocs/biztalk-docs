---
title: "How to Test a Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69f03f07-e1a2-46ca-828f-d5e16a241db4
caps.latest.revision: 4
---
# How to Test a Connection
After you create the appropriate connection string and store it in a file, you can programmatically test the validity of your connection with a call to <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.TestConnection%2A>.  
  
### To test a connection  
  
1.  Create or retrieve the connection string on which you run the sample query.  
  
     For more information about creating and retrieving connection strings, see [Creating a Connection String](../HIS2010/creating-a-connection-string2.md) and [How to Retrieve Data](../HIS2010/how-to-retrieve-data1.md).  
  
2.  Test the connection with a call to <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.TestConnection%2A>.  
  
     If successful, <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.TestConnection%2A> returns the class and version number of the server. Otherwise, the method returns null. Note that you may be required to enter the user name and password. In this case, the **Password** dialog box appears.  
  
## See Also  
 [How to Test a Connection &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/24e38852-f235-4cfe-ae18-9b6faf8fce51)   
 [Performing Administrative Tasks](../HIS2010/performing-administrative-tasks2.md)