---
title: "Step 2: Creating an XML Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a194d7ba-131e-4b37-8edc-7a2f9af0c258
caps.latest.revision: 4
---
# Step 2: Creating an XML Web Service
After you have created the connection string to your DB2 database, you can create the XML web service. After you have created the service, you can add the service to the project.  
  
### To create the XML web service  
  
1.  In Visual Studio, click File, select New, and then click Project…  
  
2.  In the New Project dialog, in the **Project types:** pane, click Other Project Types, and then select Visual Studio Solutions.  
  
3.  In the **Templates** pane, confirm that Blank Solution is selected.  
  
4.  Type `HISTraining` in the **Name** field, and then click **OK**.  
  
### To add code to the web service  
  
1.  In Solution Explorer, right-click HISTraining, select **Add…**, and then click **New Project**.  
  
2.  In the Add New Project dialog, in the **Project types:** pane, click **Other Languages**, and then select **Visual Basic**.  
  
3.  In the **Templates:** pane, select **Class Library**.  
  
4.  In the **Name** field, type `DB2DAL`, and then click **OK**.  
  
5.  In Solution Explorer, right-click DB2DAL, select **Add…**, and then click **Add Reference…**.  
  
6.  In the Add Reference dialog, on the **.NET** tab, select Microsoft.HostIntegration.MsDb2Client, and then click **OK**.  
  
7.  Add the following code to your Class1.vb file:  
  
    ```  
    Imports Microsoft.HostIntegration.MsDb2Client  
    Public Class DB2DAL  
        Public Function executeSQL(ByVal sqlQuery As String, ByVal connString As String) As DataSet  
            Dim db2Conn As New MsDb2Connection(connString)  
            Dim db2Cmd As New MsDb2Command(sqlQuery, db2Conn)  
            Dim db2DA As New MsDb2DataAdapter(db2Cmd)  
            Dim returnDS As New DataSet  
            db2Conn.Close()  
            db2DA.Fill(returnDs)  
            db2Conn.Close()  
            Return returnDS  
        End Function  
    End Class  
    ```  
  
8.  On the **Build** menu, click **Build Solution**.  
  
9. On the **File** menu, click **Save All**.  
  
## See Also  
 [Step 3: Adding a Web Service to the Project](../core/step-3-adding-a-web-service-to-the-project.md)   
 [Managed Provider for DB2 Tutorial](../core/managed-provider-for-db2-tutorial.md)