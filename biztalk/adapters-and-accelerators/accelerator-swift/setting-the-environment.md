---
description: "Learn more about: Setting the Environment"
title: "Setting the Environment"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Setting the Environment
**To set the environment:**  
  
1.  Make sure SWIFT Message Pack is configured. Refer to the Swift Message Pack documentation to configure the same.  
  
2.  Run the SQL script *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql. Change the database name in the sql script if the Swift and MessagePack are configured for database name other than A4Swift.  
  
3.  Set the value of Key “datasource” as ComputerName and key “database” as database name (for which the Swift and MessagePack is configured) in the file *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\DataImport.exe.config.  
  
    > [!NOTE]
    >  The data input file should not be in the same folder as the DataImport.exe file.  
  
4.  Run the DataImport utility to import data in BICplusIBAN and SEPA tables.
