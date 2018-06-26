---
title: "Data Access Tool2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88b57df9-92c9-4935-b50e-9c025711f097
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Access Tool
The Data Access Tool enables you to define and test connections to remote IBM DB2 relational database servers and IBM host file systems. You can view configured data sources in a scope (folder browser) and results (list item details) pane. You can use an intuitive Data Source Wizard that guides you through the process of defining, test-verifying, and storing connection information.  
  
 The following list describes the user interface tasks that you can perform by using the Data Access Tool.  
  
-   Importing an IBM DB2 Connect configuration  
  
-   Creating a New Data Source for DB2 or Host Files  
  
-   Editing a Data Source  
  
-   Displaying a Connection String  
  
-   Testing a Connection  
  
-   Creating Packages for DB2  
  
-   Running a Sample Query  
  
-   Opening a File  
  
-   Cut, copy and paste a Data Source  
  
-   Change a Password for DB2  
  
#### To Start the Data Access Tool  
  
1. Click the Data Access Tool shortcut in the Host Integration Server program folder.  
  
2. Or click **Start**, **Programs**, **Host Integration Server**, and then click **Data Access Tool**.  
  
   **Data Source Browser, Data Source Folder and Data Source Item**  
  
   The Data Access window is divided into the following three parts:  
  
- A scope pane (folder browser) that offers a tree view of data sources, with separate folders for DB2 and Host Files.  
  
- A results pane (list item details) that offers a list view of data sources, with common details such as platform and date modified.  
  
- A result pane view that displays either the output of a command or current connection string.  
  
  **Menu commands**  
  
  Commands can be accessed through the main menu and context-sensitive menu, which appears when you right-click items displayed in the browser or details panes. For example, when you right-click a data source item, you can view, edit, test, delete, or rename that data source item.. In addition, the **F5** key updates the tree view, the **Delete** key deletes the currently selected item, and the **F1** key opens the online Help.  
  
  **Creating a Data Source**  
  
  To launch the Data Source Wizard, click **New Data Source** from the **File** or context menu.  
  
1. In the Data Access Tool window, click the **File** menu.  
  
2. Click **NewData Source**. The Data Source Wizard appears.  
  
   **Opening a Data Source**  
  
   You can use the **Open Data Source** command on the **File** menu) to select a Universal Data Link (\*.udl) file using the Windows **File Open** dialog box. This command opens the data source for editing within the Data Source Wizard.  
  
3. In the Data Access Tool window, click the **File** menu.  
  
4. Click **Open Data Source.** The **File Open** dialog box appears.  
  
5. Find the data source that you want, and then click **Open**. The Data Source Wizard appears.  
  
   **Importing a Data Source**  
  
   You can use the **Import DB2 Connect File** command (File menu) to import a configuration defined for use with  IBM DB2 Connect.  
  
6. In the Data Source Browser, click the **File** menu.  
  
7. Click **Import**, and then select the file that you want.  
  
8. Click file, and the click **Open** to view item in Data Source Wizard. The Data Source Wizard appears.  
  
   For more information about IBM DB2 Connect files, see the IBM DB2 Connect documentation.  
  
   **Editing a Data Source**  
  
   You can use the Edit Data Source command from the Action or context menu to select a Universal Data Link (*.udl) file. This command opens the data source for editing in the Data Source Wizard.  
  
9. In the Data Source Browser window, click the **Actions** menu.  
  
10. Click **Edit Data Source**. The Data Source Wizard appears.  
  
    **Testing a Connection**  
  
    The **Test Connection** command on the **Action** or context menu enables you to verify the data source, and to display information such as the host platform and version.  
  
    `Successfully connected to data source 'DB2DSN1'.`  
  
    `Server class: DB2/MVS`  
  
    `Server version: 09.01.0005`  
  
    If you did not persist the user name and password into the connection configuration, an **Authentication** dialog box will appear, prompting you to enter a valid user name and password.  
  
    **Running a Sample Query**  
  
    You can use the **Sample Query** command on the **Action** and context menu to execute a sample query against the remote data source. The sample query retrieves a list of tables from the system catalog by using the default schema property configured in the data source.  
  
11. In the Data Source Browser window, select the data source and click the **Actions** menu.  
  
12. Click **Sample Query**. The Output window and Grid window display the results of the sample query  
  
     `Successfully retrieved 1000 rows from data source 'DB2DSN1'.`  
  
    **Creating Packages**  
  
    You can use the **Create Packages** command on the Actions and context menu to create packages on a remote DB2 relational database server.  
  
13. In the Data Source Browser window, select the data source and then click the **Actions** menu.  
  
14. Click **Create Packages**. The Output widow displays the results of the sample query.  
  
    If you did not persist the user name and password into the connection configuration, an Authentication dialog box appears, prompting you to enter a valid user name and password.  
  
    **Displaying a Connection String**  
  
    When you select a data source in the Data Source Browser, the Output pane displays the **Connection String** dialog box. You can copy the connection string from the dialog box and paste it into other applications. You can use this technique in  SQL Server Management Studio to define a Linked Server for use with the Query Processor.  
  
    **Change Password**  
  
    You can replace your current password using **Change Password** command  on the Actions and context menu to access the DB2 password change management (PCM) function.  
  
15. In the Data Source Browser window, select the data source, and then click the **Actions** menu.  
  
16. Click **Change Password**. The Authentication dialog appears.  
  
17. Enter the current credentials in the **User name** and **Password** text boxes.  
  
18. Enter the new password in both the **New password** and **Confirm password** text boxes. The Output window displays the results of the Change Password command.  
  
    `Successfully changed the password on data source 'DB2DSN1'.`  
  
    **Locate**  
  
    The **Locate** command  on the context menu enables you to navigate to a Universal Data Link (*.udl) file using the Windows Explorer dialog box.  
  
    **Options**  
  
    You can use the **Options** dialog on the **View** menu to specify the directory that the Data Access Tool uses to view, edit and save Universal Data Link (*.udl) files.  
  
    **Help**  
  
    You can use the **Help** command on the context menu and **Dynamic Help** on the **Help** menu to load the product documentation to learn more about using the Data Access Tool.  
  
    **Other Tasks**  
  
    In addition to the tasks described in the previous topics, you can also use the **Edit**, **View** and **Help** menus to perform the actions described in the following table.  
  
|||  
|-|-|  
|**Menu**|**Action**|  
|**Edit**|**Undo**, **Cut**, **Copy**, or **Paste** strings, and to **Delete** or **Rename** data sources.|  
|**View**|**Refresh** the browser or view the **Options** dialog box.|  
|**Help**|Access context-sensitive dynamic help, HIS DevCenter (MSDN), HIS TechCenter (TechNet), HIS Forum, HIS Feedback (Connect), and About (version and license).|  
  
## See Also  
 [Data Integration (Configuration)](../core/data-integration-configuration-2.md)