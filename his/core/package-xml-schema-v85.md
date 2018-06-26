---
title: "Package XML Schema V85 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d987e50a-9153-4807-aa90-d239d2b68add
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Package XML Schema V85
## Static SQL for DB2 Custom Packages XML Schema V85  
 The Microsoft static SQL for DB2 custom package XML file contains multiple elements to inform the DRDA AR client how to execute the DRDA commands BGNBND (Begin Binding a Package to an RDB) and BNDSQLSTT (Bind SQL Statement to an RDB Package). This topic describes the XML elements that you can define to describe the static SQL package bind options, package name, package sections, statements, parameters, and result sets. The following XML listing is an example of the custom package XML.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
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
  
 <em>**Example 1.</em>* Microsoft static SQL for DB2 custom package XML file format v85.*  
  
### Packages Root Element  
 The **Packages** root element contains a set of nested elements consisting of **Options** and **Package**. There may be one **Options** element per document. There must be at least one **Package** element per document, as described in the following table.  
  
### Options Element  
 The Options element contains a set of optional elements that instruct the DRDA Client what values to specify for the BNDOPT (Bind Options) when executing the DRDA command BGNBND (Begin Binding a Package to an RDB).  
  
 *Bind Existence Checking*  
  
 The **BNDCHKEXS** element informs the DRDA Server whether to return an error when checking for the existence of database objects and authorities referenced in a package statement. This **optional** element accepts a **string** value. BNDEXSOPT instructs the DRDA Server to not return an error. BNDEXSRQR instructs the DRDA Server to check existence of database objects and authorities. The default value is **BNDEXSOPT**.  
  
 *Bind Package Creation Control*  
  
 The **BNDCRTCTL** element informs the DRDA Server whether errors are allowed during package binding. This **optional** element accepts a **string** value. BNDNERALW instructs the DRDA Server that no errors are allowed. BNDERRALW instructs the DRDA Server to allow errors and continue binding the package. BNDCHKONL instructs the DRDA Server to validate the bind request only. The default value is **BDNERALW**.  
  
 *Bind Explain Option*  
  
 The **BNDEXPOPT** element informs the DRDA Server whether to produce explanatory information for explainable database objects. This **optional** element accepts a **string** value. EXPNON instructs the DRDA Server to not produce explanatory information. EXPALL instructs the DRDA Server to explain all statements. EXPYES instructs the DRDA Server to explain static SQL statements only. The default value is **EXPNON**.  
  
> [!NOTE]
>  When connecting to IBM DB2 for i5/OS and DB2 for LUW, you should specify a value of EXPNON only.  
  
 *Decimal Precision*  
  
 The **DECPRC** element informs the DRDA Server the default decimal precision. This **optional** element accepts an **integer** value of 15, 16, 31 or 63. There is no default value.  
  
> [!NOTE]
>  When connecting to IBM DB2 for i5/OS, you should not specify this element.  
  
 *Default RDB Collection ID*  
  
 The **DFTRDBCOL** element informs the DRDA Server what default collection identifier to use to complete unqualified database object names. This **optional** element accepts a **string** value. There is no default value for this element. IBM DB2 for z/OS accepts a 128-byte string. IBM DB2 for i5/OS accepts a 10-byte string. IBM DB2 for LUW accepts a 30-byte string.  
  
 *Degree of IO Parallelism*  
  
 The **DGRIOPRL** element informs the DRDA Server to what degree I/O parallel processing is in effect for bound statements. This **optional** element accepts an **integer** value of -1 to 32676. A value of 1 instructs the DRDA Server that no IO parallel processing is required. A value of -1 instructs the DRDA Server to apply whatever degree of IO parallel processing is appropriate. The default value is **1**.  
  
 *Package Authorization Option*  
  
 The **PKGATHOPT** element informs the DRDA Server whether to keep or revoke package authorizations when the package is replaced. This **optional** element accepts a **string** value. PKGATHKP instructs the DRDA Server to keep authorizations. PKGATHRVK instructs the DRDA Server to revoke authorizations. The default value is **PKGATHKP**.  
  
 *Package Authorization Rules*  
  
 The **PKGATHRUL** element informs the DRDA Server which authorization identifier to use when executing dynamic SQL statements. This **optional** element accepts a **string** value. There default value is **REQUESTER**.  
  
