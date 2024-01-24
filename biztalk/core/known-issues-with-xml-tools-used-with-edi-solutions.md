---
description: "Learn more about: Known Issues with XML Tools Used with EDI Solutions"
title: "Known Issues with XML Tools Used with EDI Solutions"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Known Issues with XML Tools Used with EDI Solutions
This topic describes known issues with XML Tools in BizTalk Server.  
  
## Validation of Test Map Input and Output File Still Occurs When the Validate Property Is Set to False  
 If you test a map with the TestMap Input property set to **Native** and the Validate TestMap Input and Validate TestMap Output properties set to **False**, validation will still be performed. This occurs because the native-formatted input file will be converted into XML format, and BizTalk Server will validate the XML against the schema. If there are validation issues in the input file, this validation mechanism will post errors, even though the Validate TestMap Input and Validate TestMap Output properties are set to **False**.  
  
## Length validation is not performed on a data element in a generated instance that is pulled from an enum list in the schema  
 When an instance is generated from a schema, and the enumeration values for a data element in the schema do not meet the length requirement, the instance may be generated with a data element that will subsequently fail XSD validation because of the length requirement. Schema validation will not check whether a value in the generated instance that was pulled from an enum list in the schema fulfills the min/max length requirement.  
  
## Validate Schema may not detect an invalid transaction set ID code  
 When you validate a schema with the Validate Schema command in the Solution Explorer window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the check of the root node may not detect an invalid transaction set ID code in the last part of the root-reference node (in the format X12_\<VersionRelease\>_TSID). If the TSID in the root-reference node of the schema is invalid, but it is the same as the TSID in the enumeration node of the ST01 element in the schema, the Validate Schema operation will not detect that the TSID is invalid.  
  
## Visual Studio must be restarted to make an enum change in a schema effective for instance validation  
 If you change an enumeration list in a schema, save the schema, and then run instance validation, BizTalk Server will perform validation based upon the previous version of the schema, not the latest version. BizTalk Server will not use the latest version of the schema until you restart Visual Studio.  
  
## The EDI Instance Properties dialog box may be displayed when not needed in the TestMap operation  
 BizTalk Server will display an EDI Instance Properties dialog box twice during the TestMap process: once so that you can enter the delimiters required for interpreting the input message instance and once for entering the delimiters for generating the output message instance. BizTalk Server should display the EDI Instance Properties dialog box twice only and only for EDI schemas; however, BizTalk Server may display the dialog box for non-EDI schema and more than just twice. If so, close the dialog box.  
  
## Validation of an XML Preserved Interchange Is Not Supported  
 When validating a preserved interchange, if you select XML for the **Validate Instance Input Type** property, the operation will fail and nothing will be returned. However, if you select **Native** for the **Validate Instance Input Type** when validating a preserved interchange, the operation will succeed.  
  
## An Instance Generated for a HIPAA 278 Schema Will Contain Both Request and Response Sections  
 The HIPAA 278 schema is used for both 278 request and 278 response messages. If you use the Generate Instance command on a 278 schema, the instance generated will have both request and response sections, which should never be sent. To create a workable 278 request or 278 response message, open the instance that the XML tools generated in a text editor, and delete one of the sections, e.g., delete the response section for a request message.  
  
 If you run the Validate Instance command on a 278 message with both request and response sections, the message will validate successfully against the 278 schema.  
  
## An XML instance generated from a 278 HIPAA schema will fail validation  
 If you use the Instance Generation command to generate an XML instance from a 278 HIPAA schema, and then use the Instance Validation command to validate that instance, BizTalk Server will post an error.  
  
## A native instance generated from a 837 schema incorrectly sets GS08  
 When generating a native instance using a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution that contains the X12_BatchSchema as well as an 837I, 837D or 837P schema, the value of GS08 will contain 00401. Before processing this instance, you must change the value of GS08 to the correct value for the schema instance.  The following table contains the correct GS08 value for each 837 schema:  
  
|HIPAA Schema|GS08 Value|  
|------------------|----------------|  
|837I|004010X096A1|  
|837D|004010X097A1|  
|837P|004010X098A1|  
  
## See Also  
 [Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md)   
 [Using the XML Tool Extensions](../core/using-the-xml-tool-extensions.md)   
 [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md)
