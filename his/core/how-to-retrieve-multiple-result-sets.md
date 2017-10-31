---
title: "How to Retrieve Multiple Result Sets1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d79b122e-da1a-459a-8331-154816d7db0a
caps.latest.revision: 3
---
# How to Retrieve Multiple Result Sets
<xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> provides the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader.NextResult%2A> method to iterate through multiple returned results.  
  
## Example  
 The following example shows how to retrieve multiple result sets.  
  
```  
Public void ReadMyData(string myConnString)  
{  
   string myCallQuery = "CALL MyReports()";  
   MsDb2Connection myConnection = new MsDb2Connection(myConnString);  
   MsDb2Command myCommand = new MsDb2Command(myCallQuery,myConnection);  
   myConnection.Open();  
   MsDb2DataReader myReader;  
   myReader = myCommand.ExecuteReader();  
   do  
      {  
      // Always call Read before accessing data.  
      While (myReader.Read())  
         {  
         Console.WriteLine(myReader.GetString(0) + " , ", "   
                 + myReader.GetString(1));  
         }  
       }  
   while(myReader.NextResult());  
   // Always call Close when done reading.  
   myReader.Close();  
   // Close the connection when done with it.  
   myConenction.Close();  
}  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db2.md)   
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide.md)   
 [Managed Provider for DB2 Programmer's Reference &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/a50e991f-d651-40cb-a45c-d64fa132d251)