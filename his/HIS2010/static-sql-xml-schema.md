---
title: "Static SQL XML Schema | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd4fb625-a90d-4cd9-9d77-9f8eef77bc3a
caps.latest.revision: 4
---
# Static SQL XML Schema
This topic describes the XML elements that you can define to describe the static SQL package name, bind options, sections, and statements.  
  
 The following XML listing is an example of the custom package XML.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Packages>  
  <Options>  
    <BNDCHKEXS>BNDEXSOPT</BNDCHKEXS>  
    <BNDCRTCTL>BNDNERALW</BNDCRTCTL>  
    <BNDEXPOPT>EXPNON</BNDEXPOPT>  
    <DECPRC>31</DECPRC>  
    <DFTRDBCOL>COLLID</DFTRDBCOL>  
    <DGRIOPRL>1</DGRIOPRL>  
    <PKGATHOPT>PKGATHKP</PKGATHOPT>  
    <PKGATHRUL>OWNER</PKGATHRUL>  
    <PKGDFTCC>  
      <CCSIDDBC>0</CCSIDDBC>  
      <CCSIDMBC>0</CCSIDMBC>  
      <CCSIDSBC>0</CCSIDSBC>  
    </PKGDFTCC>  
    <PKGDFTCST>CSTSYSDFT</PKGDFTCST>  
    <PKGOWNID>PLARSEN</PKGOWNID>  
    <PKGRPLOPT>PKGRPLALW</PKGRPLOPT>  
    <PKGRPLVRS></PKGRPLVRS>  
    <PRPSTTKP>F0</PRPSTTKP>  
    <RDBRLSOPT>RDBRLSCMM</RDBRLSOPT>  
    <STTDATFMT>ISODATFMT</STTDATFMT>  
    <STTDECDEL>DECDELPRD</STTDECDEL>  
    <STTSTRDEL>STRDELAP</STTSTRDEL>  
    <STTTIMFMT>ISOTIMFMT</STTTIMFMT>  
  </Options>  
  <Package  
    Collection="COLLID" Id="PACKID" Token="TOK1" IsolationLevel="CursorStability" Version="V1" Title="TITLE1">  
    <Section Number="1" Alias="PACK1">  
      <Statement Number="1">DECLARE C1 CURSOR FOR SELECT NAME FROM SYSIBM.SYSPACKAGE WHERE COLLID = (:H)</Statement>  
      <Parameters>  
        <Parameter Name="P1" Type="VARCHAR" Length="128" Precision="0" Scale="0" CCSID="37" Nullable="FALSE"/>  
      </Parameters>  
      <ResultSet>  
        <Column Ordinal="1" Name="NAME" Type="VARCHAR" Length="128" Precision="0" Scale="0" CCSID="37" Nullable="FALSE"/>  
      </ResultSet>  
    </Section>  
  </Package>  
</Packages>  
  
