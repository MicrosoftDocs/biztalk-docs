---
title: "Connect to the Oracle Database Using Windows Authentication | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b42a1b-1105-4278-bf8a-62cf0cffb08f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to the Oracle Database Using Windows Authentication
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables adapter clients to use Windows Authentication to establish a connection with the Oracle database. To use Windows Authentication, the adapter clients must specify “/” for user name and leave the password blank. For more information about connecting to the Oracle database using Windows Authentication, see [Connect to Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).  
  
 To enable adapter clients to use Windows Authentication to connect to an Oracle database, you must perform the following tasks on the computer running the Oracle database.  
  
1. Make sure that the `sqlnet.ora` file on both the client and the server, available under `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, has the following entry:  
  
   ```  
   SQLNET.AUTHENTICATION_SERVICES= (NTS)  
   ```  
  
2. Connect to the Oracle database as SYSDBA.  
  
3. Create the Windows user as an external user in the Oracle database. Note that the user name must be in upper case.  
  
   ```  
   CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
   ```  
  
4. Grant privileges to the user.  
  
   ```  
   GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
   ```  
  
5. To enable the newly created user, logging in using Windows Authentication, to access the Oracle database artifacts, you can change the user’s schema to the SCOTT schema. You can add the following SQL command to the logon script that changes the user’s default schema to SCOTT when the user logs on.  
  
   ```  
   alter session set current_schema=SCOTT;  
   ```  
  
6. Even though you changed the schema of the user to the SCOTT schema, you will still not be able to see the Oracle database artifacts while browsing and generating metadata using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. This is because the newly created user does not have permissions for the SCOTT schema. Make sure you provided permission for the SCOTT schema to the newly created user.  
  
## See Also  
 [Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)   
[Create a connection to the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)