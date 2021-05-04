---
description: "Learn more about: Package XML Schema V90"
title: "Package XML Schema V90 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fba29233-28b1-46e7-b5f6-1b1b15766f44
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Package XML Schema V90
Microsoft HIS 2013(V9) supports both the old and new format, which includes an associated XML schema for validating the XML document. Microsoft HIS 2009 and HIS 2010 (V8.5) support the old format only.  
  
 The Microsoft static SQL for DB2 custom package XML file contains multiple elements to inform the DRDA Client and DRDA Server how to execute the DRDA commands BGNBND (Begin Binding a Package to an RDB) with BNDOPT (Bind Options) and BNDSQLSTT (Bind SQL Statement to an RDB Package). The HostIntegrationStaticSql.xsd describes the XML elements, attributes and values that you can define to describe the static SQL package bind options, package name, package sections, statements, parameters, and result sets. The following XML listing is an example of the custom package XML.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<hostIntegration.staticSql xmlns="http://schemas.microsoft.com/his/StaticSql/2012">  
  
  <options bindAllowErrors="Validate"  
            bindAuthorizationKeep="true"  
            bindCheck="true"  
            bindReplace="true"  
            bindReplaceVersion=""  
            packageCcsidSbc="1208"  
            packageCcsidDbc="1208"  
            packageCcsidMbc="1200"  
            packageCharacterSubtype="Bit"  
            packageDecimalPrecision="15"  
            packageExecuteAuthorization="Requester"  
            bindExplain="AllExplainable"  
            packageIsolationLevel="RepeatableRead"  
            packageOwnerIdentifier=""  
            relationalDatabaseName=""  
            statementDateFormat="MdyHyphen"  
            statementDecimalDelimiter="Period"  
            defaultRdbCollection=""  
            releaseRelationalDatabase="Commit"  
            parallelProcessDegree="1"  
            keepPreparedStatement="None"  
            statementQueryProtocol="FixedRow"  
            statementStringDelimiter="Apostrophe"  
            statementTimeFormat="HmsColon"/>  
  
  <packages>  
    <package token="18BBB2BA1492DAC8"   
             version=""   
             collection="DSN8910"   
             id="DSN8HC3"   
             isolationLevel="RepeatableRead">  
      <sections>  
        <section number="1" alias="">  
          <statement number="1" sqlStatement="DECLARE CURDEPTLOC CURSOR FOR SELECT LOCATION FROM VHDEPT WHERE DEPTNO = :H AND LOCATION = CURRENT SERVER"/>  
            <parameters>  
              <parameter name="p00" nullable="false">  
                <smallInt length="2"/>  
              </parameter>  
              <parameter name="p01" nullable="false">  
                <int length="4" />  
              </parameter>  
              <parameter name="p02" nullable="false">  
                <bigInt length="8" />  
              </parameter>  
              <parameter name="p13" nullable="false">  
                <single length="4"/>  
              </parameter>  
              <parameter name="p14" nullable="false">  
                <double length="8"/>  
              </parameter>  
              <parameter name="p15" nullable="false">  
                <float length="8"/>  
              </parameter>  
              <parameter name="p16" nullable="false">  
                <real length="4" />  
              </parameter>  
              <parameter name="p17" nullable="false">  
                <date length="10"/>  
              </parameter>  
              <parameter name="p18" nullable="false">  
                <time length="8"/>  
              </parameter>  
              <parameter name="p19" nullable="false">  
                <timestamp length="26"/>  
              </parameter>  
              <parameter name="p03" nullable="false">  
                <char length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p04" nullable="false">  
                <charForBit length="1"/>  
              </parameter>  
              <parameter name="p05" nullable="false">  
                <varChar length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p06" nullable="false">  
                <varCharForBit length="1"/>  
              </parameter>  
              <parameter name="p07" nullable="false">  
                <graphic length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p08" nullable="false">  
                <varGraphic length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p09" nullable="false">  
                <blob length="1"/>  
              </parameter>  
              <parameter name="p10" nullable="false">  
                <clob length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p11" nullable="false">  
                <decimal precision="9" scale="4"/>  
              </parameter>  
              <parameter name="p12" nullable="false">  
                <numeric precision="9" scale="4"/>  
              </parameter>  
            </parameters>  
          <resultSet>  
            <columns>  
              <column name="p00" ordinal="0"/>  
              <column name="p01" ordinal="1"/>  
              <column name="p02" ordinal="2"/>  
              <column name="p03" ordinal="3"/>  
              <column name="p04" ordinal="4"/>  
              <column name="p05" ordinal="5"/>  
              <column name="p06" ordinal="6"/>  
              <column name="p07" ordinal="7"/>  
              <column name="p08" ordinal="8"/>  
              <column name="p09" ordinal="9"/>  
              <column name="p10" ordinal="10"/>  
              <column name="p11" ordinal="11"/>  
            </columns>  
          </resultSet>  
        </section>  
        <section number="2" alias="">  
          <statement number="2" sqlStatement="DECLARE CURDEPTLOC CURSOR FOR SELECT LOCATION FROM VHDEPT WHERE DEPTNO = :H AND LOCATION = CURRENT SERVER"/>  
            <parameters>  
              <parameter name="p00" nullable="false">  
                <smallInt length="2"/>  
              </parameter>  
              <parameter name="p01" nullable="false">  
                <int  length="4" />  
              </parameter>  
              <parameter name="p02" nullable="false">  
                <bigInt  length="8" />  
              </parameter>  
              <parameter name="p13" nullable="false">  
                <single length="4"/>  
              </parameter>  
              <parameter name="p14" nullable="false">  
                <double length="8"/>  
              </parameter>  
              <parameter name="p15" nullable="false">  
                <float length="8"/>  
              </parameter>  
              <parameter name="p16" nullable="false">  
                <real length="4" />  
              </parameter>  
              <parameter name="p17" nullable="false">  
                <date length="10"/>  
              </parameter>  
              <parameter name="p18" nullable="false">  
                <time length="8"/>  
              </parameter>  
              <parameter name="p19" nullable="false">  
                <timestamp length="26"/>  
              </parameter>  
              <parameter name="p03" nullable="false">  
                <char length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p04" nullable="false">  
                <charForBit length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p05" nullable="false">  
                <varChar length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p06" nullable="false">  
                <varCharForBit length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p07" nullable="false">  
                <graphic length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p08" nullable="false">  
                <varGraphic length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p09" nullable="false">  
                <blob length="1" ccsid="65535"/>  
              </parameter>  
              <parameter name="p10" nullable="false">  
                <clob length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p11" nullable="false">  
                <decimal precision="9" scale="4"/>  
              </parameter>  
              <parameter name="p12" nullable="false">  
                <numeric precision="9" scale="4"/>  
              </parameter>  
            </parameters>  
          <resultSet>  
            <columns>  
              <column name="p00" ordinal="0"/>  
              <column name="p01" ordinal="1"/>  
              <column name="p02" ordinal="2"/>  
              <column name="p03" ordinal="3"/>  
              <column name="p04" ordinal="4"/>  
              <column name="p05" ordinal="5"/>  
              <column name="p06" ordinal="6"/>  
              <column name="p07" ordinal="7"/>  
              <column name="p08" ordinal="8"/>  
              <column name="p09" ordinal="9"/>  
              <column name="p10" ordinal="10"/>  
              <column name="p11" ordinal="11"/>  
            </columns>  
          </resultSet>  
        </section>  
        <section number="3" alias="">  
          <statement number="3" sqlStatement="DECLARE CURDEPTLOC CURSOR FOR SELECT LOCATION FROM VHDEPT WHERE DEPTNO = :H AND LOCATION = CURRENT SERVER"/>  
            <parameters>  
              <parameter name="p00" nullable="false">  
                <smallInt length="2"/>  
              </parameter>  
              <parameter name="p01" nullable="false">  
                <int  length="4" />  
              </parameter>  
              <parameter name="p02" nullable="false">  
                <bigInt  length="8" />  
              </parameter>  
              <parameter name="p13" nullable="false">  
                <single length="4"/>  
              </parameter>  
              <parameter name="p14" nullable="false">  
                <double length="8"/>  
              </parameter>  
              <parameter name="p15" nullable="false">  
                <float length="8"/>  
              </parameter>  
              <parameter name="p16" nullable="false">  
                <real length="4" />  
              </parameter>  
              <parameter name="p17" nullable="false">  
                <date length="10"/>  
              </parameter>  
              <parameter name="p18" nullable="false">  
                <time length="8"/>  
              </parameter>  
              <parameter name="p19" nullable="false">  
                <timestamp length="26"/>  
              </parameter>  
              <parameter name="p03" nullable="false">  
                <char length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p04" nullable="false">  
                <charForBit length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p05" nullable="false">  
                <varChar length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p06" nullable="false">  
                <varCharForBit length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p07" nullable="false">  
                <graphic length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p08" nullable="false">  
                <varGraphic length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p09" nullable="false">  
                <blob length="1" ccsid="65535"/>  
              </parameter>  
              <parameter name="p10" nullable="false">  
                <clob length="1" ccsid="1208"/>  
              </parameter>  
              <parameter name="p11" nullable="false">  
                <decimal precision="9" scale="4"/>  
              </parameter>  
              <parameter name="p12" nullable="false">  
                <numeric precision="9" scale="4"/>  
              </parameter>  
            </parameters>  
          <resultSet>  
            <columns>  
              <column name="p00" ordinal="0"/>  
              <column name="p01" ordinal="1"/>  
              <column name="p02" ordinal="2"/>  
              <column name="p03" ordinal="3"/>  
              <column name="p04" ordinal="4"/>  
              <column name="p05" ordinal="5"/>  
              <column name="p06" ordinal="6"/>  
              <column name="p07" ordinal="7"/>  
              <column name="p08" ordinal="8"/>  
              <column name="p09" ordinal="9"/>  
              <column name="p10" ordinal="10"/>  
              <column name="p11" ordinal="11"/>  
            </columns>  
          </resultSet>  
        </section>  
      </sections>  
    </package>  
  </packages>  
  
