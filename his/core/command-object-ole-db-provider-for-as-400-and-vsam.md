---
title: "Command Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 891f4a43-88d8-4997-8d63-ccd138cf1004
caps.latest.revision: 3
---
# Command Object (OLE DB Provider for AS-400 and VSAM)
The **Command** object is created by an OLE DB consumer, or by a service provider on behalf of a consumer. A **Command** object is used to execute a distributed data management (DDM)-specific command on a remote DDM server. The **Command** object currently supports executing Command Language commands on AS/400 DDM servers.  
  
 It is important not to confuse a command, which is an OLE COM object, and its command text, which is a string. Commands are generally used for data definition, such as creating a table or granting privileges, and data manipulation, such as updating or deleting rows. A special case of data manipulation using the **Command** object is opening a rowset (a table).  
  
 Before a consumer can use a command, it must determine if commands are supported. To do this, the consumer calls **QueryInterface** for **IDBCreateCommand** on a session. If this interface is exposed, the provider supports commands. To create a command, the consumer then calls **IDBCreateCommand::CreateCommand** on the session. A single session can be used to create multiple commands.  
  
 When the command is first created, it does not contain a command text. The consumer sets the command text with **ICommandText::SetCommandText**. Because the text command syntax is provider-specific, the consumer passes the globally unique identifier (GUID) of the syntax to use. For use with Microsoft OLE DB Provider for AS/400 and VSAM, the GUID is DBGUID_DBSQL. Note that under OLE DB Provider for AS/400 and VSAM, this GUID does not signify that the text command is a superset of ANSI SQL. The level at which the provider supports ANSI SQL is specified by the DBPROP_SQLSUPPORT property. This property is a bitmask specifying the level of support for SQL. OLE DB Provider for AS/400 and VSAM sets this property to DBPROPVAL_SQL_NONE, indicating that SQL is not supported.  
  
 The syntax supported by OLE DB Provider for AS/400 and VSAM for command text is as follows:  
  
```  
EXEC COMMAND DDMCmd  
```  
  
 where *DDMCmd* represents a valid OS/400 control language (CL) command. Note that only OS/400 CL commands are supported. These commands enable you to request functions from the OS/400 operating system. Some examples are the Delete File (DLTF) or Display File Description DSPFFD) commands. These are the same commands that could be issued at the command prompt if you were connected to an AS/400 through a 5250 terminal session. For a detailed list of possible commands, see the OS/400 CL reference for your platform.  
  
 The syntax supported by OLE DB Provider for AS/400 and VSAM to open a rowset (table) using command text is as follows:  
  
```  
EXEC OPEN FileName  
```  
  
 where *FileName* represents one of the following host file naming conventions listed in the following table.  
  
|Host file type|File naming convention|  
|--------------------|----------------------------|  
|VSAM Data Sets|DATASETNAME.FILENAME|  
|Partitioned Data Sets|DATASETNAME.FILENAME(MEMBER)|  
|OS/400 Files|LIBRARY/FILE|  
|OS/400 Files|LIBRARY/FILENAME|  
|OS/400 File Members|LIBRARY/FILE(MEMBER)|  
|OS/400 File Members|LIBRARY.FILENAME(MEMBER)|  
  
 Note that if a member of a library contains a dot in the member name, the member name must be surrounded by double quotes. For example, if the member name is NAMES.DAT, the proper syntax used to open a rowset using command text is as follows:  
  
```  
EXEC OPEN LIBRARY/FILE("NAMES.DAT")  
```  
  
 To execute the command, the consumer calls **ICommand::Execute**. If the command text specifies the command to open a rowset, (an **EXEC OPEN** command), **Execute** instantiates the rowset and returns an interface pointer to it.  
  
 The following interfaces of the **Command** object are supported by the current version of OLE DB Provider for AS/400 and VSAM:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **IConvertType**  
  
-   **ISupportErrorInfo**