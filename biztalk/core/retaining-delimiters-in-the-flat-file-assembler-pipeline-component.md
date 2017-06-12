---
title: "Retaining Delimiters in the Flat File Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adc27561-9996-49a9-b715-e313b9148506
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Retaining Delimiters in the Flat File Assembler Pipeline Component
If there are missing records in the message going through a custom pipeline that uses the Flat File Assembler, the delimiter for those records may or may not appear in the flat file output depending on where in the input file the records are missing.  
  
 To ensure that the flat file retain certain delimiters, you can use a map and a custom script to make sure an "empty" record is created when a specific input record does not exist in the message. For this to work, you must make sure that the potentially empty nodes in the document schema for the Flat File Assembler have the following properties set as shown:  
  
|Property|Setting|  
|--------------|-------------|  
|Preserve Delimiter for Empty Data|Yes|  
|Suppress Trailing Delimiters|No|  
|Generate Empty Nodes (set this on the root node)|True|  
  
### To create a map that creates an "empty" record  
  
1.  Add a new map to your BizTalk project.  
  
2.  Specify the document schema used by the Flat File Assembler as both the map source and map destination schema.  
  
3.  Map the source fields that will not be empty to the corresponding destination fields.  
  
4.  For those fields that may be empty, use a custom script to check if the source field is empty and return an empty string (instead of Nil). Use a script like the following:  
  
    ```  
    public string ValOrEmpty(string val)  
    {  
         return (val.Length > 0) ? val : "";  
    }  
    ```  
  
    > [!NOTE]
    >  You must create a script with a unique function name for each potentially empty field you map. For example, if you have three fields that may be empty, you might have functions named `ValOrEmpty1`, `ValOrEmpty2`, `ValOrEmpty3`.  
  
5.  Using BizTalk Server Administration console, configure the send port with the custom pipeline and flat file assembler component to use the map as an outbound map.  
  
## See Also  
 [How to Configure Outbound Maps for a Send Port](../core/how-to-configure-outbound-maps-for-a-send-port.md)   
 [Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md)