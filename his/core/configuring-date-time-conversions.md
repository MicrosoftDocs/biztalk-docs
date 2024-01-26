---
description: "Learn more about: Configuring Date Time Conversions"
title: "Configuring Date Time Conversions"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Date Time Conversions
The DRDA Service will format string literal date time values from source and into target formats when processing dynamic and static SQL statements, for specific date time and character data types. The **conversionFormats** element contains dateMasks, timeMasks, and dateTimeMasks for converting to and from DB2 and SQL Server datetime formats.  
  
1.  When reading data from DB2 and writing to SQL Server, the MsDrdaService will read string literal values that match source DB2 formats specified in the app config, and then write string literal values into the default SQL Server format.  
  
2.  When reading data from SQL Server and writing to DB2, the MsDrdaService will read string literal values that match known input formats, and then write string literal values into the DB2 target format specified in the app config.  
  
    ```  
    <conversionFormats>  
                <dateTimeMasks>  
                </dateTimeMasks>  
  
                <timeMasks>  
                </timeMasks>  
  
                <dateMasks>  
                </dateMasks>  
              </conversionFormats>  
  
    ```  
  
### Date  
 The DRDA Service will process string literal date values within DB2 and SQL Server DATE, CHAR (10), and VARCHAR (10) data types, to convert from DB2 date format to SQL Server date format, and to convert from SQL Server date format to DB2 date format. The **dateMasks** contains one or more dateMask elements to define date mappings. The **dateMask** element contains a **db2ToSql** or **sqlToDb2** to indicate the direction, and a **sourceFormat** and a **targetFormat** to specify the mapping. The **db2ToSql** defines the direction from DB2 to SQL Server. The **sqlToDb2** defines the direction from SQL Server to DB2.  
  
#### DB2 DATE to SQL Server date  
 When reading data from DB2 and writing to SQL Server, the MsDrdaService will read string literal DB2 date values that match input DB2 date source formats specified in the app config, and then write string literal SQL Server date values into the default SQL Server date format.  
  
```  
<dateMask>  
                <db2ToSql sourceFormat="YmdHyphen"/>  
              </dateMask>  
```  
  
 *DRDA Service will process strings to match the input DB2 date source format YYYY-MM-DD.*  
  
 The **sourceFormat** attribute defines the format of the source string that the DRDA Service should identify as an input string literal date value. This **optional** attribute accepts an **enumerated** value. The default is **YmdHyphen**.  
  
|Format Name|Format Mask|Description|  
|-----------------|-----------------|-----------------|  
|ISO|yyyy-mm-dd|ISO date format seperator|  
|Usa|mm/dd/yyyy|USA date format seperator|  
|Eur|dd.mm.yyyy|EUR date format seperator|  
|Jis|yyyy-mm-dd|JIS date format seperator|  
|DmyBlank|dd mm yy|Day Month Year with blank seperator|  
|DmyComma|dd,mm,yy|Day Month Year with comma seperator|  
|DmyHyphen|dd-mm-yy|Day Month Year with hyphen seperator|  
|DmyPeriod|dd.mm.yy|Day Month Year with period seperator|  
|DmySlash|dd/mm/yy|Day Month Year with slash seperator|  
|JulBlank|yy ddd|Julian with blank seperator|  
|JulComma|yy,ddd|Julian with comma seperator|  
|JulHyphen|yy-ddd|Julian with hyphen seperator|  
|JulPeriod|yy.ddd|Julian with period seperator|  
|JulSlash|yy/ddd|Julian with slash seperator|  
|MdyBlank|mm dd yy|Month Day Year with blank seperator|  
|MdyComma|mm,dd,yy|Month Day Year with comma seperator|  
|MdyHyphen|mm-dd-yy|Month Day Year with hyphen seperator|  
|MdyPeriod|mm.dd.yy|Month Day Year with period seperator|  
|MdySlash|mm/dd/yy|Month Day Year with slash seperator|  
|YmdBlank|yy mm dd|Year Month Day with blank seperator|  
|YmdComma|yy,mm,dd|Year Month Day with comma seperator|  
|YmdHyphen|yy-mm-dd|Year Month Day with hyphen seperator|  
|YmdPeriod|yy.mm.dd|Year Month Day with period seperator|  
|YmdSlash|yy/mm/dd|Year Month Day with slash seperator|  
  
 *Supported sourceFormat attribute values for use with db2ToSql dateMask conversion.*  
  
