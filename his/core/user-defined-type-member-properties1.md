---
title: "User-Defined Type Member Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15435"
ms.assetid: d7698e6c-ce36-4ce4-a7a7-507c2d6d97d1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# User-Defined Type Member Properties
Use the **User-Defined Type Member** properties page to set array, COBOL, host, design, and recordset properties on user-defined type members.  
  
## Array Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Array Dimensions**|User-defined type member array dimensions. The default is **(none)**.|  
|**Is Array**|User-defined type member is an array. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
|**Occurs Depending On**|User-defined type member array occurs depending on.|  
  
## Host Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host Data Type**|User-defined type member host data type.|  
|**Error Handling**|User-defined type member error handling. The possible values are:<br /><br /> -   **Truncate**. If selected and an error occurs, TI will truncate the value. (default)<br />-   **Round**. If selected and an error occurs, TI will round the value.<br />-   **Error**. If selected and an error occurs, TI will return an error.|  
|**Filler**|User-defined type member filler.|  
|**From Host**|Indicates the number of bytes of FILLER that follows this data item in the buffers that are received from the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**To Host**|Indicates the number of bytes of FILLER that follows this data item in buffers that are sent to the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**Scale**|User-defined type member scale.|  
|**Sign Attribute**|User-defined type member sign attribute. The possible values are:<br /><br /> -   **Trailing**. For signed DISPLAY data type, indicates that the sign is trailing (default). This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type. For signed DISPLAY data type, indicates that the sign is not separate (default).<br />-   **Trailing Separate**. For signed DISPLAY data type, indicates that the sign is separate.<br />-   **Leading**. For signed DISPLAY data type, indicates that the sign is leading. This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type. For signed DISPLAY data type, indicates that the sign is not separate (default).<br />-   **Leading Separate**. For signed DISPLAY data type, indicates that the sign is separate.|  
|**Size**|User-defined type member size.|  
|**SOSI**|Specifies whether double-byte character set data is expected to begin with a shift-out (SO) and end with a shift-in (SI) character. When this check box is selected, the SO and SI characters are removed from the data when it is received from the host application, and the SO and SI characters are added to the data when it is sent to the host application. In the length of the PIC G, it is not necessary to include the two bytes for the SO and SI characters because the TI run-time environment applies them. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
|**String Delimiting**|User-defined type member string delimiting. The possible values are:<br /><br /> -   **Space-padded**. Tells the TI run-time environment that the mainframe representation of the string is delimited by padding the string definition with space characters. For example, if the mainframe's COBOL definition is PIC X(10) but only three characters are in the string, the mainframe expects seven trailing spaces. Therefore, selecting this option tells the TI run-time environment to convert strings being sent to the mainframe to change the string's NULL termination character to the appropriate number of trailing spaces before sending it to the mainframe. For example, if the string is defined on the mainframe as PIC X(10), TI will send a string of *ABC* followed by seven trailing spaces. Selecting this option also tells the TI run-time environment to convert the output string being returned from the mainframe to the TI Automation server by converting the string's trailing spaces to a single null termination character. For more information, see [Padding Mainframe Character Strings with Spaces](./how-to-pad-mainframe-character-strings-with-spaces2.md).<br />-   **Null-terminated**. Tells the TI run-time environment that the mainframe representation of the string is delimited by a null character (EBCDIC 0x00). Selecting this option tells the TI run-time environment to add a single null character to the end of a string if there is room for the byte before sending a string to the mainframe, and it tells the TI run-time environment to stop at the first null character encountered when receiving a string from the mainframe. Therefore, by selecting this option, you are telling TI to retain trailing spaces in output strings coming from the mainframe because TI will not convert the trailing spaces to a single NULL terminator. For more information, see [Padding Mainframe Character Strings with Spaces](./how-to-pad-mainframe-character-strings-with-spaces2.md).|  
  
## Design Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Data Type**|User-defined type member data type. The data type of the currently displayed user-defined type member. The possible values are:<br /><br /> -   **Void**<br />-   **Boolean**<br />-   **Byte**<br />-   **Date**<br />-   **Currency**<br />-   **Decimal**<br />-   **Integer**<br />-   **Long**<br />-   **Double**<br />-   **Single**<br />-   **String**<br />-   **User-defined type**<br />-   **Recordset**|  
|**Name**|Name of the user-defined type member. The name can be a maximum of 250 Unicode characters. The name must be unique from any other user-defined type member name in the same project. The default is **null**.|  
  
## Recordset Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Include Actual Size**|Default option indicating that the host program will not include or expect any information that indicates the actual number of rows (recordsets) or elements (arrays) being sent or received. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
|**Maximum Occurrence**|Maximum row occurrence. Indicates the maximum number of rows to be sent to or received from the host. Equivalent to the OCCURS n TIMES keyword on a COBOL group item.|  
|**Occurs Depending On**|User-defined type member recordset occurs depending on. Indicates the maximum number of rows to be sent to or received from the host. Equivalent to the OCCURS n TIMES keyword on a COBOL group item. Equivalent to variable-length tables in COBOL. Indicates that a numeric data item preceding the table (recordset or array in Automation) indicates the actual number of rows or elements being sent or received. Use the drop-down list to select which numeric data item specifies this value. For CICS Link, the recordset or array and the associated length specifier must be in/out. The data in the buffer that follows a variable length table immediately follows the last data item in the table regardless of the maximum size specified for the table. For arrays with multiple dimensions, it can only be used for the outermost loop (COBOL) or rightmost dimension (Visual C++ or Visual Basic).|  
|**Unbounded**|Indicates that any number of rows can be sent to or received from the host. Set to **true** when the rows being sent or received are from a database and the maximum number of rows is not known. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
  
> [!CAUTION]
>  The properties of a component are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the component to function incorrectly.  
  
## See Also  
 [Properties (TI Project)](../core/properties-ti-project-2.md)