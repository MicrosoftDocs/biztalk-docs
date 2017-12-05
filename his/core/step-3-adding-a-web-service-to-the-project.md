---
title: "Step 3: Adding a Web Service to the Project | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d481116d-88ce-4889-8f45-2c5c69321224
caps.latest.revision: 3
---
# Step 3: Adding a Web Service to the Project
Once you have created the XML web service, you can add the web service to your project. Once you have added the web service, you can start the application.  
  
### To add a web service to the project  
  
1.  In the Solution Explorer, right-click HISTraining, select **Add…**, and then click **New Web Site**.  
  
2.  In the Add New Web Site dialog, select ASP.NET Web Service.  
  
3.  In the Location drop-down box, select HTTP, and enter **http://localhost/DB2WebService** to the field, and then click OK  
  
4.  In Solution Explorer, right-click **http://localhost/DB2WebService**, and then click **Add Reference…**.  
  
5.  In the Add Reference dialog, on the **Projects** tab, select DB2DAL, and then click OK.  
  
6.  In Solution Explorer, expand **http://localhost/DB2WebService**, expand App_Code, and double-click Service.vb.  
  
7.  Add the following code to Service.vb  
  
    ```  
    Imports System.Web  
    Imports System.Web.Services  
    Imports System.Web.Services.Protocols  
  
    <WebService(Namespace:="http://tempuri.org/")> _  
    <WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
    <Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
    Public Class Service  
         Inherits System.Web.Services.WebService  
  
        <WebMethod()> _  
        Public Function executeSQLQuery(ByVal connstring As String, ByVal sqlStatement As String) As Data.DataSet  
            Dim dal As New DB2DAL.DB2DAL  
            Return dal.executeSQL(sqlStatement, connstring)  
        End Function  
  
    End Class  
    ```  
  
8.  On the **Build** menu, click **Build Solution**.  
  
9. On the File menu, click **Save All**.  
  
## See Also  
 [Step 4: Executing the Web Service](../core/step-4-executing-the-web-service.md)   
 [Managed Provider for DB2 Tutorial](../core/managed-provider-for-db2-tutorial.md)