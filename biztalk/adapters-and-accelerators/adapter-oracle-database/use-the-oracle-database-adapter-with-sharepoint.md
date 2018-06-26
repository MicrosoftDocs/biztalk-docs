---
title: "Use the Oracle Database Adapter with SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 254204e5-3b5d-4e70-97ab-817660d1206a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use the Oracle Database Adapter with SharePoint
The WCF Adapter Service Development Wizard for [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] enables the Microsoft BizTalk Adapter for Oracle Database and the Microsoft BizTalk Adapter for Oracle E-Business Suite to be directly consumed as an external datasource in Microsoft SharePoint. The Add Service Development Wizard that supports this feature is launched with the **WCF Adapter Service** template for creating a new Visual C# Web Sites in [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]. The template is included with the [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)]. You must also install the Microsoft Windows Communication Foundation (WCF) Line of Business (LOB) Adapter SDK.  
  
## SharePoint Operation Support  
 The Adapter Service Development wizard generates a special service contract for the Oracle adapters that is compatible with Microsoft SharePoint. The wizard will generate a service contract which includes the following operations for integrating the adapter with Microsoft SharePoint:  
  
- **Create:** Supported by the CreateItem_ operation.  
  
- **Read:** Supported by the ReadItem_ operation.  
  
- **Update:** Supported by the UpdateItem_ operation.  
  
- **Delete:** Supported by the DeleteItem_ operation.  
  
- **Query:** Supported by the ReadList operation.  
  
- **Associate:** Supported by the Associate_ operation.  
  
  The following service contract was generated using for the Microsoft BizTalk Adapter for Oracle Database as an example. The adapter is configured to provide access to the EMP table  
  
```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface ISCOTT_EMP {  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadList(System.Nullable<int> Limit);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void CreateItem(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void UpdateItem_EMPNO(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void DeleteItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] Associate_DEPTNO(System.Nullable<decimal> DEPTNO);  
}  
```  
  
## Create a New Web Site to Host the Oracle Database in IIS  
 These steps provide an example using the WCF Adapter Service Development Wizard, to create a new WCF web service hosting the Microsoft BizTalk Adapter for Oracle Database. The service contract will include operations directly compatible with Sharepoint. So that it can be directly consumed as an external datasource. The adapter is configured to authenticate with the Oracle database using the **SCOTT** account. If the **SCOTT** account is locked, you can unlock the account by logging into SQL Plus as SYSDBA.  
  
```  
<Oracle Installation Bin Directory>\Sqlplus.exe SYS AS SYSDBA  
```  
  
 Then run the following command.  
  
```  
SQL> ALTER USER scott ACCOUNT UNLOCK;  
```  
  
#### Create the New Web Site Project  
  
1. Open Visual Studio.   
  
2. In Visual Studio, on the **File** menu, select **New** and then click **Project**.  
  
3. In the **New Project** dialog box, expand **Other Languages** and click **Visual C#**. Find the **WCF Adapter Service** in the template list and click it to select it.  
  
   > [!NOTE]
   >  The **WCF Adapter Service** template is not available if the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] is not installed. On x64 systems, install both the x86 and x64 versions of the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].  
  
4. Specify **ScottEMP** for the name, and then click **OK**. The **WCF Adapter Service Development Wizard** starts.  
  
5. On the **Introduction** page, click **Next**.  
  
6. On the **Choose Operations** page, specify the **oracleDBBinding** binding.  
  
7. Click the **Configure** button. The **Configure Adapter** dialog is displayed.  
  
8. On the **Security** tab, select **Username** in the **Client credential type** dropdown list box.  
  
9. Enter **SCOTT** for the User name and enter the correct password for the SCOTT account. The default password for the SCOTT account is **tiger**.  
  
10. Click the **URI Properties** tab, enter the IP address or host name for your Oracle server in the **ServerAddress** box.  
  
11. Enter the correct Oracle database service instance name in the **ServiceName** box. You can copy the instance name information from Oracle Enterprise Manager.  
  