|Value|Description|  
|-----------|-----------------|  
|REQUESTER|Instructs the DRDA Server to use the DRDA requester authorization|  
|OWNER|Instructs the DRDA Server to use the package owner authorization|  
|INVOKER_REVERT_TO_REQUESTER|Instructs the DRDA Server to use the authorization of the invoker of a function or stored procedure, otherwise use the DRDA requester authorization|  
|INVOKER_REVERT_TO_OWNER|Instructs the DRDA Server to use the authorization of the invoker of a function or stored procedure, otherwise use the package owner authorization|  
|DEFINER_REVERT_TO_REQUESTER|Instructs the DRDA Server to use the authorization of the creator of a function or stored procedure, otherwise use the DRDA requester authorization|  
|DEFINER_REVERT_TO_OWNER|Instructs the DRDA Server to use the authorization of the creator of a function or stored procedure, otherwise use the package owner authorization|  
  
 <em>**Table 1.</em>* PKGATHRUL values.*  
  
 *Package Default CCSIDs for a Column*  
  
 The **PKGDFTCC** element informs the DRDA Server which CCSID (Coded Character Set Identifier) to use when executing a SQL CREATE or ALTER table statement. This **optional** element contains 3 elements: **CCSIDSBC** (Code Character Set Identifier for Single-Byte Characters); **CCSIDMBC** (Code Character Set Identifier for Mixed-Byte Characters); and **CCSIDDBC** (Code Character Set Identifier for Double-Byte Characters). There is no default value for this element.  
  
 *Package Default Character Subtype*  
  
 The **PKGDFTCST** element informs the DRDA Server which character subtype to use when executing a SQL CREATE or ALTER table statement. This **optional** element accepts a **string** value. CSTSYSDFT indicates system default. CSTBCS indicates SBCS. CSTMBCS indicates MBCS. CSTBITS indicates CHAR FOR BIT DATA. The default value is **CSTSYSDFT**.  
  
 *Package Owner Identifier*  
  
 The **PKGOWNID** element instructs the DRDA Server which authorization identifier is the owner of the package. This **optional** element accepts a **string** value. There is no default value for this element.  
  
 *Package Replacement Option*  
  
 The **PKGRPLOPT** element instructs the DRDA Server whether the bind should replace the existing package. This **optional** element accepts a **string** value. PKGRPLALW indicates replace package allowed. PKGRPLNA indicates replace package not allowed. There default value is **PKGRPLALW**.  
  
 *Replaced Package Version Name*  
  
 The **PKGRPLVRS** element defines the package version name of the package that the DRDA Server should replace. This **optional** element accepts a **string** value. There is no default value for this element.  
  
 *Prepared Statement Keep*  
  
 The **PRPSTTKP** element instructs the DRDA Server to keep prepared dynamic SQL statements until released. This **optional** element accepts a **string** value. The default value is **F0**.  
  
|Value|Description|  
|-----------|-----------------|  
|F0|Indicates statements are released during commit and rollback|  
|F1|Indicates statements are kept during commit, but released during rollback|  
|F2|Indicates statements are released during commit, but kept during rollback|  
|F3|Indicates statements are kept during commit and rollback|  
  
 <em>**Table 2.</em>* PRPSTTKP values.*  
  
 *RDB Release Option*  
  
 The **RDBRLSOPT** element informs the DRDA Server when to release objects. This **optional** element accepts a **string** value. RDBRLSCMM indicates resources are released at commit. RDBRLSCNV indicates resources are released at end of session. The default value is **RDBRLSCMM**.  
  
 *Statement Date Format*  
  
 The **STTDATFMT** element informs the DRDA Server which statement date format to use in SQL statements. This **optional** element accepts a **string** value. There is no default value for this element.  
  
