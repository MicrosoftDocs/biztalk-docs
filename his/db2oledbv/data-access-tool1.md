---
title: "Data Access Tool1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b86aae88-0f9d-44f9-a625-98bc1bd01dd7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Access Tool
The Data Access Tool enables administrators and developers to be more efficient when they define and test connections to remote IBM DB2 database servers. The Data Access Tool displays configured data sources in a scope and results pane, similar to Windows Explorer. The Data Access Tool offers an intuitive Data Source Wizard, which guides you through the process of defining, test-verifying, and storing connection information. The Data Access Tool simplifies configuring network, security and database information and helps you create packages on the DB2 system. You can use it to test connections, run sample queries and convert data sources.  
  
## Data Access Tool User Interface  
  
### Data Access Tool windows  
 The Data Access Tool lets you configure and manage your data sources. The tool is divided into three windows:  
  
-   A scope pane (folder browser) that offers a tree view of data sources, with separate folders for data source type.  
  
-   A results pane (list item details) that offers a list view of data sources, with common details such as platform and date modified.  
  
-   A result pane view that displays either the output of a command or current connection string.  
  
### Menu commands and toolbar  
 Commands can be accessed through the main menu and a context-sensitive menu which appears when you right-click any section of a window. For example, when you right-click a data source item, you can view, edit, test, delete, or rename that data source item. In addition, the **F5** key updates the tree view, the **Delete** key deletes the currently selected item, and the **F1** key opens the online Help.  
  
## Data Access Tool Common Tasks  
  
### Creating a Data Source  
 To launch the Data Source Wizard, click **New Data Source** from the **File** or context menu.  
  
1.  In the Data Access Tool window, click the **File** menu.  
  
2.  Click **New Data Source**.  
  
### Opening a Data Source  
 You can use the Open Data Source command on the File menu) to select a Universal Data Link (*.udl) file using the Windows File Open dialog box. This command opens the data source for editing within the Data Source Wizard.  
  
1.  In the Data Access Tool window, click the **File** menu.  
  
2.  Click **Open Data Source**. The File Open dialog box appears.  
  
3.  Find the data source that you want, and then click **Open**. The Data Source Wizard appears.  
  
### Editing a Data Source  
 You can use the Edit Data Source command from the Actions or context menu to select a Universal Data Link (*.udl) file. This command opens the data source for editing in the Data Source Wizard.  
  
1.  In the Data Source Browser window, click the **Actions** menu.  
  
2.  Click **Edit Data Source**. The Data Source Wizard will appear.  
  
### Testing a Connection  
 The **Test Connection** command on the **Actions** or context menu enables you to verify the data source, and to display information such as the host platform and version. Output from testing a connection to a DB2 server resembles the following.  
  
 Successfully connected to data source 'DB2DSN1'  
  
 Server class: DB2/MVS  
  
 Server version: 10.01.0005  
  
 If you did not save the user name and password in the connection configuration, an **Authentication** dialog box will appear, prompting you to enter a valid user name and password.  
  
### Running a Sample Query  
 You can use the **Sample Query** command on the **Actions** and context menu to execute a sample query against the remote data source. The sample query retrieves a list of tables from the system catalog by using the default schema property configured in the data source. The data is displayed in the results pane as two tabs: an **Output** window.  
  
1. In the Data Source Browser window, select the data source and click the **Actions** menu.  
  
2. Click **Sample Query**. The **Output** window and **Grid** window display the results of the sample query.  
  
   Successfully retrieved 1000 rows from data source 'DB2DSN1'.  
  
### Creating Packages  
 You can use the **Create Packages** command on the Actions and context menu to create packages on a remote DB2 relational database server.  
  
1. In the Data Source Browser window, click the **Actions** menu.  
  
2. Click Create Packages. The Create Packages dialog box will appear.  
  
   If you did not save the user name and password in the connection configuration, an Authentication dialog box appears, prompting you to enter a valid user name and password.  
  
### Displaying a Connection String  
 When you select a data source in the Data Source Browser, the Output pane displays the Connection String dialog box. You can copy the connection string from the dialog box and paste it into other applications. You can use this technique in SQL Server Management Studio to define a Linked Server for use with the Query Processor.  
  
### Changing a Password  
 You can replace your current password using **Change Password** command on the Actions and context menu to access the DB2 password change management (PCM) function.  
  
1. In the Data Source Browser window, select the data source, and then click the Actions menu.  
  
2. Click **Change Password**. The Authentication dialog appears.  
  
3. Enter the current credentials in the **User name** and **Password** text boxes.  
  
4. Enter the new password in both the **New password** and **Confirm password** text boxes. The Output window displays the results of the Change Password command.  
  
   Successfully changed the password on data source 'DB2DSN1'.  
  
### Locating a Connection Definition  
 The Locate command on the context menu enables you to navigate to a Universal Data Link (*.udl) file using the Windows Explorer dialog box.  
  
### Setting Options  
 You can use the Options dialog on the View menu to specify the directory that the Data Access Tool uses to view, edit and save Universal Data Link (*.udl) files. Also, you can use the Options dialog to 
 
    
  
### Obtaining Help  
 You can use the Help command on the context menu and Dynamic Help on the Help menu to load the product documentation to learn more about using the Data Access Tool.  
  
### Completing Other Tasks  
 In addition to the tasks described in the previous topics, you can also use the Edit, View and Help menus to perform the following actions.  
  
1.  Use the **Edit** menu to **Undo**, **Cut**, **Copy**, or **Paste** strings, and to **Delete** or **Rename** data sources.  
  
2.  Use the **View** menu to **Refresh** the browser or view the **Options** dialog box.  
  
3.  Use the **Help** menu to access context-sensitive dynamic help, HIS DevCenter (MSDN), HIS TechCenter (TechNet), HIS Forum, HIS Feedback (Connect), and About (version and license).