---
title: "FILLER for Discontiguous Output Area and Return Value2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60d0f112-18cc-49b5-a85c-905b80fd2b30
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FILLER for Discontiguous Output Area and Return Value
If the return value is discontiguous from the output area, you must calculate and manually specify the filler between the return value and the output area.  
  
 The following example shows the calculation for the filler from the original COBOL that goes into the Import Wizard (the byte counts on the right are added as an illustration):  
  
```  
01  OUTPUT-AREA.  
           05  SELECTED-OUTPUT-AREA.  
               10  FIELD1                       PIC S9(4)       COMP.     [2 Bytes]  
               10  FIELD2                       PIC S9(9)       COMP.     [4 Bytes]  
           05  DISCONTIG-UNSELECTED-AREA.  
               10  NOTSELECTED                  PIC X(10).                 [10 Bytes]  
               10  ALSO-NOTSELECTED             PIC S9(9)       COMP.     [4 Bytes]  
           05  RETVAL                           PIC S9(9)       COMP.     [4 Bytes]  
  
```  
  
 In this case, because the return value follows the output area, filler must be added to the last output parameter. To do this, perform the following steps.  
  
1. Unlock the method.  
  
2. In the details pane, click **FIELD2**.  
  
3. On the **File** menu, click **Properties**, and then click the **COBOL Definition** tab.  
  
4. In the **From Host** box, type 14 as the trailing filler.  
  
5. Click **OK**.  
  
   To verify your modified code, in **TI Project**, use the **Export** command on the **File** menu. You can then see your code in Notepad.  
  
   The following is the output with the added filler:  
  
```  
01  DISCONTIGCBL-OUTPUT-AREA.  
    05  LL                               PIC S9(4) COMP.         OUTPUT     [2 Bytes]  
    05  ZZ                               PIC S9(4) COMP.         OUTPUT     [2 Bytes]  
    05  FIELD1                           PIC S9(4) COMP.         OUTPUT     [2 Bytes]  
    05  FIELD2                           PIC S9(9) COMP.         OUTPUT     [4 Bytes]  
  
    05  RETVAL                           PIC S9(9) COMP.         OUTPUT     [4 Bytes]  
  
```  
  
## See Also  
 [Filler](../core/filler1.md)