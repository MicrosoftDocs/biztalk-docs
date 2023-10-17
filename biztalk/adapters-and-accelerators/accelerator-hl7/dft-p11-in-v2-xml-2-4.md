---
description: "Learn more about: DFT_P11 in V2.XML 2.4"
title: "DFT_P11 in V2.XML 2.4"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# DFT_P11 in V2.XML 2.4
You must manually change the following code in the DFT_P11 schema in V2.XML 2.4 after running the Update2XMLSchema tool:  
  
```  
<xsd:element ref="ROL" minOccurs="0" maxOccurs="unbounded" />  
<xsd:element ref="PV1" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="PV2" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="ROL" minOccurs="0" maxOccurs="unbounded" />  
```  
  
 You must replace the above code with the following, in order to fix the ambiguity caused by multiple occurrences of the **ROL** element definition:  
  
```  
<xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
  <xsd:choice minOccurs="0" maxOccurs="1">  
    <xsd:sequence>  
      <xsd:element minOccurs="1" maxOccurs="1" ref="PV1" />  
      <xsd:element minOccurs="0" maxOccurs="1" ref="PV2" />  
      <xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
    </xsd:sequence>  
    <xsd:sequence>  
      <xsd:element minOccurs="1" maxOccurs="1" ref="PV2" />  
      <xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
    </xsd:sequence>  
  </xsd:choice>  
```  
  
## See Also  
 [Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)   
 [Utilities](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)
