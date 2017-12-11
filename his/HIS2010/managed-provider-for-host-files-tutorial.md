---
title: "Managed Provider for Host Files Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bc6b9dd-f1e3-4bb5-bede-3c6936761ff8
caps.latest.revision: 4
---
# Managed Provider for Host Files Tutorial
This tutorial shows how to access host file data by using the Managed Provider for Host Files. After completing the tutorial, you will be able to do the following:  
  
-   Configure a connection to a host file dataset  
  
-   Build a simple XML Web service to expose host file data using ASP.NET  
  
-   Retrieve a recordset of information from a host file and return that information as a [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] dataset through an XML Web service.  
  
## Getting Started with the Managed Provider for Host Files Tutorial  
 Before you start the Managed Provider for Host Files tutorial, make sure to perform the following actions:  
  
1.  Install Visual Studio.  
  
2.  Ensure that Internet Information Services (IIS) is installed and ASP.NET 2.0 is configured.  
  
3.  Install Microsoft Host Integration Server 2010.  
  
4.  Ensure that you have access to a host dataset with permissions to query and modify data. For more information about the dataset used in this tutorial, see the Appendix.  
  
## Running the Managed Data Provider for Host Files Tutorial  
 To access host file data, you must first define the metadata associated with the dataset. Then you can use the Data Access Tool to configure a connection to the host file. After that, you can create the XML Web service and launch your application.  
  
### Step 1: Define the Structure of the Host File  
 To access the host dataset, you need to define the metadata associated with the dataset. After you have finished defining the various structures used to access the host file system, you can define the connection string you will use to connect to the file system.  
  
##### To create the host file project  
  
1.  In Visual Studio, click **File**, point to **New**, and then click **Project**.  
  
2.  In the **New Project** dialog box, in the **Project types** pane, click **Other Project Types**.  
  
3.  In the **Templates** pane, click **Blank Solution**.  
  
4.  In the **Name** field, enter `Data Integration Samples`, and then click **OK**.  
  
5.  In Solution Explorer, right-click **Data Integration Samples**, point to **Add**, and then click **New Project**.  
  
6.  In the **Add New Project** dialog box, in the **Project types** pane, click **Host Integration Projects**.  
  
7.  In the **Templates** pane, click **Host File Project**.  
  
8.  In the **Name** field, type `NorthwindHostFiles`, and then click **OK**.  
  
##### To add a host file library to the host file project.  
  
1.  In Solution Explorer, right-click **NorthwindHostFiles**, point to **Add**, and then click **Add Host File Library**.  
  
2.  In the **Add New Item - NorthwindHostFiles** dialog box, in the **Name** field, type `NorthwindHostFiles_OS390`, and then click **Add**.  
  
3.  On the **Welcome to the Host Files Library Wizard** page, click **Next**.  
  
4.  On the **Host Environment** page, confirm that **Host Files for OS390** is selected in the **Host environment** drop-down box, click **Next**, and then click **Create**.  
  
##### To import the host file definition  
  
1.  In Solution Explorer, double-click **NorthwindHostFiles_OS390.DLL** to bring up the Host File Designer.  
  
2.  In the Host File Designer, right-click **NorthwindHostFiles_OS390**, point to **Import**, and then click **Host Definition**.  
  
3.  On the **Welcome to the COBOL Import Wizard** page, click **Next**.  
  
4.  On the **Import COBOL Source File** page, click **Browse** to locate the COBOL file that defines the data structures on your host file system, and then click **Next**.  
  
5.  On the **Structures member** page, select the COBOL group that represents the structure members, click **Next**, and then click **Modify**.  
  
##### To map the host file schema to a table  
  
1.  In Host File Designer, expand **NorthwindHostFiles_OS390**, right-click **Tables**, and then click **Add Table**.  
  
2.  Right-click the newly created **table1**, and then click **Properties**.  
  
3.  In the Properties toolbox, enter an alias in the **Alias** field, the host file name in the **Host File Name** field, and a schema name in the **Schema** field.  
  
