---
title: "Install Custom RFCs for the Data Provider for SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation, custom RFCs for the Data Provider for SAP"
  - "installing, custom RFCs for the Data Provider for SAP"
  - "installing custom RFCs, how to"
ms.assetid: 7a99db70-fa5a-4c04-9dc7-b71613d4364e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install Custom RFCs for the Data Provider for SAP
Install the custom RFCs if you want to use the .NET Framework Data Provider for mySAP Business Suite to access the SAP system.

The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires custom RFCs to perform some operations on the SAP system to:
  
- Run the SELECT operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXTRACT_DATA_OO RFC.  
  
- Run the EXECQUERY operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXECUTE_SAP_QUERY RFC.  
  
To perform these operations on the SAP system, you must install these custom RFCs on the SAP system. If you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] along with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the Setup program copies the RFC transport for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as a compressed file (customRFC.zip) on the system where you install the adapter. The zip file is typically installed at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft .NET Framework Data Provider for mySAP Business Suite*. 
  
 After extracting the zip file, you will find four data files, two following the naming pattern K9*.BI1 (for example, similar to K900534.BI1), and the other two following the pattern R9\*.BI1 (for example, similar to R900534.BI1).  
  

  
1. Copy the extracted files from the computer running the adapters to the SAP application server.  
  
   1.  Log in as the SAP R/3 system administrator to the SAP application server of your development system.  
  
   2.  Copy the two transport files with the naming pattern K9*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:  
  
        `<drive>:\usr\sap\trans\cofiles`  
  
   3.  Copy the two transport files with the naming pattern R9*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:  
  
        `<drive>:\usr\sap\trans\data`  
  
2. Load the transport into the transport buffer on the SAP application server.  
  
   1.  At the command prompt, navigate to the transport program directory on the SAP application server:  
  
        `<drive>:\usr\sap\trans\bin`  
  
   2.  To load the transport into the transport buffer, execute the following command at the `\usr\sap\trans\bin` directory and replace *sysid* with the system ID of your development system:  
  
       ```  
       tp addtobuffer <TransportNumber> <sysid> pf=TP_DOMAIN_<sysid>.PFL  
       ```  
  
        where, *TransportNumber* is the actual transport number (for example BI1K900534).  
  
   3.  After the `tp` command finishes, you will see a report similar to the following:  
  
       ```  
       This is tp version 320.56.66 (release 620)  
       Addtobuffer successful for TransportNumber  
       tp finished with return code: 0  
       ```  
  
        Return code "0" means that the operation succeeded.  
  
        A return code of 0 or 4 is acceptable. Contact Microsoft Customer Service and Support, if you receive a return code of 8 or above.  
  
       > [!IMPORTANT]
       >  Repeat steps (b) and (c) for the second set of transport files.  
  
       > [!NOTE]
       >  You can easily derive the actual transport number from the cofile file name. For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.  
  
3. Import the transport into SAP.  
  
   1.  Execute the following command at the command prompt:  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL  
       ```  
  
        Replace *sysid* with the system ID of your development system. Replace *clientnumber* with the client number of your development system.  
  
        You can use the U2 parameter to overwrite previously installed objects, as follows:  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> U2  
       ```  
  
        or  
  
       ```  
       tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL U2  
       ```  
  
       > [!NOTE]
       >  You can easily derive the actual transport number from the cofile file name. For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.  
  
   2.  After the `tp` command finishes, you will see a report similar to the following:  
  
       ```  
       This is tp version 320.56.66 (release 620)  
       This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
       R3trans.exe finished (0000).  
       This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
       R3trans.exe finished (0000).  
       tp finished with return code: 0  
       ```  
  
        Return code "0" means that the operation succeeded.  
  
        A return code of 0 or 4 is acceptable. Contact Microsoft Customer Service and Support if you receive a return code of 8 or above.  
  
       > [!IMPORTANT]
       >  Repeat steps (a) and (b) for the second set of transport files.  
  
4. Check the transport log.  
  
5. Check the transport log in SAP GUI Transport Organizer using transaction SE09 to verify that there are no errors.  
  
   Setting User Authorization  
   The Z_EXTRACT_DATA_OO RFC requires user IDs with specific authorization objects. Use the SAP GUI authorization administration tools to set the minimum restrictions on the execution of the RFC:  
  
> [!NOTE]
>  You do not need to set the authorization for the Z_EXECUTE_SAP_QUERY RFC.  
  