|Value|Format|Description|  
|-----------|------------|-----------------|  
|ISODATFMT|yyyy-mm-dd|ISO date format|  
|USADATFMT|mm/dd/yyyy|USA date format|  
|EURDATFMT|dd.mm.yyyy|EUR date format|  
|JISDATFMT|yyyy-mm-dd|JIS date format|  
|DFTDATFMT|NA|Default date format|  
|LOCDATFMT|NA|Local date format|  
|DMYBLKDATFMT|dd mm yy|Day Month Year with blank separator|  
|DMYCMADATFMT|dd,mm,yy|Day Month Year with comma separator|  
|DMYHPNDATFMT|dd-mm-yy|Day Month Year with hyphen separator|  
|DMYPRDDATFMT|dd.mm.yy|Day Month Year with period separator|  
|DMYSLHDATFMT|dd/mm/yy|Day Month Year with slash separator|  
|JULBLKDATFMT|yy ddd|Julian with blank separator|  
|JULCMADATFMT|yy,ddd|Julian with comma separator|  
|JULHPNDATFMT|yy-ddd|Julian with hyphen separator|  
|JULPRDDATFMT|yy.ddd|Julian with period separator|  
|JULSLHDATFMT|yy/ddd|Julian with slash separator|  
|MDYBLKDATFMT|mm dd yy|Month Day Year with blank separator|  
|MDYCMADATFMT|mm,dd,yy|Month Day Year with comma separator|  
|MDYHPNDATFMT|mm-dd-yy|Month Day Year with hyphen separator|  
|MDYPRDDATFMT|mm.dd.yy|Month Day Year with period separator|  
|MDYSLHDATFMT|mm/dd/yy|Month Day Year with slash separator|  
|YMDBLKDATFMT|yy mm dd|Year Month Day with blank separator|  
|YMDCMADATFMT|yy,mm,dd|Year Month Day with comma separator|  
|YMDHPNDATFMT|yy-mm-dd|Year Month Day with hyphen separator|  
|YMDPRDDATFMT|yy.mm.dd|Year Month Day with period separator|  
|YMDSLHDATFMT|yy/mm/dd|Year Month Day with slash separator|  
  
 <em>**Table 3.</em>* STTDATFMT values.*  
  
 *Statement Decimal Delimiter*  
  
 The **STTDECDEL** element informs the DRDA Server which statement decimal delimiter to use in SQL statements. This **optional** element accepts a **string** value. DECDELPRD indicates a period. DECDELCMA indicates a comma. DFTPKG indicates package default, when rebinding package. There is no default value.  
  
 *Statement String Delimiter*  
  
 The **STTSTRDEL** element informs the DRDA Server which statement string delimiter to use in SQL statements. This **optional** element accepts a **string** value. STRDELAP indicates an apostrophe. STRDELDQ indicates a double quote. DFTPKG indicates package default, when rebinding package. There is no default value.  
  
 *Statement Time Format*  
  
 The **STTTIMFMT** element informs the DRDA Server which statement time format to use in SQL statements. This **optional** element accepts a **string** value. There is no default value for this element.  
  
|Value|Format|Description|  
|-----------|------------|-----------------|  
|ISOTIMFMT|hh.mm.ss|ISO time format|  
|USATIMFMT|hh:mm:ss AM|USA time format AM|  
|USATIMFMT|hh:mm:ss PM|USA time format PM|  
|EURTIMFMT|hh.mm.ss|EUR time format|  
|JISTIMFMT|hh:mm:ss|JIS time format|  
|DFTTIMFMT|NA|Default time format|  
|LOCTIMFMT|NA|Local time format|  
|HMSBLKTIMFMT|hh mm ss|Hour Minute Second with blank separator|  
|HMSCLNTIMFMT|hh:mm:ss|Hour Minute Second with colon separator|  
|HMSCMATIMFMT|hh,mm,ss|Hour Minute Second with comma separator|  
|HMSPRDTIMFMT|hh.mm.ss|Hour Minute Second with period separator|  
  
 <em>**Table 4.</em>* STTTIMFMT values.*  
  
### Package Element  
 The **Package** element contains a set of attributes, and one or more nested **Section** elements. There must be at least one **Section** element per **Package** element.  
  
 *Collection Identifier*  
  
 The **Collection** attribute corresponds to the DRDA RDBCOLID (RDB Collection Identifier) and instructs the DRDA Server into which collection to bind the package. This **optional** element accepts a **string** value. There is no default value. IBM DB2 for z/OS accepts a 128-byte string. IBM DB2 for i5/OS accepts a 10-byte string. IBM DB2 for LUW accepts a 30-byte string.  
  
> [!NOTE]
>  DRDA defines a fully-qualified static SQL package using a PKGNAM (RDB Package Name) that consists of these multiple parts.  
  
-   RDBNAM (Relational Database Name)  
  
-   RDBCOLID (RDB Collection Identifier)  
  
-   PKGID (RDB Package Identifier)  
  