##### To provide a strong key name to sign the host file project  
  
1.  In Host File Designer, right-click **NorthwindHostFiles_OS390**, and then click **Properties**.  
  
2.  In the **Properties** toolbox, expand **Assembly Information**, and then provide the path and file name to a key file.  
  
##### To save and register the assembly  
  
1.  In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, click **Save**.  
  
2.  Use the gacutil utility and the regasm tool to register the host file assembly.  
  
### Step 2: Create the Data Access String  
 After you have finished defining the structure of the host file, you can use the Data Access Tool to create a data access string. After you confirm the creation of the string, you can then create the XML Web service.  
  
##### To start the Data Access Tool and run the Data Source Wizard  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Host Integration Server 2010**, and then click **Data Access Tool**.  
  
     This starts the Data Access Tool, which you can use to configure connections in both DB2 and host file systems.  
  
2.  In the Data Access Tool, click **File**, point to **New**, and then click **Data Source**.  
  
3.  On the **Welcome to the Data Source Wizard** page, click **Next**.  
  
4.  On the **Data Source** page, in the **Data Source Platform** field, select **Mainframe or AS/36 file system**.  
  
5.  Confirm that the **SNA LU6.2 (APPC)** check box is selected, and then click **Next**.  
  
6.  On the **APPC Network Connection** page, enter the connection information for your mainframe, and then click **Next**.  
  
7.  On the **Mainframe or AS/36** page, enter the default information into the **Default library information** field.  
  
8.  Enter the path of the host file assembly created in the preceding section into the **Host File assembly** field, and then click **Next**.  
  
9. On the **Locale** page, accept the default values, and then click **Next**.  
  
10. On the **Security** page, in the **Security Method** field, confirm that **Interactive sign-on** is selected in the drop-down box.  
  
11. Enter the connection information for your mainframe in the **Properties** fields, and then click **Next**.  
  
12. On the **Advanced Options** page, click **Next**.  
  
13. On the **Validation** page, click **Connect** to test your connection string, and then click **Next**.  
  
14. On the **Saving Information** page, in the **Data source name** field, type `HIS_TRAINING_HF`.  
  
15. Select the **Initialization string file** check box, and then click **Next**.  
  
16. On the **Completing the Data Source Wizard** page, click **Finish**.  
  
##### To view the data source string  
  
1.  Open Notepad and navigate to the directory the data source string is saved in.  
  
     By default, the data source string file is located in C:\Documents and Settings\\<USERNAME\>\My Documents\Host Integration Projects\Data Sources.  
  
2.  Use Notepad to view the HIS_STRAINIGN_HF.txt file.  
  
     You should see the connection string created by the Data Access Tool. It should look something like the following:  
  
     `User ID=myname;Password=mypassword;APPC Remote LU Alias=DFM; APPC Local LU Alias=L3888888;APPC Mode Name=PA62KNU; Network Transport Library=SNA; Host CCSID=37;PC Code Page=1252;Network Port=446;Default Library=MyLibrary;Metadata='C:\Work\DataIntegrationSamples\NortwindHost Files\NortwindHostFiles_OS390.DLL'`  
  
### Step 3: Create the XML Web Service  
 After you have created the data string, you can create the XML Web service and associated code. Then you can test your code on a live Web site.  
  
##### To start Visual Studio and create a new project  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio**, and then click **Microsoft Visual Studio**.  
  
2.  In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
3.  In the **New Project** dialog box, in the **Project types** pane, expand **Other Project Types**, and then click **Visual Studio Solutions**.  
  
4.  In the **Templates** pane, confirm that **Blank Solution** is selected, enter `HISTraining` in the **Name** field, and then click **Next**.  
  
##### To add a class to hold the DB2 access logic  
  
1.  In Solution Explorer, right-click **HISTraining**, point to **Add**, and then click **New Project**.  
  
2.  In the **Add New Project** dialog box, in the **Project types** pane, expand **Other Languages**, and then click **Visual Basic**.  
  
