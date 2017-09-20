---
title: "HIPAA Schema Trigger Field Annotations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1389284-a2ec-44e7-a2f1-8d26f83fd31d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HIPAA Schema Trigger Field Annotations
EDI segments often contain qualifier values that modify the meaning of the segment. For example, an N1 segment can contain a qualifying element of “BT” to signify a “bill-to name,” or it may contain a qualifying element of “ST” to indicate a “ship-to name.” Normally it is left to business logic to determine how to interpret these fields and the disassembler resolves all instances of the N1 segment to the same XML record name; however, the HIPAA schemas shipped with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] contain annotations that allow the EDI disassembler to create unique XML records based on the presence of a qualifying element.  
  
 **Trigger Field Implementation**  
  
 Trigger fields are implemented as a pair of XML attributes that describe the segment element and the trigger value that causes this record to be created. The following table describes these attributes:  
  
|Attribute|Purpose|  
|---------------|-------------|  
|trigger_field|The segment field that will be inspected for the trigger value.|  
|trigger_value|The trigger value(s).<br /><br /> This may contain a single value, or a space delimited list of values.|  
  
 The following table shows the trigger annotation as it would appear in the HIPAA schema, the EDI segment that will cause the trigger to activate, and the resulting XML data after processing the segment.  
  
|Schema Trigger Annotation|Matching N1 Segment|Resulting XML Data|  
|-------------------------------|-------------------------|------------------------|  
|`<xs:element name="TS835W1_1000A_Loop">  <xs:annotation>   <xs:appinfo>    <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayerIdentification_TS835W1_1000A/N101__EntityIdentifierCode"     trigger_value="PR" notes="Payer Identification" />    </xs:appinfo>  </xs:annotation>`|N1*PR\*Contoso\*XV\*0000000~|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|`<xs:element name="TS835W1_1000B_Loop">   <xs:annotation>    <xs:appinfo>     <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayeeIdentification_TS835W1_1000B/N101__EntityIdentifierCode"     trigger_value="PE" notes="Payee Identification" />    </xs:appinfo>   </xs:annotation>`|N1*PE\*Fabrikam\*FI\*9999999~|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
 **EDI Disassembler Processing of Trigger Fields**  
  
 When receiving a HIPAA transaction set, if the EDI disassembler encounters a segment that contains a trigger field, it uses the trigger information to generate an XML record specific to the segment and trigger combination. For example, in the following EDI data, there are two N1 segments that have different values for N101, PR and PE:  
  
```  
  
N1*PR*Contoso*XV*0000000~  
N3*N301__PayerAddressLine~  
N4*N401__PayerCityName*N4*N403__PayerPost**N4*N406~  
……  
N1*PE*Fabrikam*FI*9999999~  
N3*N301__PayeeAddressLine~  
N4*N401__PayeeCityName*N4*N403__PayeePost**N4*N406~  
  
```  
  
 When processed by the EDI disassembler, the trigger field annotations present in the schema will result in two separate XML records based on the value of N101, <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B>, corresponding to N1*PR and N1\*PE.  
  
 When sending, the EDI assembler will drop the suffix following the “_” character for fields that contain a trigger annotation. For example, both <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B> will both become N1.  
  
 **Default Segments and Trigger Fields**  
  
 The following table contains information on the default segments and trigger fields used in HIPAA documents supplied as part of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]:  
  
> [!NOTE]
>  The individual trigger values used with the trigger fields may vary between schemas.  
  
|Segment with Trigger|Trigger field|  
|--------------------------|-------------------|  
|AMT|AMT01|  
|CRC|CRC01|  
|DTM|DTM01|  
|DTP|DTP01|  
|ENT|ENT02|  
|HI|HI01:01|  
|N1|N101|  
|NM1|NM01|  
|NTE|NTE01|  
|REF|REF01|  
|RMR|RMR01|