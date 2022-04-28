---
description: "Learn more about: Recordset Column Properties"
title: "Recordset Column Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15433"
helpviewer_keywords: 
  - "15433"
ms.assetid: bbbe57e5-4781-4428-bfd9-4128d591051f
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Recordset Column Properties
Use the **Recordset Column** properties page to set COBOL and design properties on a recordset column.  
  
## COBOL Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host Data Type**|Specifies the recordset column host data type.|  
|**Error Handling**|Recordset column error handling. The possible values are:<br /><br /> -   **Truncate**. If selected and an error occurs, TI will truncate the value. (default)<br />-   **Round**. If selected and an error occurs, TI will round the value.<br />-   **Error**. If selected and an error occurs, TI will return an error.|  
|**Filler**|Recordset column filler. The default is **0**.|  
|**From Host**|Indicates the number of bytes of FILLER that follows this data item in the buffers that are received from the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**To Host**|Indicates the number of bytes of FILLER that follows this data item in buffers that are sent to the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**Scale**|Recordset column scale.|  
|**Sign Attribute**|Recordset column sign attribute. The possible values are:<br /><br /> -   **Trailing**. For signed DISPLAY data type, indicates that the sign is trailing (default). This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type. For signed DISPLAY data type, indicates that the sign is not separate (default).<br />-   **Trailing Separate**. For signed DISPLAY data type, indicates that the sign is separate. This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type.<br />-   **Leading**. For signed DISPLAY data type, indicates that the sign is leading. This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type. For signed DISPLAY data type, indicates that the sign is not separate (default).<br />-   **Leading Separate**. For signed DISPLAY data type, indicates that the sign is separate.|  
|**Size/Precision**|Recordset column size.|  
|**SOSI**|Specifies whether double-byte character set data is expected to begin with a shift-out (SO) and end with a shift-in (SI) character. When this check box is selected, the SO and SI characters are removed from the data when it is received from the host application, and the SO and SI characters are added to the data when it is sent to the host application. In the length of the PIC G, it is not necessary to include the two bytes for the SO and SI characters because the TI run-time environment applies them. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
|**String Delimiting**|Recordset column string delimiting. The possible values are:<br /><br /> -   **Space-padded**. Tells the TI run-time environment that the mainframe representation of the string is delimited by padding the string definition with space characters. For example, if the mainframe's COBOL definition is PIC X(10) but only three characters are in the string, the mainframe expects seven trailing spaces. Therefore, selecting this option tells the TI run-time environment to convert strings being sent to the mainframe to change the string's NULL termination character to the appropriate number of trailing spaces before sending it to the mainframe. For example, if the string is defined on the mainframe as PIC X(10), TI will send a string of *ABC* followed by seven trailing spaces. Selecting this option also tells the TI run-time environment to convert the output string being returned from the mainframe to the TI Automation server by converting the string's trailing spaces to a single null termination character. For more information, see [Padding Mainframe Character Strings with Spaces](./how-to-pad-mainframe-character-strings-with-spaces2.md).<br />-   **Null-terminated**. Tells the TI run-time environment that the mainframe representation of the string is delimited by a null character (EBCDIC 0x00). Selecting this option tells the TI run-time environment to add a single null character to the end of a string if there is room for the byte before sending a string to the mainframe, and it tells the TI run-time environment to stop at the first null character encountered when receiving a string from the mainframe. Therefore, by selecting this option, you are telling TI to retain trailing spaces in output strings coming from the mainframe because TI will not convert the trailing spaces to a single NULL terminator. For more information, see [Padding Mainframe Character Strings with Spaces](./how-to-pad-mainframe-character-strings-with-spaces2.md).|  
  
## Design Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Data Type**|The data type of the currently displayed column. Recordset column data type. The possible values are:<br /><br /> -   **Void**<br />-   **Boolean**<br />-   **Byte**<br />-   **Date**<br />-   **Currency**<br />-   **Decimal**<br />-   **Integer**<br />-   **Long**<br />-   **Double**<br />-   **Single**<br />-   **String**|  
|**Name**|Name of the recordset column. The name can be a maximum of 250 Unicode characters.|  
  
> [!CAUTION]
>  The properties of a component are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the component to function incorrectly.  
  
## See Also  
 [Properties (TI Project)](../core/properties-ti-project-2.md)