```  
RDBNAME.RDBCOLID.PKGID.PKGCNSTKN.PKGSN  
```  
  
 <em>**Example 2.</em>* Fully-qualified package name with consistency token.*  
  
 *Package Identifier*  
  
 The **Id** attribute corresponds to the DRDA PKGID (RDB Package Identifier) and informs the DRDA Server what is the package identifier. This **required** element accepts a **string** value. There is no default value. IBM DB2 accepts a 128-byte string.  
  
 *Consistency Token*  
  
 The **Token** attribute corresponds to the DRDA PKGCNSTKN (RDB Package Consistency Token) and informs the DRDA Server what is the package consistency token. This **optional** element accepts a **string** value. There is no default value. IBM DB2 supports an 8-byte string.  
  
- PKGCNSTKN (RDB Package Consistency Token)  
  
- VRSNAM (Version Name)  
  
  *Version Name*  
  
  The **Version** attribute corresponds to the DRDA VRSNAM (Version Name) and informs the DRDA Server what is the package version name. This **optional** element accepts a **string** value. There default value is null. IBM DB2 supports a 254-byte string.  
  
  *Package Isolation Level*  
  
  The **IsolationLevel** attribute instructs the DRDA Server to bind the package with the requested DRDA PKGISOLVL (Package Isolation Level). This **required** element accepts a **string** value. The default value is **ISOLVLCS**.  
  
|DDM|Description|  
|---------|-----------------|  
|ISOLVLCS|DRDA ISOLVLCS (Isolation Level Cursor Stability)<br /><br /> ANSI READ COMMITTED<br /><br /> IBM DB2 CURSOR STABILITY (CS)<br /><br /> IBM DB2 for i5/OS COMMIT(*CS)<br /><br /> Microsoft .NET Framework ReadCommitted|  
|ISOLVLRR|DRDA ISOLVLRR (Isolation Level Repeatable Read)<br /><br /> ANSI SERIALIZABLE<br /><br /> IBM DB2 REPEATABLE READ (RR)<br /><br /> IBM DB2 for i5/OS COMMIT(*RR)<br /><br /> Microsoft .NET Framework Serializable|  
|ISOLVLALL|DRDA ISOLVLALL (Isolation Level All)<br /><br /> ANSI REPEATABLE READ<br /><br /> IBM DB2 READ STABILITY (RS)<br /><br /> IBM DB2 for i5/OS COMMIT(*RS)<br /><br /> Microsoft .NET Framework RepeatableRead|  
|ISOLVLCHG|DRDA ISOLVLCHG (Isolation Level Change)<br /><br /> ANSI READ UNCOMITTED<br /><br /> IBM DB2 UNCOMMITTED READ (UR)<br /><br /> IBM DB2 for i5/OS COMMIT(*UR)<br /><br /> Microsoft .NET Framework ReadUncommitted|  
|ISOLVLNC|DRDA ISOLVLNC (Isolation Level No Commit)<br /><br /> IBM DB2 for i5/OS COMMIT(*NC)|  
  
 <em>**Table 5.</em>* PKGISOLVL values.*  
  
 *Package Title*  
  
 The **Title** attribute instructs the DRDA Server to bind the package with the requested DRDA TITLE (Title), which is a descriptive comment. This **optional** element accepts a **string** value. There is no default value. DRDA supports a 254-byte string.  
  
### Section Element  
 The **Section** element contains a set of attributes, and nested **Statement**, **Parameters**, and **ResultSet** elements. There must be at least one **Statement** element per **Section** element.  
  
 *Section Number*  
  
 The **Number** attribute instructs the DRDA Server to bind the statement to the package with the requested DRDA PKGSN (RDB Package Section Number). This **required** element accepts an **integer** value and must be unique within the Package element. There is no default value.  
  
 *Section Alias*  
  
 The **Alias** attribute instructs the Microsoft DRDA Client to locate a package section based on an alias name. This **optional** element accepts an 8-byte **string** value. There is no default value.  
  
> [!NOTE]
>  See Programmer’s Reference for Microsoft.HostIntegration.MsDb2Client.MsDb2Connection SetCustomPackageData.  
  
