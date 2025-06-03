---
description: "Learn more about: How to Display All Management Pack Rules"
title: "How to Display All Management Pack Rules"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Display All Management Pack Rules
Use the following procedure to display a list of rules for the management packs that you imported. The list of rules can be viewed in Office Excel.  
  
### To display management pack rules  
  
1.  In your management server, click **Programs**, and then click **System Center**.  
  
2.  Click **Command Shell**.  
  
3.  In the Command Shell, type the following command:   
    `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-SCOMRule | export-csv "c:\rules.csv"`  
  
4.  A .csv file is created. You can open the .csv file in Office Excel.  
  
    > [!NOTE]  
    >  In Office Excel, you may be required to specify that the .csv file is a text file.
