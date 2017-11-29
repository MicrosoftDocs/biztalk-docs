---
title: "Side Information for CPI-C Programs1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4717256a-2ce1-4870-ad86-62daa98e87d9
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Side Information for CPI-C Programs
The information required for two Common Programming Interface for Communications (CPI-C) programs to communicate is stored as a table, called the side information table, in memory. The table is derived from the symbolic destination name (configured in Host Integration Server) and from the [Set_CPIC_Side_Information](../Topic/Set_CPIC_Side_Information%20\(CPI-C\)1.md), [Extract_CPIC_Side_Information](../Topic/Extract_CPIC_Side_Information%20\(CPI-C\)2.md), and [Delete_CPIC_Side_Information](../Topic/Delete_CPIC_Side_Information%20\(CPI-C\)1.md) calls.  
  
 The side information is maintained by the system administrator.  
  
 If you are developing commercial programs or programs that will be installed on multiple computers within your organization, it is recommended that you include logic that enables a user or system administrator to specify configuration information for each copy of the program.  
  
 Each side information entry contains the following fields:  
  
 *Symbolic destination name*  
 This is the *sym_dest_name* parameter specified by [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md). It is the identifier for the side information entry. The name can be up to eight ASCII characters. See [Set_CPIC_Side_Information](../Topic/Set_CPIC_Side_Information%20\(CPI-C\)1.md) for the allowed characters.  
  
 *Partner LU name*  
 This is the name by which the partner logical unit (LU) is known to the local program. It can be an alias of up to eight ASCII characters or a fully qualified network name of up to 17 characters. For the allowed characters, see [Set_Partner_LU_Name](../Topic/Set_Partner_LU_Name%20\(CPI-C\)1.md).  
  
 *Partner program type and name*  
 These fields indicate whether the partner program is an application transaction program (TP) or an SNA service TP, and provide the partner program name. An application TP name can contain up to 64 ASCII characters. A service TP name can contain up to four characters. For the allowed characters, see [Set_TP_Name](../Topic/Set_TP_Name%20\(CPI-C\)2.md).  
  
 *Mode name*  
 This name represents a set of characteristics to be used in an LU-to-LU session. The mode name can contain up to eight ASCII characters. For the allowed characters, see [Set_Mode_Name](../Topic/Set_Mode_Name%20\(CPI-C\)1.md).  
  
 *Conversation security type*  
 This field indicates whether security will be used and if so, what type.  
  
 You can use conversation security to require that the invoking program provides a user identifier and password before CPI-C allocates a conversation with the invoked program.  
  
 For an invoked program that in turn invokes another program, the security type can inform the second invoked program that security has already been verified.  
  
 For further information about conversation security, see [Set_Conversation_Security_Type](../Topic/Set_Conversation_Security_Type%20\(CPI-C\)2.md).  
  
 *Security user identifier and password*  
 If you intend to use conversation security, a valid combination of user identifier and password is required to access the invoked program. The user identifier and password can be up to 10 ASCII characters. For information about allowed characters, see [Set_Conversation_Security_User_ID](../Topic/Set_Conversation_Security_User_ID%20\(CPI-C\)2.md) and [Set_Conversation_Security_Password](../Topic/Set_Conversation_Security_Password%20\(CPI-C\)2.md).