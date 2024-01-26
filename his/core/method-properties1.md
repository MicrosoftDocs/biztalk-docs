---
description: "Learn more about: Method Properties"
title: "Method Properties1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "15430"
---
# Method Properties
Use the **Method** properties page to set array, COBOL, design, host definition, and recordset properties on the method.  
  
## Array Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Array Dimensions**|Select the array dimensions for the return value. The default is **(none)**.|  
|**Is Array**|Select whether the return value is an array. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)|  
|**Occurs Depending On**|Select to indicate that a numeric data item preceding the table (recordset or array in Automation) indicates the actual number of rows or elements being sent or received. Equivalent to variable-length tables in COBOL.<br /><br /> Use the drop-down list to select the numeric data item that specifies this value. For CICS Link, the recordset or array and the associated length specifier must be in/out. The data in the buffer that follows a variable length table immediately follows the last data item in the table regardless of the maximum size specified for the table. Arrays with multiple dimensions can only be used for the outermost loop (COBOL) or rightmost dimension (Microsoft® Visual C++® or Visual Basic). The default is **(none)**.|  
  
## COBOL Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host Data Type**|Select the host data type.|  
|**Error Handling**|Select the return value error handling. The possible values are:<br /><br /> -   **Truncate**. Select this option to set TI to truncate the value when an error occurs. (default)<br />-   **Round**. Select this option to set TI to round the value when an error occurs.<br />-   **Error**. Select this option to set TI to return an error when an error occurs.|  
|**Filler**|Type the return value filler. The default is **0**.|  
|**From Host**|Type the number of bytes of FILLER that follows this data item in the buffers that are received from the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side. The default is **0**.|  
|**To Host**|Type the number of bytes of FILLER that follows this data item in buffers that are sent to the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side. The default is **0**.|  
|**Scale**|Type the return value scale.|  
|**Sign Attribute**|Select the return value sign attribute. The possible values are:<br /><br /> -   **Trailing**. For signed DISPLAY data type, indicates that the sign is trailing (default). This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type.<br />-   **Trailing Separate**. For signed DISPLAY data type, indicates that the sign is separate. This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type.<br />-   **Leading**. For signed DISPLAY data type, indicates that the sign is leading. This option indicates to the TI run-time environment how a signed DISPLAY data type is formatted and affects how data from the host is converted to and from the Automation data type.<br />-   **Leading Separate**. For signed DISPLAY data type, indicates that the sign is separate.|  
|**Size**|Type the return value size.|  
|**SOSI**|Select this option to specifywhether a double-byte character set data is expected to begin with a shift-out (SO) and end with a shift-in (SI) character. The possible values are:<br /><br /> -   **True**. The SO and SI characters are removed from the data when it is received from the host application, and the SO and SI characters are added to the data when it is sent to the host application. In the length of the PIC G, it is not necessary to include the two bytes for the SO and SI characters because the TI run-time environment applies them.<br />-   **False** (default)|  
|**String Delimiting**|Select the return value string delimiting. The possible values are:<br /><br /> -   **Space-padded**. Tells the TI run-time environment that the mainframe representation of the string is delimited by padding the string definition with space characters. For example, if the mainframe's COBOL definition is PIC X(10) but only three characters are in the string, the mainframe expects seven trailing spaces. Therefore, selecting this option tells the TI run-time environment to convert strings being sent to the mainframe to change the string's NULL termination character to the appropriate number of trailing spaces before sending it to the mainframe. For example, if the string is defined on the mainframe as PIC X(10), TI will send a string of *ABC* followed by seven trailing spaces. Selecting this option also tells the TI run-time environment to convert the output string being returned from the mainframe to the TI Automation server by converting the string's trailing spaces to a single null termination character. For more information, see [Padding Mainframe Character Strings with Spaces](./how-to-pad-mainframe-character-strings-with-spaces2.md). (default)<br />-   **Null-terminated**. Tells the TI run-time environment that the mainframe representation of the string is delimited by a null character (EBCDIC 0x00). Selecting this option tells the TI run-time environment to add a single null character to the end of a string if there is room for the byte before sending a string to the mainframe, and it tells the TI run-time environment to stop at the first null character encountered when receiving a string from the mainframe. Therefore, by selecting this option, you are telling TI to retain trailing spaces in output strings coming from the mainframe because TI will not convert the trailing spaces to a single NULL terminator. For more information, see [Padding Mainframe Character Strings with Spaces](./how-to-pad-mainframe-character-strings-with-spaces2.md).|  
  