- Z_EXTRACT_DATA_OO requires both S_TABU_DIS and Z_EIP_TABL. The following values provide the minimum restrictions for S_TABU_DIS, which allow users to view metadata for any table in the system.  
  
  - ACTVT: 03  
  
  - DICBERCLS: *  
  
    You can use DICBERCLS to restrict authorization to tables by authorization class.  
  
    You can use the TDDAT table to view the authorization class for tables.  
  
  > [!NOTE]
  >  To prevent changes to tables by table maintenance transactions, you should only grant display privileges in a production environment (ACTVT: 03 sets the permissible activity to display).  
  
   The minimum values for Z_EIP_TABL are:  
  
  - ACTVT: 03  
  
  - TABLE: *  
  
    You can use TABLE to explicitly define the authorized tables. Note, too, that S_TABU_DIS is also used in other transactions.  
  
##### To set user authorization  
  
1.  Start the SAP GUI. Go to T-code, type `pfcg`, and press ENTER.  
  
2.  In the **Role** text box, enter a role name you want to create, for example, `ZTEST`, and then click **Role**.  
  
3.  In the **Create Role** page, click the **Authorizations** tab.  
  
     If prompted to save the role, click **Yes**.  
  
4.  In the **Change Roles** page, click the **Change Authorization Data** button.  
  
5.  If you are prompted to select a template from the **Choose Template** dialog box, click **Do not select templates**.  
  
6.  In the **Change role: Authorizations** page, click the **Manually** button.  
  
7.  In the **Manual selection of authorizations** box, enter the name of the authorization object `Z_EIP_TABL` and press ENTER.  
  
8.  In the **Change role: Authorizations** page, expand the nodes until you see the text boxes for **Activity** and **Table Name**. For the **Activity** text box, enter the value `03`. For the **Table Name** text box, enter the value `*`.  
  
9. Click the **Save** button to generate the profile.  
  
10. Go back to the **Change Roles** page and click the **User** tab.  
  
11. In the **User** tab, assign a user ID for the role by entering the user name in the **User ID** column, and click the **User comparison** button.  
  
12. In the **Compare Role User Master Record**, click **Complete comparison** to update the master record. When prompted to save the role, click **Yes**.  
  
13. Save and exit.  
  
Verifying Custom RFC Installation  
 After you install the custom RFCs, you can verify whether the RFCs installed correctly.  
  
- For Z_EXECUTE_SAP_QUERY RFC, you can do so by executing a pre-defined query in SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
- For Z_EXTRACT_DATA_OO RFC, you can do so by performing the following tests to confirm that the RFC operates and is ready for use in your system.  
  
##### To test the installation of Z_EXTRACT_DATA_OO  
  
1.  In the SAP GUI authorization administration tools, execute SE37, function module Z_EXTRACT_DATA_OO, and then run the RFC in test mode by pressing `F8`. Populate the parameters as follows.  
  
    |||  
    |-|-|  
    |IN_METADATA_ONLY||  
    |IN_METADATA_LANGUAGE|EN|  
    |IN_FROM_TABLE|T000|  
    |IN_OUTPUT_MODE|S|  
    |IN_OUTPUT_FILENAME||  
    |IN_USE_FIELD_EXITS|X|  
    |IN_SET_ROWCOUNT|0|  
    |IN_DELIMITER||  
    |IN_PACKET_SIZE|50,000|  
    |IN_MAX_WRITE_ATTEMPTS|4|  
    |IN_RETRY_DELAY|30|  
    |IN_SQL_DATES_ON||  
  
2.  Click **Execute** or press `F8`.  
  
3.  In the results pane, check the following.  
  
    |||  
    |-|-|  
    |OUT_TABLEHEADER|\<T000 general metadata\>|  
    |OUT_TECHNICALSETTINGS|\<T000 technical database level metadata\>|  
    |OUT_RECORDLENGTH|\<depends on SAP version\>|  
    |OUT_RECORDCOUNT|\<confirm the number of clients in your system with SE16 on T000\>|  
    |OUT_ZDATATABLE|\<confirm this result with the source data using SE 16 on T000\>|  
    |OUT_RETURN_TAB|S 001 Success|  
  
## Remove the RFC for the Data Provider for SAP  
  
1.  In the SAP GUI Object Navigator (SE80), find all the objects with the ZMSBI development class.  
  
2.  Delete all objects with the ZMSBI development class from the following Dictionary Objects folders:  
  
    -   Structures  
  
    -   Function Groups  
  
    -   Authorized Object  
  
3.  Raise a transport, and migrate it through each system where you installed an RFC (development, test, and production systems, for example).  
  
     For further assistance, contact your SAP Basis Administrator.  
     
## Next
[Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)  
[SAP Adapter Tutorials](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)