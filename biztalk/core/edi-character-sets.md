---
description: "Learn more about: EDI Character Sets"
title: "EDI Character Sets"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EDI Character Sets
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses a character set to validate an entire EDI interchange. The character sets used for an X12-encoded message and an EDIFACT- or KEDIFACT-encoded message are determined in different ways.  
  
## EDIFACT Character Set  
 An EDIFACT-encoded interchange is self-describing in terms of its character set. The UNB1 data element is used. EDIFACT requires that tag names and separators/delimiters are ASCII types; as a result, locating UNB1 to apply the relevant code page for the remaining interchange is possible.  
  
 When processing an incoming EDIFACT message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the character set to use for that message from the UNB1 data element. No setting in the trading partner agreement is necessary.  
  
 When processing an outgoing EDIFACT message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the character set in the trading partner agreement or the fallback agreement. You set the UNB1 data element in the **Charset and Separators** page in the bi-directional agreement tabs (if an agreement is defined) or the **Charset and Separators** page in the agreement tab of the **EDIFACT Fallback Settings** dialog box (if no agreement is defined). UNB1.1 is a mandatory composite data element called the Syntax Identifier. UNB1.2 is the version of the EDIFACT character set. The UNB1 data element is also used to validate the values entered for properties in the Trading Partner Management user interface when the entire property set is saved (not when you tab out of a field or display a different page).  
  
 The available character sets are KECA, UNOA, UNOB, UNOC, UNOD, UNOE, UNOF, UNOG, UNOH, UNOI, UNOJ, UNOK, UNOX, and UNOY. The default value is UNOB. The full character set for these levels is specified in ISO 9735 EDIFACT Syntax Rules.  
  
> [!NOTE]
>  If the UNOC character set is encountered on an inbound or outbound interchange, the EDI Disassembler or EDI Assembler will use the Latin-1 code page, instead of the UTF-8 code page. This is required because UTF-8 is not a superset of UNOC. Some characters that are acceptable in UNOC will cause an interchange to be suspended when processed as UTF-8.  
  
 Characters in some EDIFACT character sets may be double-byte characters, whereas in other EDIFACT character sets they may be single-byte characters. Because of this, when you set the release criteria for batches based upon the number of characters in the interchange, the number of bytes in the interchange may differ depending on the character set used.  
  
 The UNA Segment and Segment Name UNB are limited to the values in the ASCII character set.  
  
## KEDIFACT Character Set  
 As with EDIFACT, the character set for a KEDIFACT-encoded interchange is established in the UNB1 data element. As for EDIFACT, the character set to be applied by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when processing a KEDIFACT interchange is established in data element **UNB1** of **Charset and Separators** page in the bi-directional agreement tabs (if an agreement is defined) or the **Charset and Separators** page in the agreement tab of the **EDIFACT Fallback Settings** dialog box (if no agreement is defined). The value for the **Identifier (UNB1.1)** element must be set to KECA.  
  
## X12 Character Set  
 When the BizTalk receive pipeline or send pipeline performs EDI validation of an X12-encoded message, it uses the X12 character set selected in the CharacterSet property of the pipeline. To set this property, open the Properties dialog box for the receive location or send port, click the ellipses next to the receive or send pipeline, and then set the CharacterSet property for the Disassembler or Assembler.  
  
 The CharacterSet property of the pipeline is used to validate an X12 interchange because unlike EDIFACT or KEDIFACT, an X12-encoded interchange is not self-describing in terms of its character set. Reading the ISA header with ISO or UTF encoding may lead to different values for agreement lookup. As a result, BizTalk must know the applicable character set to be used in processing the message prior to agreement lookup (when it would obtain the applicable character set for the agreement).  
  
 You specify the X12 character set to be used for agreement validation in the in the **Charset and Separators** page in the bi-directional agreement tabs (if an agreement is defined) or the **Charset and Separators** page in the fallback agreement tab of the **X12 Fallback Settings** dialog box (if no agreement is defined). However, BizTalk only uses these settings to validate the values entered for the related properties when the entire property set is saved (not when you tab out of a field or display a different page). The receive pipeline or send pipeline will ignore these character set properties.  
  
> [!NOTE]
>  If the character set specified in the agreement or fallback agreement does not match the character set selected for the receive or send pipeline, message validation errors could result. An example would be if the X12 character set property in the agreement is set to Extended while the X12 character property in the pipeline properties is set to Basic.  
  
 The available character sets are Basic and Extended (as documented in the X12 Specifications/Implementation Guides), and UTF8/Unicode. The default is UTF8.  
  
> [!NOTE]
>  The values entered for the data-element separator, component-element separator, and segment terminator in the bi-directional agreement or fallback agreement are limited to the values in the ASCII character set. These properties are not validated against the X12 character set.  
  
 The Basic character set includes the following uppercase letters, digits, space, and special characters: A through Z, 0 through 9, ! “ & ’ ( ) * + , - . / : ; ? = (space).  
  
 The Extended character set includes the characters in the Basic character set, and lowercase letters, select language characters, and other special characters: a through z, % @ [ ] _ { } \ &#124; \< \> ~ # $.  
  
## See Also  
 [EDI Messaging](../core/edi-messaging.md)   
 [EDI Schemas](../core/edi-schemas.md)