### Statement Element  
 The **Statement** element contains an attribute and a value.  
  
 *Statement Number*  
  
 The **Number** attribute instructs the DRDA Server to bind the statement to the package with the requested DRDA SQLSTTNBR (SQL Statement Number). This **required** element accepts an **integer** value and must be unique within the Package element. There is no default value.  
  
 The **Number** attribute corresponds to the DRDA PKGSN (RDB Package Section Number) and instructs the DRDA Server to bind the section as this number. This **optional** attribute accepts an **integer** value and must be unique within the Package element. There is no default value.  
  
 *SQL Statement Command Text*  
  
 The **Statement** attribute corresponds to the DRDA SQLSTT (SQL Statement) and instructs the DRDA Server to bind the statement to the package with this SQL statement command text. This **required** element accepts a **string** value. There is no default value. DB2 accepts a 2,097,152-byte string.  
  
### Parameters Element  
 The **Parameters** element contains one or more **Parameter** elements.  
  
### Parameter Element  
 The **Parameter** element contains a set of attributes.  
  
> [!NOTE]
>  The **parameter** elements must be defined in the same order as the variables in the SQL statement.  
  
 *Parameter Name*  
  
 The **Name** attribute instructs the DRDA Server what is the name of the parameter. This **required** attribute accepts a **string** value. There is no default value. IBM DB2 supports a 128-byte string.  
  
 *Parameter Type*  
  
 The **Type** attribute instructs the DRDA Server what is the type of the parameter. This **required** attribute accepts a **string** value. There is no default value.  
  
 *Parameter Length*  
  
 The **Length** attribute instructs the DRDA Server what is the length of the parameter. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Parameter Precision*  
  
 The **Precision** attribute instructs the DRDA Server what is the precision of the parameter. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Parameter Scale*  
  
 The **Scale** attribute instructs the DRDA Server what is the scale of the parameter. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Parameter Coded Character Set Identifier*  
  
 The **CCSID** attribute instructs the DRDA Server what is the Coded Character Set Identifier of the parameter. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Parameter Nullability*  
  
 The **Nullable** attribute instructs the DRDA Server whether the parameter value is nullable. This **required** attribute accepts a **Boolean** value. There default value is true.  
  
### ResultSet Element  
 The **ResultSet** element contains one or more **Column** elements which define the output column in the result set.  
  
> [!NOTE]
>  The MsDb2Client provider uses this information to return a result set to the consumer program, including the correct metadata for the column names and data types. Optionally, configure the MsDb2Client connection string argument “Use Early Metadata=False” to instruct the MsDb2Client to ignore the design-time metadata defined in the ResultSet portion of the static SQL for DB2 XML file, and then use the late metadata returned by the DRDA Server.  
  
### Column Element  
 The **Column** element contains a set of attributes.  
  
 *Column Ordinal*  
  
 The **Ordinal** attribute identifies the place of the column within the result set. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Column Name*  
  
 The **Name** attribute instructs the DRDA Server what is the name of the column. This **required** attribute accepts a **string** value. There is no default value. IBM DB2 supports a 128-byte string.  
  
 *Column Type*  
  
 The **Type** attribute instructs the DRDA Server what is the type of the column. This **required** attribute accepts a **string** value. There is no default value.  
  
 *Column Length*  
  
 The **Length** attribute instructs the DRDA Server what is the length of the column. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Column Precision*  
  
 The **Precision** attribute instructs the DRDA Server what is the precision of the column. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Column Scale*  
  
 The **Scale** attribute instructs the DRDA Server what is the scale of the column. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Column Coded Character Set Identifier*  
  
 The **CCSID** attribute instructs the DRDA Server what is the Coded Character Set Identifier of the column. This **required** attribute accepts an **integer** value. There is no default value.  
  
 *Column Nullability*  
  
 The **Nullable** attribute instructs the DRDA Server whether the column value is nullable. This **required** attribute accepts a **Boolean** value. There default value is true.  
  
### Reference Tables  
 *Data Types*  
  
 The following table lists data types and lengths for use in defining parameter and columns in the static SQL for DB2 XML file format V85.  
  
