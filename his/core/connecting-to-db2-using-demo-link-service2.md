---
title: "Connect to DB2 using Demo Link Service | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 854026b7-f989-4aa4-a9f6-677e3bd4de35
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Connecting to DB2 using Demo Link Service
Host Integration Server includes two off-line demo link connections that enable you to learn how to configure data integration connections to IBM DB2 databases and IBM host file system servers. The demo link connections are based on SNA APPC sessions. The following two topics guide you through using the SNA Manager, Data Access Tool, and Data Source Wizard to sample connectivity to IBM DB2 and host files.  
  
- [Configuring a Demo SNA Connection for DB2](../core/connecting-to-db2-using-demo-link-service2.md#sna)  
  
- [Configuring a Demo Data Source for DB2](../core/connecting-to-db2-using-demo-link-service2.md#ds)  
  
  In these walkthroughs, you will use SNA Manager to configure a demo link service, connection, and logical units to simulate a connection to IBM DB2 for i5/OS. You will use the Data Access Tool and Data Source Wizard to configure and test a data source definition for DB2.  
  
##  <a name="sna"></a> Configuring a Demo SNA Connection for DB2  
  
1.  Click **Start**, **Programs**, **Host Integration Server**, and then click **SNA Manager**.   
     The SNA Manager appears.   
     The SNA Manager window is divided into two parts:  
  
    -   Scope pane (folder browser) that offers a tree view of services such as TN3270 and Print, and configuration objects such as pools and users.  
  
    -   Results pane (list item details) that offers a list view of configurable objects with object-specific details such as status.  
  
2.  Double click the **SNA Subdomain** item in the scope pane, directly below the high-level folder titled “Microsoft SNA Manager”. In a single server subdomain, the SNA Subdomain name is the name of the server.   
     The SNA Manager displays the following set of folders:  
  
    -   Servers  
  
    -   Pools  
  
    -   Configured Users  
  
    -   Workstations  
  
    -   APPC Modes  
  
    -   CPIC Symbolic Names  
  
3.  Double-click the **Servers** folder in the scope pane. One or more named computer server icons are displayed.  
  
4.  Double-click the server that you want to configure. The SNA Manager displays the following set of folders:  
  
    -   Link Services  
  
    -   Active Users  
  
    -   SNA Service [Inactive]  
  
    -   TN3270 Service [Inactive]  
  
    -   Print Service [Inactive]  
  
5.  Right-click the **Link Services** folder, click **New**, and then click **Link Service**. The Insert Link Service dialog box appears.  
  
6.  In the **Select a Link Service to add** list, click **DEMO SDLC Link Service**, and then click **Add**. The DEMO SDLC Link Service #1 Properties appears.  
  
7.  In the **Script File** list, click **DB2 OLE DB Demo**, and then click **OK**.  The Service account credentials dialog appears.  
  
8.  In the **Password** field, type a password, and then click **OK**.  The SNA Manager displays a new Link Service Name in results pane (“SNADEMO1”).  
  
9. In the **Insert Link Service** dialog box, click **Finish**.  
  
10. In the scope pane, double-click the **SNA Service [Inactive]** item.  The SNA Manager displays the following set of folders:  
  
    -   Connections  
  
    -   Local APPC LUs  
  
    -   Remote APPC LUs  
  
11. Right-click the **SNA Service [Inactive]** item, click **All Tasks**, and then click **AS/400 Wizard**.  The AS/400 Configuration Wizard appears.  
  
12. In the **Welcome** dialog box, click **Next**.  The SNA Service dialog appears.  
  
13. In the **SNA Service** dialog box, click the server that you want to configure, and then click **Next**. The Connection dialog appears.  
  
14. In the **Connection** dialog box, type a name for the connection, such as `DRDADEMO`, and then click **Next**.  The Link Service dialog appears.  
  
15. In the **Link Service** dialog box, click the **SNADEMO1** item, and then click **Next**.  The AS/400 Name dialog appears.  
  
16. In the **AS/400 Name**, verify that the **Network name** is **APPN** and the **Control Point Name** is **DRDADEMO**, and then click **Next**.  The Link Identification dialog appears.  
  
17. In the **Link Identification** dialog box, verify that the **PU address (PUADDR)** is **C1**, and then click **Next**.  The Completion dialog appears.  
  
18. In the **Completion** dialog box, click **Finish**. The SNA Manager displays an AS/400 Configuration Wizard confirmation dialog.  
  
19. In the **AS/400 Configuration Wizard** confirmation dialog box, click **OK**.  
  
20. Double-click the **Connections** folder, see the **DRDADEMO** connection.  
  
21. Double-click the **Remote APPC LUs** folder, see the **DRDADEMO** LU.  
  
22. Right-click the **Local APPC LUs** folder, click **New**, and then click **Local LU**. The Local APPC LU Properties dialog appears.  
  
23. In the **Local APPC LU Properties** dialog box, verify that the **Network name** is **APPN**, type **LOCAL** in the **LU alias** and **LU name** fields, and then click **OK**.  
  
24. Double-click the **Local APPC LUs** folder, see the **LOCAL** LU.  
  
25. Click the **Action** menu, and then click **Save configuration**.  
  
26. In the scope pane, right-click the **SNA Service [Inactive]** item, and then click **Start**.  The SNA Manager displays the status of the SNA Service [Active] and DRDADEMO [On Demand] connection.  
  
27. In the scope pane, verify that the status of the **SNA Service** is active (**SNA Service [Active]**) and that the **DRDADEMO** connection is ready (**DRDADEMO [On Demand]**).  
  
##  <a name="ds"></a> Configuring a Demo Data Source for DB2  
  
1. Click **Start**, **Programs**, **Host Integration Server**, and then click **Data Access Tool**. The Data Access Tool appears.  
  
2. Click **File**, and then click **New Data Source**.  The Data Source Wizard appears.  
  
3. In the **Welcome** dialog box, click **Next**.  The Data Source dialog appears.  
  
4. In the **Data source platform** list, click **DB2/400**. For **Network Transport Library**, select SNA **LU6.2 (APPC)**, and then click **Next**.  The APPC Network Connection dialog appears.  
  
5. In the **LOCAL LU alias** list, select **LOCAL**. In the **Remote LU alias** list, select **DRDADEMO**. In the **Mode name** list, select **QPCSUPP**, and then click **Next**.  The DB2 Database dialog appears.  
  
6. In the **Initial Catalog** field, type `OLYMPIA`. In the **Package collection** field type, `PUBS`. In the Default schema field, type `PUBS`, and then click **Next**.  The Locale dialog appears.  
  
7. In the **Host CCSID** list, verify that **EBCDIC – U.S./Canada [37]** is selected. In the **PC code page** list, verify that **ANSI – Latin I [1252]** is selected, and then click **Next**.  The Security dialog appears.  
  
8. In the **Security method** list, verify that **Interactive sign-on** is selected. In the **User name** field, type **SNA**. In the **Password** and **Password confirmation** fields, type **SNA**, and then click **Save password**.  The Data Access Wizard displays a Warning dialog.  
  
9. In the **Warning** dialog box, click **Yes**, and then in the **Security** dialog click **Next**.  The Advanced Options dialog appears.  
  
10. In the **Alternate TP name** field, type **0X07F9F9F9**, and then click **Next**.  The All Properties dialog appears.  
  
11. In the **All Properties** dialog box, click **Next**.  The Validation dialog appears.  
  
12. Click the **Connect** button. In the Output pane, see the results. Click the **Sample Query** button. In the **Grid** pane, see the results, and then click **Next**.  The Saving Information dialog appears.  
  
13. In the **Data source name** field, type **DRDADEMO**. For the **OLE DB or Managed** choice, select **Universal data link**, and then click **Next**.  The Completion dialog appears.  
  
14. Click **Finish**.  The Data Access Tool displays the DRDADEMO connection in the DB2 OLE DB UDLs folder.  
  
    The Data Integration Samples in the SDK include a pre-configured UDL file for use with the DRDADEMO demo link service and connection. See C:\Program Files\\Host Integration Server\SDK\Samples\DataIntegration\DRDADEMO.UDL.  
  
## See Also  
 [Data Integration (Configuration)](../core/data-integration-configuration-2.md)   