3.  In the **Templates** pane, click **Class Library**.  
  
4.  In the **Name** field, type `HFDAL`, and then click **OK**.  
  
##### To add a reference to the HostFileProvider  
  
1.  In Solution Explorer, right-click **HFDAL**, and then click **Add Reference**.  
  
2.  In the **Add Reference** dialog box, click the **.NET** tab, click the **Microsoft.HostIntegration.HostFileProvider** component, and then click **OK**.  
  
##### To write the code for the Data Access class  
  
1.  In Solution Explorer, click **Class1.vb**.  
  
2.  Enter the following code into the text editor window:  
  
    ```  
    Public Class HFDAL  
        Public Function executeSQL(ByVal sqlQuery As String, ByVal connString As String) As DataSet  
            Dim hfConn As New HostFileConnection(connString)  
            Dim hfCmd As New HostFileCommand(sqlQuery, hfConn)  
            Dim hfDA As New HostFileDataAdapter(hfCmd)  
            Dim returnDS As New DataSet  
  
            hfConn.Open()  
            hfDA.Fill(returnDS)  
            hfConn.Close()  
            Return returnDS  
        End Function  
  
    End Class  
    ```  
  
3.  On the **File** menu, click **Save All**.  
  
4.  On the **Build** menu, click **Rebuild Solution**.  
  
##### To create a Web service for the solution  
  
1.  In Solution Explorer, right-click **HISTraining**, point to **Add**, and then click **New Web Site**.  
  
2.  In the **Add New Web Site** dialog box, click **ASP.NET Web Service**.  
  
3.  In the **Location** combo box, confirm that **HTTP** is selected, type `http://localhost/HFWebService` in the associated text box, and then click **OK**.  
  
4.  In Solution Explorer, right-click **http://localhostHFWebService**, and then click **Add Reference**.  
  
5.  On the **Add Reference** dialog box, click the **Projects** tab, click **HFDAL**, and then click **OK**.  
  
6.  In Solution Explorer, expand **http://localhostHFWebService**, expand **App_Code**, and then double-click **Service.vb**.  
  
7.  Add the following code to Service.vb:  
  
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
        Public Function executeSQLQuery(ByVal connString As String, ByVal sqlStatement As String) As Data.DataSet  
            Dim dal As New HFDAL.HFDAL  
  
            Return dal.executeSQL(sqlStatement, connString)  
  
        End Function  
  
    End Class  
    ```  
  
8.  On the **File** menu, click **Save All**.  
  
### Step 4: Launch the XML Web Service  
 After you are finished creating the XML Web service, you can launch the service and observe the resulting behavior.  
  
##### To execute the Web service  
  
1.  In Solution Explorer, right-click **Service.asmx**, and then click **View in Browser**.  
  
2.  In the Web browser view of Service.asmx, click the hyperlink to **executeSQLQuery**.  
  
3.  On the **executeSQLQuery** page, copy the connection string from HIS_TRAINIGN_HF.TXT into the **connString** field.  
  
4.  In the **sqlStatement** field, type `SELECT* FROM CUSTOMERS`, and then click **Invoke**.  
  
## Appendix  
 The following COBOL copybook is used in this tutorial as the host file dataset.  
  
```  
01 CUSTOMER  
     05 CUSTIDPIC S9(9)COMP.  
     05 COMPANYPIC X(40).  
     O5 CONTACT PIC X(30).  
     05 TITLE PIC X(30).  
     05 ADDRESS PIC X(60).  
     05 CITY PIC X(20).  
     05 REGION PIC X(15).  
     05 ZIP PIC X(10).  
     05 COUNTRY PIC X(10).  
     05 PHONE PIC X(15).  
     05 FAX PIC X(24).  
     05 WEBPINPIC X(5).  
```  
  
## See Also  
 [Managed Data Provider for Host Files Programmer's Guide](../HIS2010/managed-data-provider-for-host-files-programmer-s-guide1.md)