|Type|Length|Description|  
|----------|------------|-----------------|  
|BigInt|8|A 64-bit signed integer.|  
|Char||A character string.|  
|CharForBit||A binary string.|  
|Date|10|Date and time data ranging in value from January 1, 1753 to December 31, 9999 to an accuracy of 3.33 milliseconds.|  
|Decimal||A simple type representing values ranging from 1.0 x 10 -28 to approximately 7.9 x 10 28 with 28-29 significant digits.|  
|Double|8|A floating point number within the range of -1.79E +308 through 1.79E +308.|  
|Graphic||A double-byte character string.|  
|Int|4|A 32-bit signed integer, with values between -2147483648 and 2147483647.|  
|Numeric||An exact numeric value with a fixed precision and scale.|  
|Real|4|Signed, approximate, numeric value with a binary precision 24 (zero or absolute value 10[–38] to 10[38]).|  
|SmallInt|2|A 16-bit signed integer, with values between -32768 and 32767.|  
|Time|8.|Date and time data ranging in value from January 1, 1753 to December 31, 9999 to an accuracy of 3.33 milliseconds.|  
|Timestamp|26|Data and time data in the format YYYY-MM-DD-hh.mm.ss.tttttt.|  
|VarChar||A variable-length character string.|  
|VarCharForBit||A variable-length binary string.|  
|VarGraphic||A double-byte character string.|  
  
 <em>**Table 6.</em>* Data type and length values.*  
  
 *Coded Character Set Identifiers*  
  
 The following table lists data types and lengths for use in defining options, parameter and columns in the static SQL for DB2 XML file format V85.  
  