## Design Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Allow 32K In/Out**|Select this option if you want TI to treat the input DFHCOMMAREA independently from the output DFHCOMMAREA. TI typically combines the input DFHCOMMAREA and the output DFHCOMMAREA area. The combined areas cannot exceed 32 KB of data. When this option is selected, TI treats the input DFHCOMMAREA independently from the output DFHCOMMAREA. Each input and output area uses up to 32 KB of data. Changing this option affects the currently selected method. Possible values are:<br /><br /> -   **True**<br />-   **False** (default) **Note:**  You can use this property as an accessory to "Use Link Programming Model" in the Windows-initiated processing (WIP) CICS programming model and in any host-initiated processing (HIP) programming models. **Note:**  This property is available only if the **Is Link** property is set to **True**.|  
|**Description**|Type a description of the method. The description can be a maximum of 250 Unicode characters.|  
|**Help Context ID**|Type the Help context ID associated with this method. The ID is used to connect to Help for this method, and returned when an exception occurs during invocation of this method. The default is **0**.|  
|**Include Context Parameter**|Select whether the client object method automatically includes context. The possible values are:<br /><br /> -   **True**. Visual Basic .NET automatically includes the context as an additional parameter in the argument. If you do not include **COMTIContext** parameter in your method call along with your other parameters, Visual Basic .NET returns the error message **An unhandled exception of type 'System.MissingMemberException' occurred in microsoft.visualbasic.dll** and informs you that the method cannot be called with the number of parameters you have written. If you receive this message, verify that the **Include Context Parameter** is included as a parameter within the list of parameters on the method.<br />-   **False**. Visual Basic .NET does not automatically include the context as an additional parameter in the argument. If you set this property to **False** and include **COMTIContext** parameter in your method call along with your other parameters, Visual Basic .NET returns the error message **An unhandled exception of type 'System.MissingMemberException' occurred in microsoft.visualbasic.dll** and informs you that the method cannot be called with the number of parameters you have written. If you receive this message, remove the **COMTIContext** parameter from the method parameter list.<br /><br /> The default is **True**.|  
|**Initial Buffer Value**|Type the initial buffer value. The default is null.|  
|**Is Link**|Select whether the host object method uses the Link programming model. The possible values for Windows-initiated processing (WIP) are:<br /><br /> -   **True**. Use the link model. The link programming model can be used only with CICS link protocols.<br />-   **False**. Do not use the link model.<br /><br /> The default is **False**.<br /><br /> The possible values for host-initiated processing (HIP) are:<br /><br /> -   **Yes**. Use the link model. The link programming model can be used with all protocols.<br />-   **No**. Do not use the link model.<br />-   **Link using 32K In/Out**. Use the link model and set the From Host and To Host properties.<br /><br /> The default is **No**.|  
|**Meta Data**|Select how metadata is handled. The possible values are:<br /><br /> -   **(none)**. By default no special data is sent to or received from the host application. Select this option button if you only want to send and receive the data for the method.<br />-   **Include Method Information**. The name of this method to be sent to the host along with parameter data. The method name is sent as the first 32 bytes in the buffer. This option is useful if multiple method calls go to the same transaction and you want to differentiate the data from the different calls.<br />-   **Include All Information**. All metadata available to be sent and received with your method data. For details of the format of metadata, see description for "Optional Metadata".|  
|**Name**|Type the name of the method. The name can be a maximum of 250 Unicode characters. The name must be different from any other method name in the same project. The default is **null**.|  
|**Position Return Value After**|Type the Automation method return value that follows the selected data item when it is received from the host. This option does not affect the Automation side. Use this option when the data item that you want to specify as the Automation return value is not the first data item field in the data declaration that describes the data received from the host.|  
|**Preliminary Filler**|View the number of bytes of FILLER received from or sent to the host.|  
|**From Host**|Type the number of bytes of FILLER that follows this data item in the buffers that are received from the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**To Host**|Type the number of bytes of FILLER that follows this data item in the buffers that are sent to the server. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**Return Type**|Select the return value type. The possible values are:<br /><br /> -   **Void**<br />-   **Boolean**<br />-   **Byte**<br />-   **Date**<br />-   **Currency**<br />-   **Decimal**<br />-   **Integer**<br />-   **Long**<br />-   **Double**<br />-   **Single**<br />-   **String**<br />-   **User-defined type**<br />-   **Recordset**<br />-   **(none)** (default)|  
|**Variable Sized Final Field**|-   Select this option when the last data item is a string to indicate that the size of the string varies. This option is also used to define a datatable or recordset as being either bounded or as including all rows as defined as **Maximum Occurrence** set on the parameter.|  
|**From Host**|-   **True**<br />-   **False** (default)|  
|**To Host**|-   **True**<br />-   **False** (default)|  
  