#### SQL Server date to DB2 DATE  
 When reading data from SQL Server and writing to DB2, the MsDrdaService will read string literal date values that match known input SQL Server date formats, and then write string literal date values into the DB2 date target format specified in the app config.  
  
```  
<dateMask>  
                <sqlToDb2 targetFormat="YmdHyphen"/>  
              </dateMask>  
  
```  
  
 *DRDA Service will process strings to match the DB2 date target format YYYY-MM-DD.*  
  
 The **targetFormat** attribute defines the format of the target string that the DRDA Service should produce as an output string literal date value. This **optional** attribute accepts an **enumerated** value. The default is **YmdHyphen**.  
  
|Format Name|Format Mask|Description|  
|-----------------|-----------------|-----------------|  
|ISO|yyyy-mm-dd|ISO date format seperator|  
|Usa|mm/dd/yyyy|USA date format seperator|  
|Eur|dd.mm.yyyy|EUR date format seperator|  
|Jis|yyyy-mm-dd|JIS date format seperator|  
|DmyBlank|dd mm yy|Day Month Year with blank seperator|  
|DmyComma|dd,mm,yy|Day Month Year with comma seperator|  
|DmyHyphen|dd-mm-yy|Day Month Year with hyphen seperator|  
|DmyPeriod|dd.mm.yy|Day Month Year with period seperator|  
|DmySlash|dd/mm/yy|Day Month Year with slash seperator|  
|JulBlank|yy ddd|Julian with blank seperator|  
|JulComma|yy,ddd|Julian with comma seperator|  
|JulHyphen|yy-ddd|Julian with hyphen seperator|  
|JulPeriod|yy.ddd|Julian with period seperator|  
|JulSlash|yy/ddd|Julian with slash seperator|  
|MdyBlank|mm dd yy|Month Day Year with blank seperator|  
|MdyComma|mm,dd,yy|Month Day Year with comma seperator|  
|MdyHyphen|mm-dd-yy|Month Day Year with hyphen seperator|  
|MdyPeriod|mm.dd.yy|Month Day Year with period seperator|  
|MdySlash|mm/dd/yy|Month Day Year with slash seperator|  
|YmdBlank|yy mm dd|Year Month Day with blank seperator|  
|YmdComma|yy,mm,dd|Year Month Day with comma seperator|  
|YmdHyphen|yy-mm-dd|Year Month Day with hyphen seperator|  
|YmdPeriod|yy.mm.dd|Year Month Day with period seperator|  
|YmdSlash|yy/mm/dd|Year Month Day with slash seperator|  
  
 *Supported targetFormat attribute values for use with sqlToDb2 dateMask conversion.*  
  
### Time  
 The DRDA Service will process string literal time values within DB2 and SQL Server TIME, CHAR (8), and VARCHAR (8) data types, to convert from DB2 time format to SQL Server time format, and to convert from SQL Server time format to DB2 time format. The **timeMasks** contains one or more timeMask elements to define time mappings. The **timeMask** element contains a **db2ToSql** or **sqlToDb2** to indicate the direction, and a **sourceFormat** and a **targetFormat** to specify the mapping. The **db2ToSql** defines the direction from DB2 to SQL Server. The **sqlToDb2** defines the direction from SQL Server to DB2.  
  
#### DB2 TIME to SQL Server time  
 When reading data from DB2 and writing to SQL Server, the MsDrdaService will read string literal DB2 time values that match input DB2 time source formats specified in the app config, and then write string literal SQL Server time values into the default SQL Server time format.  
  
```  
<timeMask>  
                <db2ToSql sourceFormat="HmsColon"/>  
              </timeMask>  
```  
  
 DRDA Service will process strings to match the input DB2 time source format HH:MM:SS.  
  
 The **sourceFormat** attribute defines the format of the source string that the DRDA Service should identify as an input string literal time value. This **optional** attribute accepts an **enumerated** value. The default is **HmsColon**.  
  
|Format Name|Format Mask|Description|  
|-----------------|-----------------|-----------------|  
|HmsBlank|hh mm ss|Hour Minute Second with blank separator|  
|HmsColon|hh:mm:ss|Hour Minute Second with colon separator|  
|HmsComma|hh,mm,ss|Hour Minute Second with comma separator|  
|HmsPeriod|hh.mm.ss|Hour Minute Second with period separator|  
  
 *Supported sourceFormat attribute values for use with db2ToSql timeMask conversion.*  
  