|Type|Group|CCSID|NLS|Description|  
|----------|-----------|-----------|---------|-----------------|  
|SBCS|ANSI|1250|1250|Central Europe|  
|SBCS|ANSI|1251|1251|Cyrillic|  
|SBCS|ANSI|1252|1252|Latin I|  
|SBCS|ANSI|1253|1253|Greek|  
|SBCS|ANSI|1254|1254|Turkish|  
|SBCS|ANSI|1255|1255|Hebrew|  
|SBCS|ANSI|1256|1256|Arabic|  
|SBCS|ANSI|1257|1257|Baltic|  
|SBCS|ANSI/OEM|874|874|Thai|  
|SBCS|ANSI/OEM|932|932|Japanese Shift-JIS|  
|SBCS|ANSI/OEM|1258|1258|Viet Nam|  
|SBCS|EBCDIC|37|1140|U.S./ Canada (Euro)|  
|SBCS|EBCDIC|37|37|U.S./ Canada|  
|SBCS|EBCDIC|273|1141|Germany (Euro)|  
|SBCS|EBCDIC|273|20273|Germany|  
|SBCS|EBCDIC|277|1142|Denmark/ Norway (Euro)|  
|SBCS|EBCDIC|277|20277|Denmark/ Norway|  
|SBCS|EBCDIC|278|1143|Finland/ Sweden (Euro)|  
|SBCS|EBCDIC|278|20278|Finland/ Sweden|  
|SBCS|EBCDIC|280|1144|Italy (Euro)|  
|SBCS|EBCDIC|280|20280|Italy|  
|SBCS|EBCDIC|284|1145|Latin America/Spain (Euro)|  
|SBCS|EBCDIC|284|20284|Latin America/Spain|  
|SBCS|EBCDIC|285|1146|United Kingdom (Euro)|  
|SBCS|EBCDIC|285|20285|United Kingdom|  
|SBCS|EBCDIC|290|NA|Japan Katakana (Extended)|  
|SBCS|EBCDIC|290|290|Japan Katakana (Extended)|  
|SBCS|EBCDIC|297|1147|France (Euro)|  
|SBCS|EBCDIC|297|20297|France|  
|SBCS|EBCDIC|420|20420|Arabic|  
|SBCS|EBCDIC|423|20423|Greek|  
|SBCS|EBCDIC|424|20424|Hebrew|  
|SBCS|EBCDIC|500|1148|International (Euro)|  
|SBCS|EBCDIC|500|500|International|  
|SBCS|EBCDIC|833|NA|Korean (Extended)|  
|SBCS|EBCDIC|836|NA|Simplified Chinese (Extended)|  
|SBCS|EBCDIC|838|20838|Thai|  
|SBCS|EBCDIC|870|870|Multilingual/ ROECE (Latin-2)|  
|SBCS|EBCDIC|871|1149|Icelandic (Euro)|  
|SBCS|EBCDIC|871|20871|Icelandic|  
|SBCS|EBCDIC|875|875|Greek (Modern)|  
|SBCS|EBCDIC|880|20880|Cyrillic (Russian)|  
|SBCS|EBCDIC|905|20905|Turkish (Latin-3)|  
|SBCS|EBCDIC|924|20924|Latin-1/Open System (Euro)|  
|SBCS|EBCDIC|930|930|Japan Katakana/Kanji (Extend Katakana)|  
|SBCS|EBCDIC|931|931|Japanese|  
|SBCS|EBCDIC|933|933|Korea (Extended)|  
|SBCS|EBCDIC|935|935|Simplified Chinese (Extended)|  
|SBCS|EBCDIC|937|937|Traditional Chinese (Extended)|  
|SBCS|EBCDIC|939|939|Japan English/Kanji (Extended)|  
|SBCS|EBCDIC|1025|21025|Cyrillic (Serbian, Bulgarian)|  
|SBCS|EBCDIC|1026|1026|Turkish (Latin-5)|  
|SBCS|EBCDIC|1027|NA|Japan English (Extended)|  
|SBCS|EBCDIC|1027|NA|Japan English (Extended)|  
|SBCS|EBCDIC|1047|1047|Latin-1/Open System|  
|SBCS|EBCDIC|5026|NA|Japan Katakana/Kanji (Extend Katakana)|  
|SBCS|EBCDIC|5035|NA|Japan English/Kanji (Extended)|  
|SBCS|EBCDIC|28709|NA|Traditional Chinese (Extended)|  
|SBCS|ISO|813|28597|8859-7 Greek|  
|SBCS|ISO|819|28591|8859-1 Latin-1|  
|SBCS|ISO|912|28592|8859-2 Central Europe|  
|SBCS|ISO|913|28593|8859-3 Latin 3|  
|SBCS|ISO|914|28594|8859-4 Baltic|  
|SBCS|ISO|915|28595|8859-5 Cyrillic|  
|SBCS|ISO|916|28598|8859-8 Hebrew (Visually Ordered)|  
|SBCS|ISO|920|28599|8859-9 Hebrew (Logically Ordered)|  
|SBCS|ISO|923|20865|8859-15 Latin 9 (Euro)|  
|SBCS|ISO|1089|28596|8859-6 Arabic|  
|SBCS|ISO|6937|20269|6937 Non-Spacing Accent|  
|SBCS|OEM|437|437|United States|  
|SBCS|OEM|737|737|Greek 437G|  
|SBCS|OEM|775|775|Baltic|  
|SBCS|OEM|850|850|Multilingual Latin I|  
|SBCS|OEM|852|852|Multilingual Latin II|  
|SBCS|OEM|855|855|Cyrillic|  
|SBCS|OEM|857|857|Turkish|  
|SBCS|OEM|860|860|Portuguese|  
|SBCS|OEM|861|861|Icelandic|  
|SBCS|OEM|862|862|Hebrew|  
|SBCS|OEM|863|863|Canadian French|  
|SBCS|OEM|864|864|Arabic|  
|SBCS|OEM|865|865|Nordic|  
|SBCS|OEM|866|866|Cyrillic II|  
|SBCS|OEM|869|869|Modern Greek|  
|MBCS|EBCDIC|930|NA|Japan Katakana/Kanji (Extended)|  
|MBCS|EBCDIC|931|NA|Japanese|  
|MBCS|EBCDIC|933|NA|Korea (Extended)|  
|MBCS|EBCDIC|935|NA|Simplified Chinese (Extended)|  
|MBCS|EBCDIC|937|NA|Traditional Chinese (Extended)|  
|MBCS|EBCDIC|939|NA|Japan English/Kanji (Extended)|  
|MBCS|EBCDIC|5026|NA|Japan Katakana/Kanji (Extended)|  
|MBCS|EBCDIC|5035|NA|Japan English/Kanji (Extended)|  
|DBCS|ANSI/OEM|936|936|Simplified Chinese GBK|  
|DBCS|ANSI/OEM|949|949|Korean|  
|DBCS|ANSI/OEM|950|950|Traditional Chinese Big5|  
|DBCS|EBCDIC|300|NA|IBM EBCDIC - Japan|  
|DBCS|EBCDIC|834|NA|IBM EBCDIC - Korea|  
|DBCS|EBCDIC|835|NA|IBM EBCDIC - Traditional Chinese|  
|DBCS|EBCDIC|837|NA|IBM EBCDIC - Simplified Chinese|  
|DBCS|EBCDIC|4396|NA|IBM EBCDIC - Japan|  
  
 <em>**Table 7.</em>* Coded Character Set Identifier values.*  
  
> [!NOTE]
>  The Microsoft ADO.NET Data Provider for DB2 supports a set of Coded Character Set Identifiers. IBM DB2 database servers for z/OS and i5/OS typically use EBCDIC. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).