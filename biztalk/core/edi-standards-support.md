---
title: "EDI Standards Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2ef14c5-5f12-40e2-93d7-59b5c5a0d641
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Standards Support
BizTalk Server provides for design- and run-time support for four encoding standards. The following table lists the encoding standards with links to more information.  
  
|Encoding Standard|Industry Segment|References|  
|-----------------------|----------------------|----------------|  
|UN/EDIFACT|General Industry|[Standards Website](http://go.microsoft.com/fwlink/?LinkId=77532) (reference to payload)<br /><br /> [Encoding rule](http://go.microsoft.com/fwlink/?LinkId=77534) per ISO 9735-4.1|  
|X12|General Industry|[Standards Website](http://go.microsoft.com/fwlink/?LinkID=28673)<br /><br /> [Specifications Development](http://go.microsoft.com/fwlink/?LinkId=77535)|  
|EANCOM|Retail|[Standards Website](http://go.microsoft.com/fwlink/?LinkId=92861)|  
|HIPAA X12N|Health Care|[HIPAA Implementation Guide](http://go.microsoft.com/fwlink/?LinkId=77541)<br /><br /> [HIPAA Specifications](http://go.microsoft.com/fwlink/?LinkId=77542)|  
  
> [!NOTE]
>  EANCOM schemas are a subset of EDIFACT. EANCOM follows the same encoding rules that EDIFACT follows.  
  
> [!NOTE]
>  KEDIFACT is a separate standard, but is closely based on the EDIFACT standard.  
  
## X12 and EDIFACT  
 Two standards, ANSI X12 and UN/EDIFACT, constitute more than 90% of all EDI messages exchanged globally:  
  
- The UN/EDIFACT EDI international message standard (EDI for Administration, Commerce, and Trade) was developed and continues to be maintained by the United Nations Economic Commission for Europe (UN/ECE). Also known as just EDIFACT.  
  
- The X12 EDI U.S. message standard was developed and continues to be maintained by the Accredited Standards Committee (ASC) X12 committee chartered by the American National Standards Institute (ANSI).  
  
  EDIFACT is based largely on the U.S. X12 standards. The two EDI standards are very similar in terms of structure. Differences include:  
  
- Structural elements are named differently in the two standards. For example, the interchange control header is an ISA data element in X12 and a UNB data element in EDIFACT.  
  
- While many transaction sets map between the two standards, the transaction sets are named differently in the two standards. For example, a purchase order is an 850 transaction set in X12 and an ORDERS transaction set in EDIFACT.  
  
- EDIFACT has an optional header segment UNA to set structural elements such as separators/delimiters and decimal notation, overriding the default values defined in a pipeline.  
  
- X12 has two acknowledgments (a technical acknowledgment called TA1 and a functional acknowledgment called 997), while EDIFACT has one comprehensive acknowledgment called CONTRL.  
  
- X12 recommends ASCII encoding, while EDIFACT recommends UTF8 encoding.  
  
  BizTalk Server supports the KEDIFACT (Korea EDIFACT) standard. KEDIFACT follows the Message Implementation Guide of UN/EDIFACT, so is closely based on EDIFACT. However, there are differences between KEDIFACT and X12/EDIFACT. KEDIFACT uses several KEDIFACT-specific EDI schemas and uses the KECA code page.  
  
## HIPAA  
 BizTalk Server supports X12 processing, and since HIPAA processing is a derivative of X12 processing, BizTalk Server supports HIPAA processing. Where you see references to X12 support in this document, it also applies to HIPAA processing.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the additional HIPAA-specific support:  
  
- A set of version 4010A1 HIPAA document schemas. For more information on EDI and HIPAA document schemas in BizTalk Server, see [EDI Document Schemas](../core/edi-document-schemas.md).  
  
- A set of version 5010 HIPAA document schemas. For more information, see [HIPAA Document Schema Version 5010](../core/hipaa-document-schema-version-5010.md).  
  
- HIPAA subdocument splitting. For more information, see [Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md).  
  
- Support for the first two levels of WEDI SNIP testing: X12 syntax integrity and requirements of the [HIPAA Implementation Guide](http://go.microsoft.com/fwlink/?LinkId=77541).  
  
  BizTalk Server provides HIPAA support as part of the native BizTalk Server EDI functionality. For more information, see [EDI Support in BizTalk Server](../core/edi-support-in-biztalk-server2.md).  
  
## EANCOM  
 BizTalk Server supports EDIFACT processing, and since EANCOM processing is a derivative of EDIFACT processing, BizTalk Server supports EANCOM processing. Where you see references to EDIFACT support in this document, this support also applies to EANCOM processing.  
  
 BizTalk Server provides the additional EANCOM-specific support:  
  
-   A set of version EAN94, EAN97, and EAN02 EANCOM document schemas. For more information on EDI and EANCOM document schemas in BizTalk Server, see [EDI Document Schemas](../core/edi-document-schemas.md).  
  
## See Also  
 [EDI Message Structure](../core/edi-message-structure.md)   
 [EDI Document Schemas](../core/edi-document-schemas.md)