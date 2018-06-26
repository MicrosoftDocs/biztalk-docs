---
title: "Run the Migration Utility | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d17de9db-0f58-43eb-b5d6-b3d1f2400bd9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Run the Migration Utility
You can migrate your existing host security data into the new Single Sign-On (SSO) environment by using the hissomig.exe command-line utility. Migration is essentially a two-step process:  
  
1. First, the tool **exports** data from the host security domain into an XML file. This file also contains validation data for the migration process. If mappings or file names conflict, an administrator can resolve them before the next step.  
  
2. Second, the tool **imports** data into the Single Sign-On (SSO) environment, and updates the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] credential database appropriately.  
  
   The Migration Utility has the following restrictions:  
  
-   You must be an SSO administrator and have at least read privileges to the SNAUDB database to perform migration.  
  
-   Both importing and exporting must be done on the master secret server.  
  
> [!NOTE]
>  The XML file that is generated during migration is not deleted. Because this file contains security data, it is important that you manually delete the file as soon as migration is finished.  
  
### To export from Host Integration Server  
  
1.  Stop the Host Account Cache service.  
  
2.  Click **Start**, click **Run**, and then type `cmd` and press Enter.  
  
3.  Type `hissomig –export –servername <server> -output <XML file>` where *\<server>* is the fully qualified name, NetBIOS name, or IP address of the Host Integration Server primary domain controller, and *\<XML file>* is the full path of the XML file to which the data will be exported.  
  
     For example:  
  
     `hissomig –export –servername SERVER1 -output c:\hostsecdb.xml`  
  
4.  Press Enter.  
  
5.  Restart the Host Account Cache service.  
  
### To export from SNA Server 4.0  
  
1.  Stop the Host Account Cache service.  
  
2.  Click **Start**, click **Run**, and then type `cmd` and press Enter.  
  
3.  Type `hisssomig –export –dbfile <database file> -output <XML file>` where *\<database file>* is the full path of the SNA 4.0 Host Security database file, and *\<XML file>* is the full path of the XML file to which the data will be exported.  
  
     For example:  
  
     `hisssomig –export –dbfile Y:\Program Files\SNA Server\hostsec\dbfile.dbs -output c:\hostsecdb.xml`  
  
4.  Press Enter.  
  
5.  Restart the Host Account Cache service.  
  
### To import into Host Integration Server  
  
1. Click **Start**, click **Run**, and then type `cmd` and press Enter.  
  
2. Type `hisssomig –import –key <key> -input <XML file>` where *\<key>* is the full path of the file that contains the encryption key, and *\<XML file>* is the full path of the XML file from which the data will be imported.  
  
    For example:  
  
    `hisssomig –import –key Z:\hostseckey.bak -input c:\hostsecdb.xml`  
  
3. Press Enter.  
  
   **Other commands for Migration Utility**  
  
   The following is a list of commands for the Migration Utility. These commands are also displayed during migration if you attempt to run the utility with incorrect data.  
  
|Command|Comment|  
|-------------|-------------|  
|-servername|Name of server that holds the Host Integration Server Host Security primary host account cache database.|  
|-dbfile|Full path of the SNA 4.0 Host Security database file.|  
|-key|Full path of the file that contains the encryption key.|  
|-username|User name that is used for encryption.|  
|-password|Password for the user name that is used for encryption.|  
|-output|Full path of the XML file to which the data will be exported.|  
|-input|Full path of the XML file from which the data will be imported.|  
|-log|Creates migration log in the directory specified. For example: `-log c:SSO\log`|  
  
## See Also  
 [Upgrading from Host Integration Server 2000 or SNA Server 4.0](../esso/upgrading-from-host-integration-server-2000-or-sna-server-4-0.md)