## Host Definition Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Link-to-Program Name**|Type the link-to-program name (CICS LINK/DPL).|  
|**Mirror Transaction ID**|Type the mirror TRANID that this method uses, if you want to override the mirror TRANID for the remote environment (RE) that this component is associated with. Leaving this box blank causes the mirror TRANID in the remote environment description to be used.<br /><br /> The TRANID can be up to four characters in length. Acceptable characters are A-Z a-z 0-9 $ @ # . / _ % & ? ! : &#124; =  , ; \< >.<br /><br /> Transaction names beginning with C are reserved for CICS and should not be used. The % and & characters may cause problems with Resource Access Control Facility (RACF) if transaction security is active.|  
|**TP Name**|Type a source transaction program (TP) name when the CICS application program must access a DB2 database. The TP name is referenced in a CICS Resource Control Table (RCT) entry, which associates CICS transactions with DB2 plans.<br /><br /> Specifies the name of the host transaction program (IMS or CICS) or the link-to program name (CICS LINK/DPL).|  
  
## Recordset Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Include Actual Size**|The host program will not include or expect any information that indicates the actual number of rows (recordsets) or elements (arrays) being sent or received. The possible values are:<br /><br /> -   **True**<br />-   **False** (default)<br /><br /> This property is read-only and will always be set to **False** unless it was set to **True** at the time the type library was created with the first version of COM Transaction Integrator.|  
|**Maximum Occurrence**|Maximum row occurrence. Indicates the maximum number of rows to be sent to or received from the host. Equivalent to the OCCURS n TIMES keyword on a COBOL group item. The default is **1**.|  
|**Occurs Depending On**|Equivalent to variable-length tables in COBOL. Indicates that a numeric data item preceding the table (recordset or array in Automation) indicates the actual number of rows or elements being sent or received. Use the drop-down list to select which numeric data item specifies this value. For CICS Link, the recordset or array and the associated length specifier must be in/out. The data in the buffer that follows a variable length table immediately follows the last data item in the table regardless of the maximum size specified for the table. For arrays with multiple dimensions, it can only be used for the outermost loop (COBOL) or rightmost dimension (Visual C++ or Visual Basic). Return value recordset occurs depending on. The default is **(none)**.|  
|**Unbounded**|Indicates the recordset is unbounded. Indicates that any number of rows can be sent to or received from the host. You would select this option when the rows being sent or received are from a database and the maximum number of rows is not known. The possible values are:<br /><br /> -   **True**. When the last data item is a string, this means that the size of the string varies.<br />-   **False**. When the last data item is an array, this means that the number of elements in the array varies. When the last data item is a recordset, this means that the number of rows in the recordset varies. (default)|  
  
> [!CAUTION]
>  The properties of a component are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the component to function incorrectly.  
  
## See Also  
 [Custom TRMs and ELMs with COMTIContext](./custom-trms-and-elms-with-comticontext2.md)   
 [Method Name Node (.NET)](../core/method-name-node-net-2.md)   
 [Properties (TI Project)](../core/properties-ti-project-2.md)
