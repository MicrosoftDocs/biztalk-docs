---
description: "Learn more about: REF_I12 in V2.XML 2.3.1"
title: "REF_I12 in V2.XML 2.3.1"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# REF_I12 in V2.XML 2.3.1
You must manually change the following code in the REF_I12 schema in V2.XML 2.3.1 after running the Update2XMLSchema tool:  
  
```  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
```  
  
 You must replace the above code with the following, in order to fix the ambiguity caused by multiple occurrences of the **REF** element definition:  
  
```  
<xsd:element minOccurs="0" maxOccurs="2" ref="REF_I12.PATIENT_VISIT" />  
```  
  
## See Also  
 [Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)   
 [Utilities](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)