#### SQL Server time to DB2 TIME  
 When reading data from SQL Server and writing to DB2, the MsDrdaService will read string literal time values that match known input SQL Server time formats, and then write string literal time values into the DB2 time target format specified in the app config.  
  
```  
<timeMask>  
                <sqlToDb2 targetFormat="HmsColon"/>  
              </timeMask>  
  
```  
  
 DRDA Service will process strings to match the DB2 time target format HH:MM:SS.  
  
 The **targetFormat** attribute defines the format of the target string that the DRDA Service should produce as an output string literal time value. This **optional** attribute accepts an **enumerated** value. The default is **HmsColon**.  
  
|Format Name|Format Mask|Description|  
|-----------------|-----------------|-----------------|  
|HmsBlank|hh mm ss|Hour Minute Second with blank separator|  
|HmsColon|hh:mm:ss|Hour Minute Second with colon separator|  
|HmsComma|hh,mm,ss|Hour Minute Second with comma separator|  
|HmsPeriod|hh.mm.ss|Hour Minute Second with period separator|  
  
 *Supported targetFormat attribute values for use with sqlToDb2 timeMask conversion.*  
  
### Timestamp  
 The DRDA Service will process string literal timestamp values within DB2 and SQL Server TIMESTAMP, DATETIME2 (6), CHAR (26), and VARCHAR (26) data types, to convert from DB2 timestamp format to SQL Server datetime2 (6) format, and to convert from SQL Server datetime2 (6) format to DB2 timestamp format. The **dateTimeMasks** contains one or more dateTimeMask elements to define timestamp-datetime mappings. The **dateTimeMask** element contains a **db2ToSql** or **sqlToDb2** to indicate the direction, and a **sourceFormat** and a **targetFormat** to specify the mapping. The **db2ToSql** defines the direction from DB2 to SQL Server. The **sqlToDb2** defines the direction from SQL Server to DB2.  
  
#### DB2 TIMESTAMP to SQL Server datetime2  
 When reading data from DB2 and writing to SQL Server, the MsDrdaService will read string literal DB2 timestamp values that match input DB2 timestamp source formats specified in the app config, and then write string literal SQL Server datetime2 (6) values into the default SQL Server datetime2 (6) format.  
  
```  
<dateTimeMask>  
                <db2ToSql sourceFormat="Db2TimestampFormat"/>  
              </dateTimeMask>  
```  
  
 DRDA Service will process strings to match the input DB2 timestamp source format YYYY-MM-DD hh:mm:ss.nnnnnn.  
  
 The **sourceFormat** attribute defines the format of the source string that the DRDA Service should identify as an input string literal timestamp value. This **optional** attribute accepts an **enumerated** value. The default is **Db2TimestampFormat**.  
  
|Format Name|Format Mask|  
|-----------------|-----------------|  
|Db2TimestampFormat|YYYY-MM-DD-hh:mm:ss.tttttt|  
|IsoTimestampFormat|YYYY-MM-DD.hh.mm.ss.tttttt|  
|SqlServerTimestampFormat|YYYY-MM-DD hh:mm:ss.tttttt|  
|AnyTimeStampFormat|YYYY?MM?DD?hh?mm?ss?tttttt|  
  
 *Supported sourceFormat attribute values for use with db2ToSql dateTimeMask conversion.*  
  
#### SQL Server datetime2 to DB2 TIMESTAMP  
 When reading data from SQL Server and writing to DB2, the MsDrdaService will read string literal timestamp values that match known input SQL Server datetime2 (6) formats, and then write string literal date values into the DB2 timestamp target format specified in the app config.  
  
```  
<dateTimeMask>  
                <sqlToDb2 targetFormat="Db2TimestampFormat"/>  
              </dateTimeMask>  
```  
  
 DRDA Service will process strings to match the DB2 timestamp target format YYYY-MM-DD hh:mm: ss.nnnnnn.  
  
 The **targetFormat** attribute defines the format of the target string that the DRDA Service should produce as an output string literal timestamp value. This **optional** attribute accepts an **enumerated** value. The default is **Db2TimestampFormat**.  
  
|Format Name|Format Mask|  
|-----------------|-----------------|  
|Db2TimestampFormat|YYYY-MM-DD-hh:mm:ss.tttttt|  
|IsoTimestampFormat|YYYY-MM-DD.hh.mm.ss.tttttt|  
|SqlServerTimestampFormat|YYYY-MM-DD hh:mm:ss.tttttt|  
  
 *Supported targetFormat attribute values for use with sqlToDb2 dateTimeMask conversion.*
