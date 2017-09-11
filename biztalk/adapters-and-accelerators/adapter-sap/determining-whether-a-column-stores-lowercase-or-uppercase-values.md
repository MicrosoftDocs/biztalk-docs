---
title: "Determining Whether a Column Stores Lowercase or Uppercase Values | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1edc8332-d8c7-4040-895b-f121fb03df44
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Determining Whether a Column Stores Lowercase or Uppercase Values
This section lists high-level tasks to be performed on the SAP system to determine whether a column in an SAP table stores lowercase or uppercase characters. For detailed instructions on how to perform this task you must contact your SAP administrator or refer to SAP documentation.  
  
### To determine the case of values stored in a column  
  
1.  Start the SAP GUI.  
  
2.  Go to Transaction SE37 and execute DDIF_TABL_GET.  
  
3.  For the NAME parameter, specify the table name containing the column for which you want to determine the character case information. For example, KNA1.  
  
4.  The first table parameter is DD03P_TAB. Click the parameter to see the rows in the table. Every row in this table corresponds to a column in the table (such as KNA1) you specified in step 3.  
  
5.  In DD03P_TAB, look for the value in the LOWERCASE column for each row. If the value in the LOWERCASE column is 'X', the corresponding column in the table (such as KNA1), can store both lowercase and uppercase characters. If the value in the LOWERCASE column is empty, the corresponding column can only store uppercase characters.  
  
     For example, for the NAME row the LOWERCASE column is X. So, the NAME column in KNA1 can store both uppercase and lowercase characters. However, for the LAND1 row the LOWERCASE column is empty. So, the LAND1 column in KNA1 table can only store uppercase characters.  
  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)