```  
  
## Packages Root Element  
 The **Packages** root element contains a set of nested elements consisting of **Options** and **Package**. There may be one **Options** element per document. There must be at least one **Package** element per document, as described in the following table.  
  
|||  
|-|-|  
|**Element**|**Description**|  
|Packages|Contains one **Options** element.<br /><br /> Contains one or more **Package** elements.|  
  
## Options Element  
 The following table describes the **Options** element, which contains a set of optional elements used for binding custom static SQL packages.  
  
||||||  
|-|-|-|-|-|  
|**Element**|**Type**|**Length**|**Values**|**Description**|  
|BNDCHKEXS|String|8|BNDEXSRQR<br /><br /> BNDEXSOPT|Bind Existence Checking:<br /><br /> -   Yes, require existence checking of database objects and authorities (BNDEXSRQR); or<br /><br /> -   No, do not check existence (BNDEXSOPT).|  
|BNDCRTCTL|String|8|BNDERRALW<br /><br /> BDNERALW<br /><br /> BNDCHKONL|Bind Package Creation Control:<br /><br /> -   Yes, errors allowed (BNDERRALW);<br /><br /> -   No errors allowed (BDNERALW); or<br /><br /> -   Validate bind only (BNDCHKONL)|  
|BNDEXPOPT|String|6|EXPALL<br /><br /> EXPYES<br /><br /> EXPNON|Bind Explain Option:<br /><br /> -   Yes, explain all (EXPALL); or<br /><br /> -   No, explain none (EXPNON).|  
|DECPRC|String|2|15<br /><br /> 16<br /><br /> 31<br /><br /> 63|Decimal Precision: 15; 16; 31; or 63.|  
|DFTRDBCOL|String|255||Default RDB Collection ID: A 255-character string that the database uses to identify unqualified object names.<br /><br /> -   DB2 for z/OS accepts a 128-byte string.<br /><br /> -   DB2 for i5/OS accepts a 10-byte string.<br /><br /> -   DB2 for LUW accepts a 30-byte string.|  
|DGRIOPRL|String|6|1<br /><br /> -1<br /><br /> 2-32,767|Degree of I/O Parallelism:<br /><br /> -   A value of 1 indicates no parallel processing.<br /><br /> -   A value of -1 indicates parallel processing determined as appropriate.<br /><br /> -   A value of 2 to 32,767 indicates a special value for parallel processing.|  
|PKGATHOPT|String|8|PKGATHRVK<br /><br /> PKGATHKP|Package Authorization Option:<br /><br /> -   PKGATHRVK to revoke package authorizations when a package is replaced; or<br /><br /> -   PKGATHKP to keep package authorizations when a package is replaced.|  
|PKGATHRUL|String|25|REQUESTER<br /><br /> OWNER<br /><br /> INVOKER<br /><br /> INVOKER_REVERT_TO_REQUESTER<br /><br /> INVOKER_REVERT_TO_OWNER<br /><br /> DEFINER_REVERT_TO-REQUESTER<br /><br /> DEFINER_REVERT_TO_OWNER|Package Authorization Rules:<br /><br /> -   REQUESTER is the package execution requester’s authorization identifier;<br /><br /> -   OWNER is the package owner’s authorization identifier;<br /><br /> -   INVOKER_REVERT_TO_REQUESTER is the authorization identifier of the statement invoking the function or stored procedure, or is the creator of the view invoking function;<br /><br /> -   INVOKER_REVERT_TO_OWNER is the authorization identifier of the statement invoking the function or stored procedure, or is the creator of the view invoking function;<br /><br /> -   DEFINER_REVERT_TO_REQUESTER is the creator of the function or stored procedure; or<br /><br /> DEFINER_REVERT_TO_OWNER is the creator of the function or stored procedure.|  
|PKGDFTCC|NA|NA|(see list directly below)|Package Default CCSIDs for a Column:<br /><br /> -   See CCSIDDBC, CCSIDMBC, and CCSIDSBC.|  
|CCSIDDBC|Integer|||Code Character Set Identifier for Double-Byte Characters|  
|CCSIDMBC|Integer|||Code Character Set Identifier for Mixed-Byte Characters|  
|CCSIDSBC|Integer|||Code Character Set Identifier for Single-Byte Characters|  
|PKGDFTCST|String|8|CSTSYSDFT<br /><br /> CSTBITS<br /><br /> CSTSBCS<br /><br /> CSTMBCS|Package Default Character Subtype:<br /><br /> -   CSTSYSDFT indicates system default;<br /><br /> -   CSTBITS indicates CHAR FOR BIT DATA;<br /><br /> -   CSTBCS indicates SBCS; or<br /><br /> -   CSTMBCS indicates MBCS.|  
|PKGOWNID|String|||Package Owner Identifier:<br /><br /> -   DB2 for z/OS accepts an 8-byte string.<br /><br /> -   DB2 for i5/OS accepts a 10-byte string.<br /><br /> -   DB2 for Linux or UNIX accepts an 8-byte string.<br /><br /> -   DB2 for Windows accepts a 30-byte string.|  
|PKGRPLOPT|String|8|PKGRPLALW<br /><br /> PKGRPLNA|Package Replacement Option:<br /><br /> -   PKGRPLALW indicates that bind process should replace package.<br /><br /> -   PKGRPLNA indicates that bind process should not replace package.|  
|PKGRPLVRS|String|254||Replaced Package Version Name|  
|PRPSTTKP|String|2|F0<br /><br /> F1<br /><br /> F2<br /><br /> F3|Prepared Statement Keep:<br /><br /> -   F0 indicates default behavior where dynamic statements are dropped during commit and rollback.<br /><br /> -   F1 indicates that dynamic statements are kept during commit, but dropped during rollback.<br /><br /> -   F2 indicates that dynamic statements are dropped during commit, but kept during rollback.<br /><br /> -   F3 indicates that dynamic statements are kept during commit and rollback.|  
|RDBRLSOPT|String|8|RDBRLSCMM<br /><br /> RDBRLSCNV|RDB Release Option:<br /><br /> -   RDBRLSCMM indicates resources released at commit.<br /><br /> -   RDBRLSCNV indicates resources released at end of session.|  
|STTDATFMT|String|8|IISODATFMT<br /><br /> USADATFMT<br /><br /> EURDATFMT<br /><br /> JISDATFMT<br /><br /> DFTDATFMT<br /><br /> LOCDATFMT<br /><br /> DMYBLKDATFMT<br /><br /> DMYCMADATFMT<br /><br /> DMYHPNDATFMT<br /><br /> DMYPRDDATFMT<br /><br /> DMYSLHDATFMT<br /><br /> JULBLKDATFMT<br /><br /> JULCMADATFMT<br /><br /> JULHPNDATFMT<br /><br /> JULPRDDATFMT<br /><br /> JULSLHDATFMT<br /><br /> MDYBLKDATFMT<br /><br /> MDYCMADATFMT<br /><br /> MDYHPNDATFMT<br /><br /> MDYPRDDATFMT<br /><br /> MDYSLHDATFMT<br /><br /> YMDBLKDATFMT<br /><br /> YMDCMADATFMT<br /><br /> YMDHPNDATFMT<br /><br /> YMDPRDDATFMT<br /><br /> YMDSLHDATFMT|Statement Date Format:<br /><br /> -   ISODATFMT indicates ISO<br /><br /> -   USADATFMT indicates USA<br /><br /> -   EURDATFMT indicates EUR<br /><br /> -   JISDATFMT indicates JIS<br /><br /> -   DFTDATFMT indicates default<br /><br /> -   LOCDATFMT indicates local<br /><br /> -   DMYBLKDATFMT indicates DMY Blank<br /><br /> -   DMYCMADATFMT indicates DMY Comma<br /><br /> -   DMYHPNDATFMT indicates DMY Hyphen<br /><br /> -   DMYPRDDATFMT indicates DMY Period<br /><br /> -   DMYSLHDATFMT indicates DMY Slash<br /><br /> -   JULBLKDATFMT indicates JUL Blank<br /><br /> -   JULCMADATFMT indicates JUL Comma<br /><br /> -   JULHPNDATFMT indicates JUL Hyphen<br /><br /> -   JULPRDDATFMT indicates JUL Period<br /><br /> -   JULSLHDATFMT indicates JUL Slash<br /><br /> -   MDYBLKDATFMT indicates MDY Blank<br /><br /> -   MDYCMADATFMT indicates MDY Comma<br /><br /> -   MDYHPNDATFMT indicates MDY Hyphen<br /><br /> -   MDYPRDDATFMT indicates MDY Period<br /><br /> -   MDYSLHDATFMT indicates MDY Slash<br /><br /> -   YMDBLKDATFMT indicates YMD Blank<br /><br /> -   YMDCMADATFMT indicates YMD Comma<br /><br /> -   YMDHPNDATFMT indicates YMD Hyphen<br /><br /> -   YMDPRDDATFMT indicates YMD Period<br /><br /> -   YMDSLHDATFMT indicates YMD Slash|  
|STTDECDEL|String|8|DECDELPRD<br /><br /> DECDELCMA<br /><br /> DFTPKG|Statement Decimal Delimiter:<br /><br /> -   DECDELPRD indicates Period<br /><br /> -   DECDELCMA indicates Comma<br /><br /> -   DFTPKG indicates Package|  
|STTSTRDEL|String|8|STRDELAP<br /><br /> STRDELDQ<br /><br /> DFTPKG|Statement String Delimiter:<br /><br /> -   STRDELAP indicates Apostrophe<br /><br /> -   STRDELDQ indicates Double Quote<br /><br /> -   DFTPKG indicates Package|  
|STTTIMFMT|String|8|ISOTIMFMT<br /><br /> USATIMFMT<br /><br /> EURTIMFMT<br /><br /> JISTIMFMT<br /><br /> DFTTIMFMT<br /><br /> LOCTIMFMT<br /><br /> HMSBLKTIMFMT<br /><br /> HMSCLNTIMFMT<br /><br /> HMSCMATIMFMT<br /><br /> HMSPRDTIMFMT|Statement Time Format:<br /><br /> -   ISOTIMFMT indicates ISO<br /><br /> -   USATIMFMT indicates  USA<br /><br /> -   EURTIMFMT indicates  EUR<br /><br /> -   JISTIMFMT indicates  JIS<br /><br /> -   DFTTIMFMT indicates  Default<br /><br /> -   LOCTIMFMT indicates  Local<br /><br /> -   HMSBLKTIMFMT indicates  HMS Blank<br /><br /> -   HMSCLNTIMFMT indicates  HMS Colon<br /><br /> -   HMSCMATIMFMT indicates  HMS Comma<br /><br /> -   HMSPRDTIMFMT indicates  HMS Period|  
  
## Package Element  
 The **Package** element contains the following set of attributes: **Collection**, **Id**, **Token**, **Isolation Level**, **Version** and elements (Section).  
  
|||||||  
|-|-|-|-|-|-|  
|**Attribute**|**Type**|**Length**|**Values**|**Req**|**Description**|  
|Collection|String|128||Yes|-   DB2 for z/OS accepts a 128-byte string.<br /><br /> -   DB2 for i5/OS accepts a 10-byte string.<br /><br /> -   DB2 for LUW accepts a 30-byte string.|  
|Id|String|128||Yes|Identifier (name) is a 128-byte string.|  
|Token|String|8||No|Consistency Token is an 8-byte string.|  
|Isolation Level|String|8|Serializable<br /><br /> RepeatableRead<br /><br /> ReadCommitted<br /><br /> ReadUncommitted<br /><br /> NoCommit|Yes|-   Serializable indicates DB2 Repeatable Read (*RR)<br /><br /> -   RepeatableRead indicates DB2 Read Stability (\*ALL)<br /><br /> -   ReadCommitted indicates DB2 Cursor Stability (\*CS)<br /><br /> -   ReadUncommitted indicates DB2 Uncommitted Read (\*CHG)<br /><br /> -   NoCommit indicates DB2 for i5/OS No Commit (\*NC)|  
|Version|String|254||No|Version Name is a 254-byte string.|  
|Title|String|255||No|Title is a 255-byte string.|  
  
## Section Element  
 The **Section** element described in the following table contains two attributes, **Number** and **Alias**. It also contains the following set of elements: **Statement**, **Parameters** and **ResultSet**.  
  
|||||||  
|-|-|-|-|-|-|  
|**Attribute**|**Type**|**Length**|**Values**|**Req**|**Description**|  
|Number|Integer|||Yes|Relational Database Package Section Number is an integer.|  
|Alias|String|8||No|Alias allows you to define a friendly package name for use with the Microsoft ADO.NET Data Provider for DB2.|  
  
## Statement Element  
 The **Statement** element described in the following table has one required attribute, **Number**, and a required value for the SQL statement command string.  
  
||||||  
|-|-|-|-|-|  
|**Attribute**|**Type**|**Length**|**Values**|**Description**|  
|Number|Integer|||**Statement Number** is a required attribute.|  
|(Value)|String|||SQL statements are defined as strings within the \<Statement> and \</Statement> element tags.<br /><br /> -   DB2 for z/OS accepts a 2,097,152-byte string.<br /><br /> -   DB2 for i5/OS accepts a 2,097,152-byte string.<br /><br /> -   DB2 for Linux, UNIX, or Windows accepts a 2,097,152-byte string.|  
  
## Parameters Element  
 The **Parameters** element contains one or more **Parameter** elements, which define the input and/or output parameters on the SQL statement.  
  
### Parameter Element  
 The following table describes the **Parameter** element. There can be one or more **Parameter** elements, each containing a set of required attributes consisting of **Name**, **Type**, **Length**, **Precision**, **Scale**, **CCSID**, and **Nullable**.  
  
||||||  
|-|-|-|-|-|  
|**Attribute**|**Type**|**Length**|**Values**|**Description**|  
|Name|String|128||-   DB2 for z/OS accepts a 128-byte string.<br /><br /> -   DB2 for i5/OS accepts a 128-byte string.<br /><br /> -   DB2 for Linux, UNIX, or Windows accepts a 128-byte string.|  
|Type|String|30||Type is defined by using the name or abbreviation supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Length|Integer|||Length is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Precision|Integer|||Precision is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Scale|Integer|||Scale is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|CCSID|Integer|||Coded Character Set Identifier is defined by using a value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Nullable|String|5|TRUE<br /><br /> FALSE|Nullability is specified by using TRUE or FALSE|  
  
## ResultSet Element  
 The **ResultSet** element contains one or more **Column** elements which define the output column in the result set.  
  
### Column Element  
 The following table describes the required attributes of the **Column** element. There can be one or more **Column** elements, each identified by two attributes: **Ordinal** and **Name**.  
  
||||||  
|-|-|-|-|-|  
|**Attribute**|**Type**|**Length**|**Values**|**Description**|  
|Ordinal|Integer|||Specifies the position within the zero-based array of columns.|  
|Name|String|128||-   DB2 for z/OS accepts a 30- byte string.<br /><br /> -   DB2 for i5/OS accepts a 128-byte string.<br /><br /> -   DB2 for Linux, UNIX, or Windows accepts a 30-byte string.|  
|Type|String|30||Type is defined by using the name or abbreviation supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Length|Integer|||Length is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Precision|Integer|||Precision is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Scale|Integer|||Scale is defined by using the value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|CCSID|Integer|||Coded Character Set Identifier is defined by using a value supported by the target DB2 server platform and version. See SQL Reference for supported values.|  
|Nullable|String|5|TRUE<br /><br /> FALSE|Nullability is specified by using TRUE or FALSE|