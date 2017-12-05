---
title: "Step 1: Configuring a Connection to DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c46cc31-1c78-4151-b18b-03699cb767f1
caps.latest.revision: 4
---
# Step 1: Configuring a Connection to DB2
The first step you need to perform is to create and configure a connection string to your DB2 data source. Once you are finished creating the string, you will use the string to create an XML web service.  
  
### To create the connection string  
  
1.  Start the Data Access Tool by clicking on **Start**, then **Programs**, then **Microsoft Host Integration Server**, and then click **Data Access Tool**.  
  
2.  On the Data Access Tool, click **File**, select **New**, click **Data Source…**, and then click **Next**.  
  
3.  On the Data Source page, select your data source platform and network type, and then click **Next**.  
  
     For the purpose of this tutorial, we will select DB2/MVS from **Data source platform**, and TCP/IP as a **Network type**.  
  
4.  On the TCP/IP Network Connection page, enter the IP address or alias of your DB2 source into the **Address or alias** field, and enter the port number of your DB2 source into the **Port** field.  
  
5.  Ensure the **Distributed Transactions** box is unchecked, and then click **Next**.  
  
6.  On the DB2 Database page, fill in the **Initial Catalog**, **Package collection**, **Default schema**, and **Default qualifier** fields with the information relevant to your database, and then click **Next**.  
  
7.  On the Locale page, confirm that the locales are correct for your system, and then click **Next**.  
  
8.  On the Security page, select Interactive Sign-On from the **Security Method** drop-down box, enter your user name and password in the **Properties** fields, and then click **Next**.  
  
9. On the Advanced Options page, confirm that no options are checked, and then click **Next**.  
  
10. On the Validation page, click **Connect** to connect to your database using the information you provided, and click **Sample Query** to send a sample query to your DB2 database.  
  
     Once you confirm that your information is correct, click **Next**.  
  
11. On the Saving Information page, check the **Initialization string file** box, enter a data source name in the **Data source name** field, and then click **Next**.  
  
12. On the Completing the Data Source Wizard, click **Finish**.  
  
### To view the connection string  
  
1.  Click **Start**, and then click **Run…**.  
  
2.  In the **Run** dialog, type `Notepad` in the **Open:** field, and then click **OK**.  
  
3.  In Notepad, click **File**, and then click **Open…**.  
  
4.  Use the Open dialog to browse to the .txt file that contains the connection string information for the data source.  
  
     For this tutorial, the file name is HIS_TRAINING.txt, and is located in c:\Documents and Settings\username\My Documents\Host Integration Projects\Data Sources.  
  
## See Also  
 [Step 2: Creating an XML Web Service](../core/step-2-creating-an-xml-web-service.md)   
 [Managed Provider for DB2 Tutorial](../core/managed-provider-for-db2-tutorial.md)