</hostIntegration.staticSql>  
```  
  
## Options Element  
 The **Options** element contains a set of optional attributes that define the values for the BNDOPT (Bind Options) when executing the DRDA command BGNBND (Begin Binding a Package to an RDB).  
  
### Bind Package Creation Control  
 The bindAllowErrors attribute informs the DRDA Server whether errors are allowed during package binding. This optional attribute accepts a string value.  
  
 A value of **Yes** instructs the DRDA Server to allow errors and continue binding the package.  
  
 A value of **No** instructs the DRDA Server that no errors are allowed.  
  
 A value of **Validate** instructs the DRDA Server to validate the bind request only.  
  
 The default value is **No**.  
  
### Package Authorization Option  
 The **bindAuthorizationKeep** attribute informs the DRDA Server whether to keep or revoke package authorizations when the package is replaced. This optional attribute accepts a Boolean value. The default value is true.  
  
### Bind Existence Checking  
 The **bindCheck** attribute informs the DRDA Server whether to return an error when checking for the existence of database objects and authorities referenced in a package statement. This optional attribute accepts a Boolean value. The default value is false.  
  
### Package Replacement Option  
 The **bindReplace** attribute instructs the DRDA Server whether the bind should replace the existing package. This optional attribute accepts a Boolean value. The default value is true.  
  
### Replaced Package Version Name  
 The **bindReplaceVersion** attribute defines the package version name of the package that the DRDA Server should replace. This optional attribute accepts a string value. There is no default value for this element.  
  
### Package Default SBCS CCSID for a Column  
 The **packageCcsidSbc** informs the DRDA Server which Code Character Set Identifier for Single-Byte Characters to use when executing a SQL CREATE or ALTER table statement. This optional attribute accepts an integer value. The default value is 1208.  
  
### Package Default DBCS CCSID for a Column  
 The **packageCcsidDbc** informs the DRDA Server which Code Character Set Identifier for Double-Byte Characters to use when executing a SQL CREATE or ALTER table statement. This optional attribute accepts an integer value. The default value is 1200.  
  
### Package Default MBCS CCSID for a Column  
 The **packageCcsidMbc** informs the DRDA Server which Code Character Set Identifier for Mixed-Byte Characters to use when executing a SQL CREATE or ALTER table statement. This optional attribute accepts an integer value. The default value is 1208.  
  
### Package Default Character Subtype  
 The **packageCharacterSubtype** attribute informs the DRDA Server which character subtype to use when executing a SQL CREATE or ALTER table statement. This optional attribute accepts a string value. The default value is Default.  
  
|Value|Description|  
|-|-|  
|Bit|CHAR FOR BIT DATA|  
|Default|System default|  
|MBCS|Mixed-Byte Character Set|  
|SBCS|Single-Byte Character Set|  
  
### Decimal Precision  
 The **packageDecimalPrecision** attribute informs the DRDA Server the default decimal precision. This optional attribute accepts an integer value of 15, 16, 31 or 63. The default value is 15.  
  
> [!NOTE]
>  When connecting to IBM DB2 for i5/OS, you should not specify this attribute.  
  
### Package Authorization Rules  
 The **packageExecuteAuthorization** attribute informs the DRDA Server which authorization identifier to use when executing dynamic SQL statements. This optional element attribute a string value. The default value is **Requester**.  
  
|Value|Description|  
|-|-|  
|Requester|Instructs the DRDA Server to use the DRDA requester authorization|  
|Owner|Instructs the DRDA Server to use the package owner authorization|  
|InvokerRevertToRequester|Instructs the DRDA Server to use the authorization of the invoker of a function or stored procedure, otherwise use the DRDA requester authorization|  
|InvokerRevertToOwner|Instructs the DRDA Server to use the authorization of the invoker of a function or stored procedure, otherwise use the package owner authorization|  
|DefinerRevertToRequester|Instructs the DRDA Server to use the authorization of the creator of a function or stored procedure, otherwise use the DRDA requester authorization|  
|DefinerRevertToOwner|Instructs the DRDA Server to use the authorization of the creator of a function or stored procedure, otherwise use the package owner authorization|  
  
### Bind Explain Option  
 The **bindExplain** attribute informs the DRDA Server whether to produce explanatory information for explainable database objects. This optional attribute accepts a string value.  
  
 A value of **ExplainNone** instructs the DRDA Server to not produce explanatory information.  
  
 A value of **ExplainAll** instructs the DRDA Server to explain all statements.  
  
 A value of **ExplainStatic** instructs the DRDA Server to explain static SQL statements only.  
  
 The default value is **ExplainNone**.  
  
> [!NOTE]
>  When connecting to IBM DB2 for i5/OS and DB2 for LUW, you should specify a value of **ExplainNone** only.  
  
### Package Isolation Level  
 The **packageIsolationLevel** attribute instructs the DRDA Server to bind the package with the requested DRDA PKGISOLVL (Package Isolation Level). This required attribute accepts a string value. The default value is **ReadCommitted**.  
  
|Value|Description|  
|-|-|  
|ReadCommitted|ANSI READ COMMITTED<br /><br /> DRDA ISOLVLCS (Isolation Level Cursor Stability)<br /><br /> IBM DB2 CURSOR STABILITY (CS)<br /><br /> IBM DB2 for i5/OS COMMIT(*CS)<br /><br /> Microsoft .NET Framework ReadCommitted|  
|Serializable|ANSI SERIALIZABLE<br /><br /> DRDA ISOLVLRR (Isolation Level Repeatable Read)<br /><br /> IBM DB2 REPEATABLE READ (RR)<br /><br /> IBM DB2 for i5/OS COMMIT(*RR)<br /><br /> Microsoft .NET Framework Serializable|  
|RepeatableRead|ANSI REPEATABLE READ<br /><br /> DRDA ISOLVLALL (Isolation Level All)<br /><br /> IBM DB2 READ STABILITY (RS)<br /><br /> IBM DB2 for i5/OS COMMIT(*RS)<br /><br /> Microsoft .NET Framework RepeatableRead|  
|ReadUncommitted|ANSI READ UNCOMMITTED<br /><br /> DRDA ISOLVLCHG (Isolation Level Change)<br /><br /> IBM DB2 UNCOMMITTED READ (UR)<br /><br /> IBM DB2 for i5/OS COMMIT(*UR)<br /><br /> Microsoft .NET Framework ReadUncommitted|  
|NoCommit|DRDA ISOLVLNC (Isolation Level No Commit)<br /><br /> IBM DB2 for i5/OS COMMIT(*NC)|  
  
### Package Owner Identifier  
 The **packageOwnerIdentifier** attribute instructs the DRDA Server which authorization identifier is the owner of the package. This optional attribute accepts a string value. There is no default value for this element.  
  
### Statement Date Format  
 The **statementDateFormat** element informs the DRDA Server which statement date format to use in SQL statements. This optional element accepts a string value. The default value is **Default**.  
  
|Value|Format|Description|  
|-|-|-|  
|Iso|yyyy-mm-dd|ISO date format|  
|Usa|mm/dd/yyyy|USA date format|  
|Eur|dd.mm.yyyy|EUR date format|  
|Jis|yyyy-mm-dd|JIS date format|  
|Default|NA|Default date format|  
|Local|NA|Local date format|  
|DmyBlank|dd mm yy|Day Month Year with blank separator|  
|DmyComma|dd,mm,yy|Day Month Year with comma separator|  
|DmyHyphen|dd-mm-yy|Day Month Year with hyphen separator|  
|DmyPeriod|dd.mm.yy|Day Month Year with period separator|  
|DmySlash|dd/mm/yy|Day Month Year with slash separator|  
|JulBlank|yy ddd|Julian with blank separator|  
|JulComma|yy,ddd|Julian with comma separator|  
|JulHyphen|yy-ddd|Julian with hyphen separator|  
|JulPeriod|yy.ddd|Julian with period separator|  
|JulSlash|yy/ddd|Julian with slash separator|  
|MdyBlank|mm dd yy|Month Day Year with blank separator|  
|MdyComma|mm,dd,yy|Month Day Year with comma separator|  
|MdyHyphen|mm-dd-yy|Month Day Year with hyphen separator|  
|MdyPeriod|mm.dd.yy|Month Day Year with period separator|  
|MdySlash|mm/dd/yy|Month Day Year with slash separator|  
|YmdBlank|yy mm dd|Year Month Day with blank separator|  
|YmdComma|yy,mm,dd|Year Month Day with comma separator|  
|YmdHyphen|yy-mm-dd|Year Month Day with hyphen separator|  
|YmdPeriod|yy.mm.dd|Year Month Day with period separator|  
|YmdSlash|yy/mm/dd|Year Month Day with slash separator|  
  
### Statement Decimal Delimiter  
 The **statementDecimalDelimiter** attribute informs the DRDA Server which statement decimal delimiter to use in SQL statements. This optional attribute accepts a string value. The default value is System.  
  
|Value|Description|  
|-|-|  
|Period|Indicates a period|  
|Comma|Indicates a comma|  
|Package|Indicates package default, when rebinding package|  
|System|Indicates the system default|  
  
### Default RDB Collection ID  
 The **defaultRdbCollection** attribute informs the DRDA Server what default collection identifier to use to complete unqualified database object names. This optional attribute accepts a string value. There is no default value. IBM DB2 for z/OS accepts a 128-byte string. IBM DB2 for i5/OS accepts a 10-byte string. IBM DB2 for LUW accepts a 30-byte string.  
  
### Release Database Object Resources  
 The **releaseDatabaseResources** attribute informs the DRDA Server when to release database object resources such as locks that are associated with the package execution. This optional attribute accepts a string value. A value of Commit instructs the DRDA Server to release database object resources when processing a transaction commit. A value of **Deallocation** instructs the DRDA Server to release database object resources when de-allocating the session. The default value is **Commit**.  
  
### Degree of IO Parallelism  
 The **parallelProcessDegree** attribute informs the DRDA Server to what degree to utilize I/O parallel processing for bound statements. This optional attribute accepts an integer value of -1 to 32676. A value of 1 instructs the DRDA Server that no IO parallel processing is required. A value of -1 instructs the DRDA Server to apply whatever degree of IO parallel processing is appropriate. The default value is 1.  
  
### Keep Prepared Statement  
 The **keepPreparedStatement** attribute instructs the DRDA Server to keep prepared dynamic SQL statements until released. This optional attribute accepts a string value. The default value is **None**.  
  
|Value|Description|  
|-|-|  
|None|Indicates statements are released during commit and rollback|  
|Commit|Indicates statements are kept during commit, but released during rollback|  
|Rollback|Indicates statements are released during commit, but kept during rollback|  
|All|Indicates statements are kept during commit and rollback|  
  
### Query Block Protocol Control  
 The **statementQueryProtocol** attribute instructs the DRDA Server what type of query block protocol to use when returning results on a query. This optional attribute accepts a string value. The default value is **FixedRow**.  
  
|Value|Description|  
|-|-|  
|FixedRow|Indicates fixed row query protocol|  
|LimitedBlock|Indicates limited block query protocol|  
|ForceFixedRow|Indicates force fixed row query protocol|  
  
### Statement String Delimiter  
 The **statementStringDelimiter** attribute informs the DRDA Server which statement string delimiter to use in SQL statements. This optional attribute accepts a string value. The default value is System.  
  
|Value|Description|  
|-|-|  
|Apostrophe|Indicates an apostrophe|  
|DoubleQuote|Indicates a double quote|  
|Package|Indicates package default, when rebinding package|  
|System|Indicates the system default|  
  
### Statement Time Format  
 The **statementTimeFormat** attribute informs the DRDA Server which statement time format to use in SQL statements. This optional attribute accepts a string value. The default value is **Iso**.  
  
|Value|Format|Description|  
|-|-|-|  
|Iso|hh.mm.ss|ISO time format|  
|Usa|hh:mm:ss AM|USA time format AM &#124; PM|  
|Eur|hh.mm.ss|EUR time format|  
|Jis|hh:mm:ss|JIS time format|  
|Default|NA|Default time format|  
|Local|NA|Local time format|  
|HmsBlank|hh mm ss|Hour Minute Second with blank separator|  
|HmsColon|hh:mm:ss|Hour Minute Second with colon separator|  
|HmsComma|hh,mm,ss|Hour Minute Second with comma separator|  
|HmsPeriod|hh.mm.ss|Hour Minute Second with period separator|  
  
## Packages Element  
 The packages element contains one or more package elements that define the values when executing the DRDA command BGNBND (Begin Binding a Package to an RDB).  
  
## Package Element  
 The package element contains a set of attributes and a sections element.  
  
### Collection Identifier  
 The **collectionIdentifier** attribute corresponds to the DRDA RDBCOLID (RDB Collection Identifier) and instructs the DRDA Server into which collection to bind the package. This optional element accepts a string value. There is no default value. IBM DB2 for z/OS accepts a 128-byte string. IBM DB2 for i5/OS accepts a 10-byte string. IBM DB2 for LUW accepts a 30-byte string.  
  
> [!NOTE]
>  DRDA defines a fully-qualified static SQL package using a PKGNAM (RDB Package Name) that consists of these multiple parts.  
  
-   RDBNAM (Relational Database Name)  
  
-   RDBCOLID (RDB Collection Identifier)  
  
-   PKGID (RDB Package Identifier)  
  
```  
RDBNAME.RDBCOLID.PKGID.PKGCNSTKN.PKGSN  
```  
  
 The previous example shows a fully-qualified package name with consistency token.  
  
### Package Identifier  
 The **packageIdentifier** attribute corresponds to the DRDA PKGID (RDB Package Identifier) and informs the DRDA Server what is the package identifier. This required element accepts a string value. There is no default value. IBM DB2 accepts a 128-byte string.  
  
### Consistency Token  
 The **consistencyToken** attribute corresponds to the DRDA PKGCNSTKN (RDB Package Consistency Token) and informs the DRDA Server what is the package consistency token. This optional element accepts a string value. There is no default value. IBM DB2 supports an 8-byte string.  
  
> [!NOTE]
>  If more than one package has the same value for PKGNAM, then the packages are distinguished by the VRSNAM (Version Name) or PKGCNSTKN (package name consistency token).  
  
 PKGCNSTKN (RDB Package Consistency Token)  
  
 VRSNAM (Version Name)  
  
### Version Name  
 The **versionName** attribute corresponds to the DRDA VRSNAM (Version Name) and informs the DRDA Server what is the package version name. This optional element accepts a string value. The default value is null. IBM DB2 supports a 254-byte string.  
  
### Package Title  
 The Title attribute corresponds to the DRDA TITLE (Title) and instructs the DRDA Server to bind the package with a descriptive comment. This optional element accepts a string value. There is no default value. DRDA supports a 254-byte string.  
  
## Sections Element  
 The sections element contains one or more section elements that define the values when executing the DRDA command BGNBND (Begin Binding a Package to an RDB).  
  
## Section Element  
 The section element contains a set of attributes, a required statement element, and an optional resultSet element.  
  
### Section Number  
 The **packageSectionNumber** attribute corresponds to the DRDA PKGSN (RDB Package Section Number) and instructs the DRDA Server to bind the section as this number. This optional attribute accepts an integer value and must be unique within the Package element. There is no default value.  
  
### Section Alias  
 The **packageSectionAlias** attribute instructs the Microsoft DRDA Client to locate a package section based on an alias name. This optional element accepts an 8-byte string value. There is no default value.  
  
> [!NOTE]
>  See Programmer’s Reference for Microsoft.HostIntegration.MsDb2Client.MsDb2Connection SetCustomPackageData.  
  
## Statement Element  
 The Statement element contains a set of attributes, and an optional parameters element.  
  
### Statement Number  
 The **sqlStatementNumber** attribute corresponds to the DRDA SQLSTTNBR (SQL Statement Number) and instructs the DRDA Server to bind the statement as this number, which is a reference to the statement embedded within the source application. This optional attribute accepts an integer value and must be unique within the Package element. There is no default value.  
  
### SQL Statement Assumptions  
 The **sqlStatementAssumptions** attribute corresponds to the DRDA BNDSTTASM (Bind SQL Statement Assumptions) and instructs the DRDA Server to bind the statement with these assumptions. This optional attribute accepts a Boolean value. A value of Yes indicates the source server successfully classified the statement during the program precompile preparation process. A value of No indicates the source server made assumptions for a statement that it could not classify. The default value is Yes.  
  
### SQL Statement Command Text  
 The **sqlStatement** attribute corresponds to the DRDA SQLSTT (SQL Statement) and instructs the DRDA Server to bind the statement to the package with this SQL statement command text. This required element accepts a string value. There is no default value. DB2 accepts a 2,097,152-byte string.  
  
## Parameters Element  
 The **parameters** element contains one or more parameter elements.  
  
## Parameter Element  
 The **parameter** element contains a set of attributes that correspond to the DRDA SQLSTTVRB (SQL Statement Variable Descriptions), and type element.  
  
> [!NOTE]
>  The parameter elements must be defined in the same order as the variables in the SQL statement.  
  
### Parameter Name  
 The **name** attribute instructs the DRDA Server what is the name of the parameter. This required attribute accepts a string value. There is no default value. IBM DB2 supports a 128-byte string.  
  
### Parameter Nullability  
 The **nullable** attribute instructs the DRDA Server whether the parameter value is nullable. This required attribute accepts a Boolean value. The default value is true.  
  
## Parameter Type  
 The **type** element instructs the DRDA Server what is the type of the parameter. This required attribute accepts a string value. There is no default value.  
  
### Parameter Length  
 The **length** attribute instructs the DRDA Server what is the length of the parameter. This required attribute accepts an integer value. There is no default value.  
  
### Parameter Precision  
 The precision attribute instructs the DRDA Server what is the precision of the parameter. This required attribute accepts an integer value. There is no default value.  
  
### Parameter Scale  
 The **scale** attribute instructs the DRDA Server what is the scale of the parameter. This required attribute accepts an integer value. There is no default value.  
  
### Parameter Coded Character Set Identifier  
 The **ccsid** attribute instructs the DRDA Server what is the Coded Character Set Identifier of the parameter. This required attribute accepts an integer value. There is no default value.  
  
## ResultSet Element  
 The optional **resultSet** element contains a columns element, which informs the DRDA Client what are the expected order and data types of columns in the result set.  
  
> [!NOTE]
>  The MsDb2Client provider uses this information to return a result set to the consumer program, including the correct metadata for the column names and data types. Optionally, configure the MsDb2Client connection string argument “Use Early Metadata=False” to instruct the MsDb2Client to ignore the design-time metadata defined in the ResultSet portion of the static SQL for DB2 XML file, and then use the late metadata returned by the DRDA Server.  
  
## Columns Element  
 The **columns** element contains one or more column elements.  
  
## Column Element  
 The **column** element contains a set of attributes.  
  
### Column Ordinal  
 The **ordinal** attribute identifies the place of the column within the result set. This required attribute accepts an integer value. There is no default value.  
  
### Column Name  
 The **name** attribute instructs the DRDA Server what is the name of the column. This required attribute accepts a string value. There is no default value. IBM DB2 supports a 128-byte string.  
  
### Column Nullability  
 The **nullable** attribute instructs the DRDA Server whether the column value is nullable. This required attribute accepts a Boolean value. The default value is true.  
  
## Column Type  
 The **type** element instructs the DRDA Server what is the type of the column. This required attribute accepts a string value. There is no default value.  
  
### Column Length  
 The **Length** attribute instructs the DRDA Server what is the length of the column. This required attribute accepts an integer value. There is no default value.  
  
### Column Precision  
 The **Precision** attribute instructs the DRDA Server what is the precision of the column. This required attribute accepts an integer value. There is no default value.  
  
### Column Scale  
 The **Scale** attribute instructs the DRDA Server what is the scale of the column. This required attribute accepts an integer value. There is no default value.  
  
### Column Coded Character Set Identifier  
 The **CCSID** attribute instructs the DRDA Server what is the Coded Character Set Identifier of the column. This required attribute accepts an integer value. There is no default value.  
  
## Reference Tables  
  
### Data Types  
 The following table lists data types and lengths for use in defining parameter and columns in the static SQL for DB2 XML file format V85.  
  
|Type|Length|Description|  
|-|-|-|  
|bigint|8|A 64-bit signed integer.|  
|char||A character string.|  
|charForBit||A binary string.|  
|date|10|Date and time data ranging in value from January 1, 1753 to December 31, 9999 to an accuracy of 3.33 milliseconds.|  
|decimal||A simple type representing values ranging from 1.0 x 10 -28 to approximately 7.9 x 10 28 with 28-29 significant digits.|  
|double|8|A floating point number within the range of -1.79E +308 through 1.79E +308.|  
|graphic||A double-byte character string.|  
|int|4|A 32-bit signed integer, with values between -2147483648 and 2147483647.|  
|numeric||An exact numeric value with a fixed precision and scale.|  
|real|4|Signed, approximate, numeric value with a binary precision 24 (zero or absolute value 10[–38] to 10[38]).|  
|smallint|2|A 16-bit signed integer, with values between -32768 and 32767.|  
|time|8.|Date and time data ranging in value from January 1, 1753 to December 31, 9999 to an accuracy of 3.33 milliseconds.|  
|timestamp|26|Data and time data in the format YYYY-MM-DD-hh.mm.ss.tttttt.|  
|varChar||A variable-length character string.|  
|varCharForBit||A variable-length binary string.|  
|varGraphic||A double-byte character string.|  
  
### Coded Character Set Identifiers  
 The following table lists data types and lengths for use in defining options, parameter and columns in the static SQL for DB2 XML file format V85.  
  
|Type|Group|CCSID|NLS|Description|  
|-|-|-|-|-|  
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
  
> [!NOTE]
>  The Microsoft ADO.NET Data Provider for DB2 supports a set of Coded Character Set Identifiers. IBM DB2 database servers for z/OS and i5/OS typically use EBCDIC. For more information, see