12. Press the **OK** button on the **Configure Adapter** dialog  
  
13. On the **Choose Operations** page of the wizard, click the **Connect** button and wait a few moments for the categories to be built for the Oracle database.  
  
14. Once the categories are added in the **Select a category** list, scroll down to **SCOTT** and expand it. Then expand **Table** and click the **EMP** table entry.  
  
15. In the **Available categories and operations** list, select all the operations in the list and click the **Add** button. All the operations are added to the **Added categories and operations** list.  
  
16. On the **Choose Operations** page, click the **Next** button.  
  
17. On the **Configure Service and Endpoint Behaviors** page, set the **UseServiceCertificate** Service behavior to **false** for this example. Then click the **Next** button.  
  
18. On the **Configure Service Endpoint Binding and Address** page, click the **Apply** button. Then click the **Next** button.  
  
19. On the **Summary** page, click the **Finish** button.  
  
20. Click the **Build** menu option and then click **Build Solution**. Verify the project build was successful with no errors.  
  
## Publish the New Service to IIS  
 For this example you will publish the adapter host service to the local IIS web server.  
  
1.  In Solution Explorer for Visual Studio, right click the **ScottEmp** project and click **Properties**. The Project Designer tabs are displayed.  
  
2.  Click the **Web** tab, then click the **Use Local IIS Web server** option.  
  
3.  Click the **Create Virtual Directory** button.  
  
4.  Open a web browser to the service address **http://localhost/ScottEmp/ISCOTT_EMP.svc**. You should receive a message stating “You have created a service” indicating the adapter is hosted in IIS.  
  
## Add the External Data Source to a SharePoint Site using SharePoint Designer  
 This section describes how to add the WCF Service as an external data source to a new Web Site using SharePoint Designer.  
  
  
1.  Open SharePoint Designer and create a new Web Site.  
  
2.  In SharePoint Designer, expand **Navigation** and click **External Content types** in the **Site Objects** list.  
  
3.  Click the **External Content Type** menu button to create a new external content type.  
  
4.  Click the text beside **Name** to edit the name of the new external content type. Enter **OracleEMP** for the name.  
  
5.  Click the text link beside **External System** which says **Click here to discover external data sources and operations.**. This opens the Operation Designer for the OracleEMP external content type.  
  
6.  Click the **Add Connection** button on the discovery screen.  
  
7.  In the External Data Source Type Selection dialog, choose **WCF Service** and click the **OK** button.  
  
8.  In the WCF Connection dialog, in the **Service Metadata URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**  
  
9. In the **Service Endpoint URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc**  
  
10. Click the **OK** button to close the WCF Connection dialog.  
  
11. Once the Data Source information is populated, expand the **https://localhost/ScottEmp/ISCOTT_EMP.svc** data source and expand **Web Methods**.  
  
12. Right click the **ReadList** Web Method and click **New Read List Operation**. The Read List configuration dialog is launched.  
  
13. In the Read List dialog click **Return Parameters** and click **EMPNO** in the Data Source Elements. Click the **Map to identifier**.  
  
14. Click **Finish** in the Read List dialog.  
  
15. Save the new external data source by typing **Ctrl+s**.  
  
#### Test the External Data Source Connection  
  
1.  In the new web site, click the **Create Lists and Forms** button. The Create List and Form for OracleEMP dialog appears.  
  
2.  Enter **OracleEMP_List** for the List Name and click the **OK** button.  
  
3.  Once the list is create, click the **Summary View** button on the menu.  
  
4.  Click **OracleEMP_List** under External Lists.  
  
5.  Click the **Preview in Browser** button on the menu to test the ReadList operation of the adapter.  
  
## Troubleshoot
  
-   On 64-bit machines you must make sure that 32-bit Oracle client components are also installed. This is because Visual Studio and it’s wizards will be running as a 32-bit process requiring access to 32-bit components during development.