---
description: "Learn more about: Configuring Microsoft Client Connections"
title: "Configuring Microsoft Client Connections | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3825609-8836-4f88-bb9e-81369e4fc0b4
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring Microsoft Client Connections
### Connect Microsoft Client to DRDA Service  
 You can connect the Microsoft Client for DB2 to the DRDA Service directly, to test the DRDA Service configuration.  
  
1.  On the **Start** menu, point to **All Programs**, point to **Microsoft Host Integration Server 2010**, and click **Data Access Tool**. When prompted by **User Access Control**, click **Yes**.  
  
2.  In the **Data Access Tool**, click the **Data Sources**, click the **File** menu, and then click **New Data Source**.  
  
3.  In the **Welcome** dialog of the **Data Source Wizard**, click **Next**.  
  
4.  In the **Data Source** dialog, select **DB2/NT** in the **Data source platform** list, select **TCP/IP**, and click **Next**.  
  
5.  In **TCP/IP Network Connection** dialog, enter an **Address or alias** (e.g. “**127.0.0.1**”), enter a Port (e.g. “**446**”), and then click **Next**.  
  
6.  In the **DB2 Database** dialog, enter an **Initial Catalog** (e.g. “**NWIND**”), **Package collection** (e.g. “**dbo**”, **Default schema** (e.g. “**dbo**”, **Default qualifier** (e.g. “**dbo**”, and then click **Next**.  
  
7.  In the **Locale** dialog, select the **Host CCSID** (e.g. “**Unicode – UTF8 [1208]”) and PC code page** (e.g. “**Unicode – UTF8 [1208]**”), and then click Next.  
  
8.  In the **Security** dialog, select **Interactive Sign-On** from the **Security** method list, enter “**HISDEMO**“ in the **User name**, **Password**, and **Password confirmation** fields, and then click **Next** to continue.  
  
9. In the **Advanced Options** dialog, optionally select **Connection pooling**, and then click **Next**.  
  
10. In the **All Properties** dialog, optionally verify the properties in the list, and then click **Next**.  
  
11. In the **Validation** dialog, click **Connect**, and then verify the **Output** of the test connection.  
  
    ```  
    Successfully connected to data source 'DB2_IP_DRDA_AS_NWIND'.  
    Server class: DB2/NT  
    Server version: 09.07.0000  
    ```  
  
12. In the **Validation** dialog, optionally click **Packages**, and then verify the **Output** of the create package process. When prompted by the Warning dialog, click Continue.  
  
    > [!NOTE]
    >  The Packages operation will succeed, however the DRDA Service does not create the corresponding SQL Server stored procedures for these Microsoft Client packages. See DRDA Service operations topic describing use of IgnoreStandardPackages.txt file.  
  
13. In the **Validation** dialog, optionally click **Sample Query**, and then verify the results in the **Grid**, and then click **Next**.  
  
    > [!NOTE]
    >  The Sample Query operation will fail unless you’ve defined a SQL Server view that is compatible with the IBM DB2 SYSCAT.TABLES catalog view.  
  
14. In the **Saving Information** dialog, enter a **Data source name** (e.g. “DB2_IP_DRDAAS_NWIND”), click **Universal data link** and **Initialization string file**, and then click **Next**.  
  
15. In the **Completing the Data Source Wizard** dialog, review what you have accomplished, and then click **Finish**.  
  
16. In the **Data Access Tool**, click the newly-created DB2 OLE DB UDL (e.g. “DB2_IP_DRDA_AS_NWIND”), to view the Connection String.  
  
    ```  
    Provider=DB2OLEDB;User ID=HISDEMO;Password=HISDEMO;Initial Catalog=NWIND;Network Transport Library=TCPIP;Host CCSID=1208;PC Code Page=1208;Network Address=127.0.0.1;Network Port=446;Package Collection=dbo;Default Schema=dbo;Process Binary as Character=False;Units of Work=RUW;Default Qualifier=dbo;DBMS Platform=DB2/NT;Use Early Metadata=False;Defer Prepare=False;DateTime As Char=False;Rowset Cache Size=0;Datetime As Date=False;AutoCommit=False;Authentication=Server;Persist Security Info=True;Data Source=DB2ADMIN;Cache Authentication=False;Connection Pooling=False;Derive Parameters=False;  
    ```  
  
     Data Access Tool connection string.
