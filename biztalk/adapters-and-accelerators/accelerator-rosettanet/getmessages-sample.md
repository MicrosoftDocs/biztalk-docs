---
title: "GetMessages Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29e575fa-d68b-4975-84b8-da4f17bd2db3
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetMessages Sample
This topic provides sample code that you can use to retrieve messages from one of the message non-repudiation tables or one of the line-of-business (LOB) tables in a readable form. The message non-repudiation tables include MessageStorageIn and MessageStorageOut in the [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]Archive database; the LOB tables include MessageFromLOB and MessageToLOB in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA database.  
  
 Use `GetMessages` for either troubleshooting or development. By default, the code returns a base 64 string.  
  
> [!NOTE]
>  The GetMessages.cs sample code contains two sections of code—one for retrieving messages from one of the LOB tables, and one for retrieving messages from one of the non-repudiation tables. Create separate applications for each purpose.  
  
### To retrieve messages from an LOB table  
  
1.  Add the following sample code to your program:  
  
     `private static string GetLOBMessage(string sMessageSource, string sMessageID)`  
  
2.  Set the `sMessageSource` parameter to either the MessagesFromLOB or MessagesToLOB table.  
  
3.  Set the `sMessageID` parameter to the value of the **MessageID** field in the database.  
  
    > [!NOTE]
    >  The application returns a string that contains the retrieved message.  
  
### To retrieve messages from a non-repudiation table  
  
1.  Add the following sample code to your program:  
  
     `private static string GetNRMessage(string sMessageSource, string sMessageID)`  
  
2.  Set the `sMessageSource` parameter to either the MessageStorageIn or MessageStorageOut table.  
  
3.  Set the `sMessageID` parameter to the value of the **RecordID** field in the database.  
  
    > [!NOTE]
    >  The application returns a string that contains the retrieved message.  
  
## Demonstrates  
 The GetMessages sample includes the following two sections of code:  
  
-   One section shows you how to retrieve a binary message from one of the non-repudiation tables, and convert it into readable ASCII form.  
  
-   The other section shows you how to retrieve a message from one of the LOB tables. Because a message in an LOB table is already in ASCII form, this is a SQL select statement.  
  
    > [!IMPORTANT]
    >  For demonstration purposes, the sample code provided uses a direct SQL statement that is prone to SQL injection vulnerabilities. In a production environment, it is recommended that you use parameterized SQL stored procedures, instead of the direct SQL statement, to prevent such vulnerabilities.  
  
## Example  
 Use one of the two sections in the following code example for retrieving messages from one of the non-repudiation tables or one of the LOB tables.  
  
```  
using System;  
using System.Text;  
using System.Data.SqlClient;   
using Microsoft.Solutions.BTARN.Shared;  
  
namespace Microsoft.Solutions.BTARN.Admin  
{  
  
      /// <summary>  
      /// Summary description for GetMessages.  
      /// </summary>  
      class GetMessages  
      {  
            /// <summary>  
            /// The main entry point for the application.  
            /// </summary>  
            [STAThread]  
            static void Main(string[] args)  
            {  
                  Console.WriteLine(GetLOBMessage("MessagesFromLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetLOBMessage("MessagesToLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetNRMessage("MessageStorageIn", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
                  Console.WriteLine(GetNRMessage("MessageStorageOut", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
            }  
  
            /// <summary>  
            /// Retrieve a message from the LOB tables in the BTARNDATA database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessagesFromLOB or MessagesToLOB</param>  
            /// <param name="sMessageID">The value of the MessageID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>        
            private static string GetLOBMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.DataDbConnectionString);  
                  sQuery = "SELECT ServiceContent from " + sMessageSource + " WHERE MessageID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                        sReturnedMessage=localReader.GetString(0);  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
  
            /// <summary>  
            /// Retrieve a message from the non-repudiation tables in the BTARNArchive database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessageStorageIn or MessageStorageOut</param>  
            /// <param name="sMessageID">The value of the RecordID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>  
            private static string GetNRMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.ArchiveDbConnectionString);  
                  sQuery = "SELECT Content from " + sMessageSource + " WHERE RecordID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                  {  
                        //Determine the size of the field in bytes and create a new byte array  
                        byte[] bData= new byte[localReader.GetBytes(0, 0, null, 0, 0)];  
  
                        //Read the value of the field into bData  
                        localReader.GetBytes(0, 0, bData, 0, bData.Length);  
  
                        //Convert the byte array into a string  
                        sReturnedMessage=Encoding.ASCII.GetString(bData);  
                  }  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
      }  
}  
```  
  
## See Also  
 [Messaging Samples](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)